---
title: "Wireless connection drops when screen locks"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by Fracta on 2011-01-22
I just got a wireless dongle because in my house wired is not possible, but now I am getting problems. The dongle is a tp-link that turned out to be plug&play (unlike windows) and seems to work perfectly, except when the screen locks. 
I have tried to download overnight several times and it seems like a few minutes after the screensaver comes on or after I lock the screen, the connection is dropped. It works completely fine normally. 
So what changes when Ubuntu (its maverick with all updates) locks the screen? Also, when I log back in, I have to unplug the dongle and plug it back in to get it to connect again.

This is really REALLY annoying, enough to make me switch back to windows if I can only download while I'm looking at the screen.

---

### Post by ravengangrel on 2011-01-23
Hi, Fracta.

I am suffering the same issue. However, I think I have found a workaround.

If I set "Put screen to sleep after..." to "Never" in Power saving settings, then my connection doesn't drop.

Remember you must set it in "AC mode" and "battery mode" if your system is a laptop.

Does this work for you? What hardware are you running?

---

### Post by Fracta on 2011-01-25
Nope, doesn't work for me. Which hardware are you talking about? I have a radeon gfx card and a tp-link wireless usb dongle that i use to connect. Not a laptop.
I do have ahci switched on in the bios. Maybe that has something to do with it? I remember thats why sleep couldn't work on my pc. Linux has problems with ahci and sleeping.

---

### Post by grahammechanical on 2011-01-25
If we enable various features of power saving, whether in the OS or BIOS, then when power saving clicks in various parts of the hardware will be switched off including the wireless adapter. With the wireless adapter switched off the connection will drop. It makes sense if we are trying to save the planet.

Regards.

---

### Post by Fracta on 2011-01-25
All of my power saving features are turned off. I haven't checked the bios yet but I doubt anything is set in there. My problem is, I want to be able to download overnight and I can't if it keeps disconnecting me

---

