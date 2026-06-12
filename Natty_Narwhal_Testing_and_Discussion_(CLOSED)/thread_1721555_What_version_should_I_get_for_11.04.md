---
title: "What version should I get for 11.04"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by gfgodoy on 2011-04-04
I got a netbook from Sony. Y series AMD E-350

Should my processor benefit from a 64bit version?


I did download the alternate 64bit version but it gets me a Syslinux error on boot (using UNetbootin AND universal USB to create boot image! on windows 7)

Thanks in advance.

---

### Post by Dutch70 on 2011-04-04
If you're processor is capable of 64-bit, then imho, you'll be much happier with it.

---

### Post by bodhi.zazen on 2011-04-04
I think that is a 32 bit processor, and if so, you will need 32 bit Ubuntu.

---

### Post by gfgodoy on 2011-04-04
Did download that version also. It isnt boooting! 

On my dell it boots just fine, on my vaio it stays on a black screen with a line with linux version. thats all

Weird problem.

---

### Post by bodhi.zazen on 2011-04-04
Too bad. If the iso is good, must be a hardware or video driver that is missing.

Try a google search on your hardware + linux to see if you can find any advice.

---

### Post by cariboo on 2011-04-04
Do you get a menu when you press any key at the first boot screen, the one with the keyboard and man on it, if you do, press F6 and select nomodeset, then press esc, and enter. This will start the system in low graphics mode, but it should get you to a desktop. Once at the desktop, you can check additional drivers to see if there is graphics drivers.

That's a pretty bleeding edge APU (not cpu) so there might not be a lot of support for it yet. If you do get Natty to work on it, I'd really like to see what the output of cat /proc/cpuinfo is.

---

### Post by gfgodoy on 2011-04-04
Couldn't hit F6, did not even get that screen. Only the syslinux version screnn.

But I got it working. I used the flashdrive install function in Windows 7. (autorun file). Tried rebooting from there, no success, but I did click on alternate version... it copied all the needed files to my hdd and on boot I got windows x ubuntu options. Got a live boot, selected install. And it works. Sounds and mic work.

Thanks for your help.

---

