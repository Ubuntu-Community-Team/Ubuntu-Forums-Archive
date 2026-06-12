---
title: "Lock-Ups with nvidia driver &amp; Breezy"
date: 2005-11-16
forum: Multimedia &amp; Video
---

### Post by tardis_junkie on 2005-11-16
Hi,

I have been away from ubuntu for a while and have installed breezy to have another look.

After installing nvidia-glx and running nvidia config command, I log out restart X and log back in all is fine.

However when I log out or restart the screen display becomes garbled and the machine is hard-locked.

Cannot even SSH in to restart.

Breezy AMD64 running i386 version - Nvidia FX5700 Ultra.

Look forward to your assistance.

Paul

---

### Post by Teroedni on 2005-11-17
hmm 
Could you give us the log file whe x try to start up and Freeze?

Also have you tried AMD64 Version?

---

### Post by action09 on 2005-11-17
Hi !

I have "exactly" the same problem and  i'm happy not to be alone.
My English isn't very good so i had difficulties to tell that's the Workstation is locked and screen 'garbled'.

For my case: after installing nvidia driver (from ubuntu: nvidia-glx), i'm using my Ubuntu/Linux and some applications close by themselves ( aMule, Firefox, Galeonpan..etc) , the most annoying thing are the browsers :(

I got for some reasons too a freeze with the garbled screen while watching a movie with mplayer or else.
Nothing is possible to unlock the machine (ctrl +F2 or ssh or anything :( i HAVE to reboot it by poweroff the plug :()

Here are my log files:
 /var/log/Xorg.0.log after the reboot and my /etc/X11/xorg.conf

placed on my site..
I dunno if it can help , tell me what's needed to look first into please :)

lsmod output is in the .tar.gz too
---> here: [http://action09.suidzer0.org/hard.tgz](http://action09.suidzer0.org/hard.tgz)

I'm using a kernel:
uname -a
Linux WOPR 2.6.12-9-686-smp #1 SMP Mon Oct 10 13:36:57 BST 2005 i686 GNU/Linux

Thanks in advance.

Regards

---

### Post by action09 on 2005-11-17
As i read some posts on it, i'd like to say that i tried to disable autohinting
by doing 
like expained here: sudo dpkg-reconfigure fontconfig and not choosed autohinting...

I found this in the forum:
[http://ubuntuforums.org/showpost.php?p=132408&postcount=19](http://ubuntuforums.org/showpost.php?p=132408&postcount=19)

It seems to be related to autohinting in fonts....
If you turn autohinting off, it should no longer crash, though you loose your
pretty fonts :-(

and from this page:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=7183](http://bugzilla.ubuntu.com/show_bug.cgi?id=7183)



One more thing i found this in the logs too:
-----------------------------------------
root@WOPR:/home/action09# grep gdm /var/log/daemon.log
Nov 17 21:55:28 localhost gdm[8457]: gdm_slave_xioerror_handler : erreur X fatale - Redémarrage de :0
root@WOPR:/home/action09# 




One last thing:
--------------
When i had a bug with galeon, the bugzilla window opened and i choose to submit a bug (maybe a gnome problem i thought ?) but the developpers told me it was a font config and nothing to do with gnome, and closed the case.

So i'm not experienced in low-level debugging, especially with proprietary drivers, (i tried the free one but wathching a move was horrible because of some horizontal lines)


Thanks in advance :)  I will tell you if the problem occur again :)

---

### Post by Teroedni on 2005-11-18
hmm could you state your hardware?
cpu ram graphics card sound card

---

### Post by action09 on 2005-11-18
CPU:
*****

sudo cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 5
cpu MHz         : 2806.931
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5554.17

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 5
cpu MHz         : 2806.931
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5603.32




RAM
****
 sudo cat /proc/meminfo
MemTotal:      1036088 kB
MemFree:         71112 kB
Buffers:        252112 kB
Cached:         338128 kB
SwapCached:          0 kB
Active:         635840 kB
Inactive:       217672 kB
HighTotal:      131008 kB
HighFree:          120 kB
LowTotal:       905080 kB
LowFree:         70992 kB
SwapTotal:      530136 kB
SwapFree:       530136 kB
Dirty:             848 kB
Writeback:           4 kB
Mapped:         325044 kB
Slab:            92696 kB
CommitLimit:   1048180 kB
Committed_AS:   622116 kB
PageTables:       1808 kB
VmallocTotal:   114680 kB
VmallocUsed:     27248 kB
VmallocChunk:    87280 kB


it's CORSAIR 1GB



Graphics Card:
**************

lspci -v | grep nVidia
0000:01:00.0 VGA compatible controller: nVidia Corporation NV 36 [GeForce 5700 Ultra] (rev a1) (prog-if 00 [VGA])



Sound Card:
************
 lspci -v | grep audio
0000:02:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)

Hope this help !  :)

TIA.

Action

---

### Post by oofnik on 2005-12-12
Same problem here. Pentium IV 2.6 HT, 1GB RAM, and GeForge FX5700 Ultra. I tried compiling the nvidia drivers and installing through nvidia-glx but both would cause X to crash hard on exit. I've had to go back to using the nv driver until a workaround is found. :(

---

### Post by kg4gyt on 2005-12-13
I'm having the problem too, Its an AMD 2600+ with 512 RAM and an FX5700 Ultra card, that seems to be a recurring theme, hopefully we'll find something out.  I'm using the drivers from NVIDIA rather than those from Synaptic, and still no luck.  It also freezes whenever I try to switch to a terminal using Ctrl-Alt-F?.

---

### Post by kg4gyt on 2005-12-14
It seems that if you disable usplash in the /boot/grub/menu.lst file the problem is gone.  More of a workaround than a fix, but makes it much more usable.

---

### Post by action09 on 2005-12-17
kg4gyt  You're my hero !!!!!!!!!!!!!:KS 

Many thanks , i disabled usplash in the /boot/grub/menu.lst and uninstall usplash becaus i 'hate' it and all my problems were solved !!!!

A -MA-ZING  ! Awesome :)

I'm really happy and thank you very much  :razz:

---

