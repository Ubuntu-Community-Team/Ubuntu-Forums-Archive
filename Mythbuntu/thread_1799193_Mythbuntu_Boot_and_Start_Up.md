---
title: "Mythbuntu Boot and Start Up"
date: 2011-07-07
forum: Mythbuntu
---

### Post by childe joseph on 2011-07-07
I just installed mythbuntu 'Natty', and am eager to use it, but I got more then a couple problems right off the bat. I'll start with the boot and start up. Problem #1 Turning on computer offers black screen. After waiting a few minutes pressing ctrl-alt-delete gets me a reboot, that then yields a black screen with the following

BusyBox v.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)

typing 'exit' at '(initramfs)' prompt starts my Front End. I can 'Esc' the myth front end, and bring up 'X' and the back end. Still usable, but obviously something is amiss. Any help would be appreciated. Thanks!

---

### Post by ian dobson on 2011-07-07
Hi,

Can you provide abit more information, what hardware are you using? What Mythbuntu have you installed (32/64bit)? What graphic card driver are you using.

Your problem sounds alot like a graphic card driver problem.

Regards
Ian Dobson

---

### Post by childe joseph on 2011-07-07
I've attached a short form of my Hardware report. I hope this helps. This was taken from a system running WinXp SP3. But the Hardware is the same. I read your Mythbuntu project on your website. Hopefully this should be a bit easier. I want to use the same machine for the Front and Back ends. Maybe watch it on a T.V. screen. But I'll settle for it just working on my monitor for now. Note: I use Linux Mint on my main machine. But I've never really successfully installed drivers, though I have attempted it more then once, maybe even more then twice. I've unpacked them, compiled them, but never been actually installed them. 32Bit mythbuntu 11.04

---

### Post by ian dobson on 2011-07-07
Hi,

My mythtv project is abit over the top (7 x 2Tb drives, 16Gb Ram, Quad Core SandyBridge and a complex network configuration) and I enjoy playing.

OK, the box is an old compaq with a ATI AGP graphic card. When you get the box up and running in graphic mode, you can try uninstalling the open source driver and install the ATI. You can install them through the myth control pannel.

I must admit I've never had much luck with ATI especially MythTV/Video playback, all my Linux boxes use NVidia cards.

Regards
Ian Dobson

---

### Post by markpennock on 2011-07-08
I am having the same boot problem. How do I get it running in graphic, or any mode, to fix this?

---

### Post by markpennock on 2011-07-08
Another thing is that running from the live cd is fine. Only after installation I am unable to boot into mythbuntu. I was able to successfully install and run ubuntu LTS 10.04.

---

### Post by ian dobson on 2011-07-09
Hi,

Go through your initramfs "login" process, then maybe try uninstalling the ATI drivers and reboot. It sounds as if the graphic card isn't being setup correctly.

If the box then boots normally in "low graphics mode" try installing the ATI closed source drivers.

Regards
Ian Dobson

---

