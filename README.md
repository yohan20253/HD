-- ServerScript: ChatCommandsScript
local Players = game:GetService("Players")

-- IDs ou nomes permitidos para usar comandos
local allowedUsers = {
    ["alma_perdidaS"] = true,
    -- ["roblox"] = true,
}

Players.PlayerAdded:Connect(function(player)
    player.Chatted:Connect(function(msg)
        if not allowedUsers[player.Name] then return end

        -- Comando :speed 100
        if msg:lower():sub(1,7) == ":speed " then
            local speed = tonumber(msg:sub(8))
            if speed and player.Character and player.Character:FindFirstChild("Humanoid") then
                player.Character.Humanoid.WalkSpeed = speed
            end
        end

        -- Comando :jump 150
        if msg:lower():sub(1,6) == ":jump " then
            local jump = tonumber(msg:sub(7))
            if jump and player.Character and player.Character:FindFirstChild("Humanoid") then
                player.Character.Humanoid.JumpPower = jump
            end
        end

        -- Comando :fly
        if msg:lower() == ":fly" then
            -- Exemplo simples de voo (requer mais lógica para ser completo)
            local humanoidRoot = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
            if humanoidRoot then
                humanoidRoot.Velocity = Vector3.new(0, 100, 0)
            end
        end
    end)
end)
