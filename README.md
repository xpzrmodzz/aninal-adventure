getgenv().SecureMode = true

local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "FRITE HUB animal adventure",
   LoadingTitle = "Best Gui",
   LoadingSubtitle = "FRITE on top",
   ConfigurationSaving = {
      Enabled = false,
      FolderName = nil, -- Create a custom folder for your hub/game
      FileName = "Big Hub"
   },
   Discord = {
      Enabled = false,
      Invite = "noinvitelink", -- The Discord invite code, do not include discord.gg/. E.g. discord.gg/ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },
   KeySystem = false, -- Set this to true to use our key system
   KeySettings = {
      Title = "Untitled",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided",
      FileName = "Key", -- It is recommended to use something unique as other scripts using Rayfield may overwrite your key file
      SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})

Rayfield:Notify(
    {
        Title = "You executed the script",
        Content = "FRITE/C.N on top",
        Duration = 5,
        Image = nil,
        Actions = {
            Ignore = {
                Name = "Okay!",
                Callback = function()
                    print("The user tapped Okay!")
                end
            }
        }
    }
)

local MainTab = Window:CreateTab("Farm", 4483362458)

local Section = MainTab:CreateSection("Farm")

local Tab = Window:CreateTab("other farm", 4483362458)

local Section = Tab:CreateSection("other farm")

local scriptTab = Window:CreateTab("script", 4483362458)

local Section = scriptTab:CreateSection("script")


local Button =
   scriptTab:CreateButton(
        {
            Name = "Anti afk 😴",
            Callback = function()
                loadstring(game:HttpGet("https://raw.githubusercontent.com/xpzrmodzz/anti-afk/main/Anti%20afk"))()
            end
        }
    )


local Button =
   scriptTab:CreateButton(
        {
            Name = "infinite yeild",
            Callback = function()
                loadstring(game:HttpGet('https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source'))()
            end
        }
    )

    local ToggleAutoAttackMushrooms = MainTab:CreateToggle({
        Name = "Auto Attack Mushrooms 🍄 (lvl1)",  -- Nom de la bascule
        CurrentValue = false,               -- Valeur initiale
        Flag = "AutoAttackMushroomsToggle",  -- Identifiant de la bascule
        Callback = function(Value)
            if Value then
                _G.AutoAttackMushroomsActive = true
                
                while _G.AutoAttackMushroomsActive do
                    wait(0.1)
    
                    -- Définit l'argument pour l'attaque
                    local args = {
                        [1] = {
                            ["isLocalNPC"] = true,  -- Indique que c'est un NPC local
                            ["npcName"] = "Lvl1"    -- Nom du NPC (champignon de niveau 1)
                        }
                    }
    
                    -- Appelle l'événement d'attaque
                    game:GetService("ReplicatedStorage").Remotes.Attack:FireServer(unpack(args))
                end
            else
                _G.AutoAttackMushroomsActive = false
            end
        end,
    })
    
    local ToggleCoins = MainTab:CreateToggle({
        Name = "Coins Collection 💰 (lvl1)",  -- Nom de la bascule
        CurrentValue = false,           -- Valeur initiale
        Flag = "CoinsToggle",           -- Identifiant de la bascule
        Callback = function(Value)
            if Value then
                _G.CoinsActive = true
                
                while _G.CoinsActive do
                    wait(0.1)
    
                    -- Définit l'argument pour signaler que le NPC est mort
                    local args = {
                        [1] = {
                            ["action"] = "npc_died",  -- Indique que le NPC est mort
                            ["npcName"] = "Lvl1"      -- Nom du NPC (champignon de niveau 1)
                        }
                    }
    
                    -- Appelle l'événement pour collecter les pièces
                    game:GetService("ReplicatedStorage").Events.coinsEvent:FireServer(unpack(args))
                end
            else
                _G.CoinsActive = false
            end
        end,
    })

    local ToggleInfHealth = MainTab:CreateToggle({
        Name = "Infinite Health ♾️",  -- Nom de la bascule
        CurrentValue = false,           -- Valeur initiale
        Flag = "InfHealthToggle",       -- Identifiant de la bascule
        Callback = function(Value)
            if Value then
                _G.InfHealthActive = true
                
                while _G.InfHealthActive do
                    wait(0.1)
    
                    -- Définit l'argument pour infliger des dégâts infinis
                    local args = {
                        [1] = -math.huge  -- Utilise une valeur pour infliger des dégâts infinis
                    }
    
                    -- Appelle l'événement pour infliger des dégâts
                    game:GetService("ReplicatedStorage").Events.NPCDamageEvent:FireServer(unpack(args))
                end
            else
                _G.InfHealthActive = false
            end
        end,
    })
    
    

Rayfield:LoadConfiguration()
