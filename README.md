local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local Window = Library.CreateLib("Testing GUI",Midnight)
local Tab = Window:NewTab("Teleporting")
local Section = Tab:NewSection("Teleports")

Section:NewLabel("TweenTest")

Section:NewButton("ButtonText", "ButtonInfo", function()
	 local teleport_table = {
	location1 = Vector3.new(x,y,z)
}

local tween_s = game:GetService('TweenService')
local tweeninfo = TweenInfo.new(12,Enum.EasingStyle.Linear)

local lp = game.Players.LocalPlayer

function bypass_teleport(v)
	if lp.Character and
	lp.Character:FindFirstChild('HumanoidRootPart') then
		local cf = CFrame.new(v)
		local a = tween_s:Create(lp.Character.HumanoidRootPart,tweeninfo,{CFrame=cf})
		a:Play()
	end
end

bypass_teleport(teleport_table.location1)
end)

local Tab = Window:NewTab("Player")
local Section = Tab:NewSection("Player")

Section:NewLabel("Modify")

Section:NewSlider("Walkspeed", "change your walkspeed", 380, 0, function(s) -- 380 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = s
end)

Section:NewSlider("JumpPower", "change jumppower", 800, 0, function(s) -- 800 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.JumpHeight = s
end)

Section:NewButton("Change Health (Not Bypassed)", "THIS MIGHT GET YOU BANNED", function()
     game.Players.LocalPlayer.Character.Humanoid.MaxHealth = 999999999999999
end)

Section:NewSlider("Health", "change health", 999, 0, function(s) -- 999 (MaxValue) | 0 (MinValue)
    game.Players.LocalPlayer.Character.Humanoid.MaxHealth = s
end)

local Tab = Window:NewTab("AutoFarm")
local Section = Tab:NewSection("Games")

Section:NewLabel("Rebirth Champions")

Section:NewButton("Turn on AutoC", "ButtonInfo", function()
print("turned on AutoC")
wait(1)
getgenv().autoclick = true;

while getgenv().autoclick == true do
	game:GetService("ReplicatedStorage").Events.Click3:FireServer()
	wait()
end
end)

Section:NewButton("Turn off AutoC", "ButtonInfo", function()
print("turned off AutoC")
wait(1)
getgenv().autoclick = false;

while getgenv().autoclick == true do
	game:GetService("ReplicatedStorage").Events.Click3:FireServer()
	wait()
end
end)

Section:NewButton("Turn on AutoR", "", function()
print("turned on AutoR")
wait(1)
getgenv().autorebirth = true;

while getgenv().autorebirth == true do
	local A_1 = 1
game:GetService("ReplicatedStorage").Events.Rebirth:FireServer(A_1)
	wait()
end
end)

Section:NewButton("Turn off AutoR", "", function()
print("turned off AutoR")
wait(1)
getgenv().autorebirth = false;

while getgenv().autorebirth == true do
	local A_1 = 1
game:GetService("ReplicatedStorage").Events.Rebirth:FireServer(A_1)
	wait()
end
end)
