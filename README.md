 local NotificationBindable = Instance.new("BindableFunction")
                NotificationBindable.OnInvoke = callback
                --
                game.StarterGui:SetCore("SendNotification",  {
                 Title = "Pietro é gay";
                 Text = "confirmado.";
                 Icon = "";
                 Duration = 5;
                 Callback = NotificationBindable;
                })
            


-- you can only use the words that are listed under here

local Bypasses = {
    ["1!"] = "UM !",
    ["2!"] = "DOIS !",
    ["3!"] = "TRÊS !",
    ["4!"] = "QUATRO !",
    ["5!"] = "CINCO !",
    ["6!"] = "SEIS !",
    ["7!"] = "SETE !",
    ["8!"] = "OITO !",
    ["9!"] = "NOVE !",
    ["10!"] = "DEZ !",
    ["11!"] = "ONZE !",
    ["12!"] = "DOZE !",
    ["13!"] = "TREZE !",
    ["14!"] = "QUATORZE !",
    ["15!"] = "QUINZE !",
    ["16!"] = "DEZESSEIS !",
    ["17!"] = "DEZESSETE !",
    ["18!"] = "DEZOITO !",
    ["19!"] = "DEZENOVE !",
    ["20!"] = "VINTE !",
    ["21!"] = "VINTE E UM !",
    ["22!"] = "VINTE E DOIS !",
    ["23!"] = "VINTE E TRÊS !",
    ["24!"] = "VINTE E QUATRO !",
    ["25!"] = "VINTE E CINCO !",
    ["26!"] = "VINTE E SEIS !",
    ["27!"] = "VINTE E SETE !",
    ["28!"] = "VINTE E OITO !",
    ["29!"] = "VINTE E NOVE !",
    ["30!"] = "TRINTA !",
    ["31!"] = "TRINTA E UM !",
    ["32!"] = "TRINTA E DOIS !",
    ["33!"] = "TRINTA E TRÊS !",
    ["34!"] = "TRINTA E QUATRO !",
    ["35!"] = "TRINTA E CINCO !",
    ["36!"] = "TRINTA E SEIS !",
    ["37!"] = "TRINTA E SETE !",
    ["38!"] = "TRINTA E OITO !",
    ["39!"] = "TRINTA E NOVE !",
    ["40!"] = "QUARENTA !",
	["41!"] = "QUARENTA E UM !",
	["42!"] = "QUARENTA E DOIS !",
	["43!"] = "QUARENTA E TRÊS !",
	["44!"] = "QUARENTA E QUATRO !",
	["45!"] = "QUARENTA E CINCO !",
	["46!"] = "QUARENTA E SEIS !",
	["47!"] = "QUARENTA E SETE !",
	["48!"] = "QUARENTA E OITO !",
	["49!"] = "QUARENTA E NOVE !",
	["50!"] = "CINQUENTA !",
	["51!"] = "CINQUENTA E UM !",
	["52!"] = "CINQUENTA E DOIS !",
	["53!"] = "CINQUENTA E TRÊS !",
	["54!"] = "CINQUENTA E QUATRO !",
	["55!"] = "CINQUENTA E CINCO !",
	["56!"] = "CINQUENTA E SEIS !",
	["57!"] = "CINQUENTA E SETE !",
	["58!"] = "CINQUENTA E OITO !",
	["59!"] = "CINQUENTA E NOVE !",
	["60!"] = "SESSENTA !",
	["61!"] = "SESSENTA E UM !",
	["62!"] = "SESSENTA E DOIS !",
	["63!"] = "SESSENTA E TRÊS !",
	["64!"] = "SESSENTA E QUATRO !",
	["65!"] = "SESSENTA E CINCO !",
	["66!"] = "SESSENTA E SEIS !",
	["67!"] = "SESSENTA E SETE !",
	["68!"] = "SESSENTA E OITO !",
	["69!"] = "SESSENTA E NOVE !",
	["70!"] = "SETENTA !",
	["71!"] = "SETENTA E UM !",
	["72!"] = "SETENTA E DOIS !",
	["73!"] = "SETENTA E TRÊS !",
	["74!"] = "SETENTA E QUATRO !",
	["75!"] = "SETENTA E CINCO !",
	["76!"] = "SETENTA E SEIS !",
	["77!"] = "SETENTA E SETE !",
	["78!"] = "SETENTA E OITO !",
	["79!"] = "SETENTA E NOVE !",
	["80!"] = "OITENTA !",
	["81!"] = "OITENTA E UM !",
	["82!"] = "OITENTA E DOIS !",
	["83!"] = "OITENTA E TRÊS !",
	["84!"] = "OITENTA E QUATRO !",
	["85!"] = "OITENTA E CINCO !",
	["86!"] = "OITENTA E SEIS !",
	["87!"] = "OITENTA E SETE !",
	["88!"] = "OITENTA E OITO !",
	["89!"] = "OITENTA E NOVE !",
	["90!"] = "NOVENTA !",
	["91!"] = "NOVENTA E UM !",
	["92!"] = "NOVENTA E DOIS !",
	["93!"] = "NOVENTA E TRÊS !",
	["94!"] = "NOVENTA E QUATRO !",
	["95!"] = "NOVENTA E CINCO !",
	["96!"] = "NOVENTA E SEIS !",
	["97!"] = "NOVENTA E SETE !",
	["98!"] = "NOVENTA E OITO !",
	["99!"] = "NOVENTA E NOVE !",
	["100!"] = "CEM !",
	["101!"] = "CENTO E UM !",
	["102!"] = "CENTO E DOIS !",
	["103!"] = "CENTO E TRÊS !",
    [""] = "",
    [""] = ""


}

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Remote = ReplicatedStorage:FindFirstChild("SayMessageRequest", true)

local ChatBypass; ChatBypass = hookmetamethod(Remote, "__namecall", function(self, ...)
    local Method = getnamecallmethod()
    local Arguments = {...}
    
    if self == Remote and Method == "FireServer" then
        local Message = Arguments[1]
        local Split = Message:split(" ")
        local FinalMessage = ""

        for _, x in next, Split do
            for _, Bypass in next, Bypasses do
                if x:lower() == _ then
                    if x:upper() ~= x then
                        Message = Message:gsub(x, Bypass)
                        FinalMessage = Message .. ""
                    else
                        Message = Message:gsub(x, Bypass):upper()
                        FinalMessage = Message:gsub(x, Bypass):upper() .. ""
                    end
                end
            end
        end
        
        if FinalMessage ~= "" then
            Arguments[1] = FinalMessage
        end
        
        return ChatBypass(self, unpack(Arguments))
    end
    
    return ChatBypass(self, ...)
end)
