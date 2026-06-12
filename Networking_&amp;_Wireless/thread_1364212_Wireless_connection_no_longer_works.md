---
title: "Wireless connection no longer works"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by pacman5 on 2009-12-25
Installed Ubuntu 8.04 yesterday as dual-boot addition to Windows XP Pro on my laptop. Wireless connection functioned normally and I was able to surf and pick up email with Evolution.

Today I installed Thunderbird and the wireless connection now no longer works. The wired connection works and the original Windows XP system on the same laptop can still communicate via wireless so the wireless card on the laptop and the wireless router are intact.

I opened up the Ubuntu network manager and checked that the router address and the password were correct. HOWEVER, I discovered that when I re-opened the network manager the router password had disappeared and the password field was empty. I re-entered the password, clicked OK etc., no wireless connection, and when I re-opened the network manager the password had disappeared again. And so on ad infinitum.

So it seems that for some reason the network manager is not saving (or is deleting) the router password.

Can anyone tell me where the problem might lie (yes, I've been to the troubleshooting wiki but cannot find a reference to this type of problem) ?

Paddy

---

### Post by pacman5 on 2009-12-26
P.S. To this - I de-installed Thunderbird but the problem persisted.

---

### Post by trintin7 on 2009-12-26
Try execute these in Terminal
 ```
nm-applet --sm-disable
```

---

### Post by pacman5 on 2009-12-26
Thanks for this.

I typed that into Terminal exactly as it was written, hit Enter, and all I got was a blinking cursor on the next line without the normal cursor prompt. There was still no internet connection.

Any other ideas ?

Paddy

---

### Post by trintin7 on 2009-12-26
I'm out of ideas but I'm finding the right command.

---

### Post by pacman5 on 2009-12-26
I'm afraid I'm not very knowledgeable about Linux/Ubuntu, just kind of working from the recipe book without understanding what the commands are actually doing.

Is there some way to completely remove the network manager from the system and re-install it or is it so deeply lodged in the system that its removal would bring down the whole house of cards ?

Paddy

---

### Post by trintin7 on 2009-12-26
> **pacman5 said:**
> I'm afraid I'm not very knowledgeable about Linux/Ubuntu, just kind of working from the recipe book without understanding what the commands are actually doing.

Is there some way to completely remove the network manager from the system and re-install it or is it so deeply lodged in the system that its removal would bring down the whole house of cards ?

Paddy

Well its impossible to bring down the network (PHYSICALLY) by just using Command
And for the Deletion of the network manger I think it is impossible because it is the system components. So I think won't be so easy  to bring down the network that much.

---

### Post by pacman5 on 2009-12-26
I've solved the problem. The solution was very simple but I'll post it even though I can't understand its mechanism, in case others can profit from it.

I took the laptop from its usual desk around 15 feet and one wall away from the wireless router and plonked it right next to the router. To my amazement a window I had never seen before popped up asking me for the router password. I entered the password, and bingo! everything started working again. I returned the laptop to its usual position away from the router and things continued working (as they had done until two days ago).

I can only conclude that momentarily "bombarding" the Ubuntu laptop with a strong wireless router signal woke up some peacefully slumbering bit of code (or a 6-year old and maybe gradually tiring wireless network adapter in the laptop) and made it smell the coffee.

This solution had not occurred to me because the laptop had been functioning wirelessly on its usual desk for years, previously with XP and now with Ubuntu, and there had never been the slightest wireless problem so I didn't think its position might be an issue (whacks side of head several times....)

Anyway, thanks again for your help.

Paddy

---

