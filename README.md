-- Servicios necesarios
local Players = game:GetService("Players")
local TeleportService = game:GetService("TeleportService")
local HttpService = game:GetService("HttpService")
local TweenService = game:GetService("TweenService")

local LocalPlayer = Players.LocalPlayer
local PlaceId = game.PlaceId

-- Creación de la Interfaz GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "PrivateServerFinder"
ScreenGui.ResetOnSpawn = false

if syn and syn.protect_gui then
    syn.protect_gui(ScreenGui)
    ScreenGui.Parent = game.CoreGui
elseif gethui then
    ScreenGui.Parent = gethui()
else
    ScreenGui.Parent = game.CoreGui
end

-- Ventana Principal (Estilo Minimalista Oscuro)
local MainFrame = Instance.new("Frame")
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(15, 12, 25)
MainFrame.BorderSizePixel = 0
MainFrame.Position = UDim2.new(0.5, -130, 0.5, -120)
MainFrame.Size = UDim2.new(0, 260, 0, 240)
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.ClipsDescendants = true
Instance.new("UICorner", MainFrame).CornerRadius = UDim.new(0, 12)

local UIStroke = Instance.new("UIStroke", MainFrame)
UIStroke.Color = Color3.fromRGB(60, 50, 90)
UIStroke.Thickness = 1.5

-- Cabecera
local Title = Instance.new("TextLabel", MainFrame)
Title.Position = UDim2.new(0, 15, 0, 12)
Title.Size = UDim2.new(0, 180, 0, 18)
Title.BackgroundTransparency = 1
Title.Font = Enum.Font.FredokaOne
Title.Text = "PX"
Title.TextColor3 = Color3.fromRGB(0, 230, 255)
Title.TextSize = 14
Title.TextXAlignment = Enum.TextXAlignment.Left

local Subtitle = Instance.new("TextLabel", MainFrame)
Subtitle.Position = UDim2.new(0, 15, 0, 30)
Subtitle.Size = UDim2.new(0, 220, 0, 14)
Subtitle.BackgroundTransparency = 1
Subtitle.Font = Enum.Font.GothamMedium
Subtitle.Text = "ピエロの卵を盗む"
Subtitle.TextColor3 = Color3.fromRGB(160, 160, 180)
Subtitle.TextSize = 10
Subtitle.TextXAlignment = Enum.TextXAlignment.Left

-- Botón Cerrar
local CloseBtn = Instance.new("TextButton", MainFrame)
CloseBtn.BackgroundColor3 = Color3.fromRGB(35, 30, 50)
CloseBtn.Position = UDim2.new(1, -32, 0, 12)
CloseBtn.Size = UDim2.new(0, 20, 0, 20)
CloseBtn.Font = Enum.Font.GothamBold
CloseBtn.Text = "X"
CloseBtn.TextColor3 = Color3.fromRGB(200, 200, 220)
CloseBtn.TextSize = 11
Instance.new("UICorner", CloseBtn).CornerRadius = UDim.new(0, 6)
CloseBtn.MouseButton1Click:Connect(function() ScreenGui:Destroy() end)

-- Tarjeta de Estado
local StatusCard = Instance.new("Frame", MainFrame)
StatusCard.Position = UDim2.new(0, 15, 0, 50)
StatusCard.Size = UDim2.new(1, -30, 0, 52)
StatusCard.BackgroundColor3 = Color3.fromRGB(24, 20, 40)
StatusCard.BorderSizePixel = 0
Instance.new("UICorner", StatusCard).CornerRadius = UDim.new(0, 8)

local NowLabel = Instance.new("TextLabel", StatusCard)
NowLabel.Position = UDim2.new(0, 10, 0, 6)
NowLabel.Size = UDim2.new(1, -20, 0, 18)
NowLabel.BackgroundTransparency = 1
NowLabel.Font = Enum.Font.GothamBold
NowLabel.TextXAlignment = Enum.TextXAlignment.Left
NowLabel.TextColor3 = Color3.fromRGB(0, 230, 255)
NowLabel.TextSize = 12

local StatusLabel = Instance.new("TextLabel", StatusCard)
StatusLabel.Position = UDim2.new(0, 10, 0, 24)
StatusLabel.Size = UDim2.new(1, -20, 0, 22)
StatusLabel.BackgroundTransparency = 1
StatusLabel.TextXAlignment = Enum.TextXAlignment.Left
StatusLabel.TextColor3 = Color3.fromRGB(160, 160, 180)
StatusLabel.TextSize = 10
StatusLabel.TextWrapped = true

-- Campo de Entrada (Máximo de jugadores)
local MaxBox = Instance.new("TextBox", MainFrame)
MaxBox.Position = UDim2.new(0, 15, 0, 110)
MaxBox.Size = UDim2.new(1, -30, 0, 32)
MaxBox.BackgroundColor3 = Color3.fromRGB(24, 20, 40)
MaxBox.BorderSizePixel = 0
MaxBox.Font = Enum.Font.GothamBold
MaxBox.Text = "1"
MaxBox.PlaceholderText = "Max Players Allowed"
MaxBox.TextColor3 = Color3.fromRGB(255, 255, 255)
MaxBox.TextSize = 13
MaxBox.ClearTextOnFocus = false
Instance.new("UICorner", MaxBox).CornerRadius = UDim.new(0, 8)

-- Botón de Acción Única (Hop Server Now)
local JoinBtn = Instance.new("TextButton", MainFrame)
JoinBtn.Position = UDim2.new(0, 15, 0, 150)
JoinBtn.Size = UDim2.new(1, -30, 0, 34)
JoinBtn.BackgroundColor3 = Color3.fromRGB(0, 140, 255)
JoinBtn.BorderSizePixel = 0
JoinBtn.Font = Enum.Font.GothamBold
JoinBtn.Text = "HOP SERVER NOW"
JoinBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
JoinBtn.TextSize = 11
Instance.new("UICorner", JoinBtn).CornerRadius = UDim.new(0, 8)

-- Botón de Auto Hop
local AutoBtn = Instance.new("TextButton", MainFrame)
AutoBtn.Positio
