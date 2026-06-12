---
title: "ATI HD4890 driver (v10.7) on ubuntu 10.04 - driver install problem"
date: 2010-08-14
forum: Multimedia Software
---

### Post by poznir on 2010-08-14
hi,
i installed Ubuntu 10.04 (x86)
the desktop is loading but with no effects enabled and no 3d support.
i tried to install the ati drivers (version 10.07)
with the help of every guide i could find online but nothing works.
every time after i finish installing i reboot and i get black screen before getting in to the login screen.

my graphics card is ati hd4890

what can i do in order to solve this problem?

thanks!

---

### Post by poznir on 2010-08-15
please, anyone can help me?
i really dont know what to do about it

---

### Post by Zeggi on 2010-08-18
I have the same problem.
New installation of Ubuntu 10.04
at first start i only see bios and after that its black with "|" flashing.
 
My setup,
Crosshair IV Formula
ATI HD4890
Intel X25-M

I tried a install with my old 9800GT and it worked fine, but i want my ATI card to work.
Im not even sure if its possible to go around by using both cards maybe?
but again i should be able to run with the ATI card only.
 
Im new to Ubuntu and i have searched for tips/guides etc but they all seem to have the grub menu as option while its black for me with no options at all.

---

### Post by Zeggi on 2010-08-19
I got it working.
I have done a clean install of windows 7 after that ubuntu 10.04 x64 which was on CD.
at first boot i couldn't get the grub menu to show and windows booted straigt off.
So what i did was i used the livecd in grub i turned off acpi and then i booted with first choice in grub. I had to copy the grub menu from the livecd i guess it ended up on another HDD.
 
Anyway at reboot i got grub showing and i started ubuntu for the first time, i did a update of the programs and after that i downloaded the ati drivers from amd.com and followed the instructions. worked like a charm:)
 
I couldn't get the first reboot going when i installed from USB but with CD it worked.
Also i think the blackscreen it self is because grub must have ended somewhere else therefor i used the Livecd. If you need details let me know.

---

