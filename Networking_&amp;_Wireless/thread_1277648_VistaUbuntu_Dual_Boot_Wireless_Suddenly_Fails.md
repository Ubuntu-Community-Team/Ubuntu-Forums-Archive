---
title: "Vista/Ubuntu Dual Boot Wireless Suddenly Fails"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by ScarletWyvern on 2009-09-28
Yesterday, I set up a dual-boot on my system, having had Vista installed first. I now have Ubuntu 9.04 installed as well.

Yesterday, my wireless connection worked fine in both Ubuntu and Vista. I had no problems at all.

I came home today and fired up Ubuntu. The connection process lagged for a few minutes, but wouldn't connect, so I restarted. This time, it just failed to connect at all. I tried enabling the madwifi driver, since I have an Atheros card, but that did nothing.

Upon restarting and booting into Vista, Vista doesn't say that there's anything wrong with my card, just that it can't find any networks to connect to

The other two computers in my house can connect fine, but only the laptop in question seems to be having problems.

I have no idea where to even start to try and fix this. Please help.

---

### Post by ScarletWyvern on 2009-09-28
So more information, if it helps:

iwconfig detects my wlan0, but says that it's not associated with any AP.

I was Googling earlier, and I forget what the command was, but it gave something like "*-network DISABLED"

---

### Post by ScarletWyvern on 2009-09-28
Bump?

---

### Post by ScarletWyvern on 2009-09-28
After following a suggestion I found in which I boot with my wifi switch set to off, and then turn it on after its booted, I've been able to get wireless working again in Vista, but now Ubuntu doesn't even detect my card. =/

I guess I should also point out that my wifi "switch" is a button. When its off, the light is orange and when it's on, the light is blue. The light is always orange when I'm in Ubuntu, but it was like that yesterday when wifi was working flawlessly in Ubuntu, so I'm just confused...

lspci tells me that my card is there, but iwconfig only brings up eth0...

Well, at least its progress, right?

---

