---
title: "lucid lynx - proposed-updates 4nvidia - odd status"
date: 2010-09-12
forum: Multimedia Software
---

### Post by dirty_harry on 2010-09-12
happy sunday everybody :)

Tried to setup my old system: Nvidia 7600 GT with KT333 chipset (Nvidia [says[LINK]]("http://us.download.nvidia.com/XFree86/Linux-x86/256.53/README/configuringagp.html") you need agpgart).
I ended up with making proposed-updates to linux-2.6.32-25 and NVIDIA-Linux-x86-256.53 from the website, not ppa. [Long Version[LINK]]("http://ubuntuforums.org/showthread.php?t=1571559") 

Now it is back to normal. xorg.0.log shows no errors anymore and opengl-games, flash in full screen etc. works. 
But now agpgart status is disabled and the device is listed as PCI whatsoever... 
I attached a current nvidia-bug-report.

I would like to give this machine to a "normal" user; none techie! But with *proposed+odd status* maybe not so good.

Should I go for a fresh new installation or is there anything I can do? 
Is there a bug or something which is related to agpgart/via_agp/nvidia in combination with my chipset?
Any ideas?

thx and enjoy the sun 8)
[FONT=Century Gothic][SIZE=1]/me will now eat something and then go to the city garden relaxing
[/SIZE][/FONT]

---

### Post by dirty_harry on 2010-09-14
Odyssey is it called?

What I tried and failed:
# _NEW_ installation Xubuntu 10.04 NVIDIA-Linux-x86-256.53
# installation Xubuntu 9.10 with NVIDIA-Linux-x86-256.53 
#  installation debian lenny 5.0.5 withNVIDIA-Linux-x86-256.53
# "WINDOWS 2003 evaluation" with 258.96_desktop_winxp_32bit_international_whql.exe
every time the same error: "nvidia error switch back...."

What I tried and now functions since yesterday:
# replace nvidia geforce 7600 GT with ati radeon 9600
the free radeon driver is really nice 8)

---

