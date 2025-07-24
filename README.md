
game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        wait(1)

        local clone = character:Clone()
        clone.Name = player.Name .. "_Clone"

        if clone:FindFirstChild("HumanoidRootPart") then
            clone:MoveTo(character.HumanoidRootPart.Position + Vector3.new(5, 0, 0))
        end

        clone.Parent = workspace

        for _, obj in ipairs(clone:GetDescendants()) do
            if obj:IsA("Script") or obj:IsA("LocalScript") then
                obj:Destroy()
            end
        end
    end)
end)
