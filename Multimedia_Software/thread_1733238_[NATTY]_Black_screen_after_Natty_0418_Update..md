---
title: "[NATTY] Black screen after Natty 04/18 Update."
date: 2011-04-19
forum: Multimedia Software
---

### Post by GTMoraes on 2011-04-19
Hey, the computer in question is a friend's computer that got broken after the update. Been a while since I built his machine, and I barely remember the config. It has a AMD Atlhon II Processor, 2GB worth of DDR2 800 RAM and a cheap motherboard, a Gigabyte GA-M68M-S2P, nForce 630a Chipset (GeForce 7025). The latter I think it's the issue.

	Why I think the graphic card is the issue? Because running X in safemode works. He was using the restricted nVidia drivers on Jockey without a issue before the update. After we managed to get in Ubuntu with X running, I've told him to remove the Restricted driver on Jockey, he said it was successful. After googling for a little while, I've found a instruction that said to remove a nvidia*.ko, nvidia*.o and nvidia*.so files. We did it and he downloaded the .run file on nVidia site. After some fight with Ubuntu to shut down the gdm (Ctrl Alt F1/F2/F3.. was taking him back to the recovery menu), he installed the nVidia driver - according to him - properly. I told him to issue nvidia-xconfig and he said the operation was successful. Restarted and the problem remained.

He said some messages were issued and he said 'yes' to some things. He doesn't know anything about anything of computers (when he saw the black screen with "root@his-computer", he thought he had virus lol), so I'm not sure what happened there. We, then, restarted and gone into "netroot" mode on recovery menu. I told him to install nvidia-glx-185 and he said it was successful. Told him to issue nvidia-xconfig again and he said "it says there's no such thing here". He had a test tomorrow so I told him to catch some sleep and I would be there tomorrow to fix things up.

	But honestly, I don't know what I should do. I might had forgotten to install the build-essential on his computer, so the .run driver might had failed because of this. I've found [this site over the web]("http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux") and I'll try it over there. But I'm not so sure. Like, it was running pretty well before the update, and then - bam. I've reported some bugs recently and I was happy to see my bug reports being answered and the results showing up on the Update Manager, but indeed there are many bugs.

So, I'm actually concerned about the Natty bugs. I know, I know.. it's development branch and I shouldn't install it on someone with zero knowledge on computers because of the bugs, but it worked flawlessly and out-of-the-box on three computers I had installed before (two notebooks and a built computer) so I thought it would be okay to install it. Are there any known bugs with his chipset/videocard that I should know? How should I proceed?

	Thanks in advance. Hope you take some time to help me just like I'm trying to help my friend here.

[size=1]P.S.: Before everything, the Ubuntu loading screen and the GRUB O.S. Select wasn't showing up. The  monitor complained about being "Out of Range" and nothing more, but it  would start as soon as it hit the desktop. I blamed his 2003 LCD  Monitor. Also, for some reason, the only refresh rate it would be usable was 51Hz. I don't know if this is related to the bug, but certainly it's strange..[/size]
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by sanderd17 on 2011-04-19
There are a lot of "black screen" complaints for different nvidea and intel video cards. I have tried all kind of bot options, but I can't get rid of the black screen on my own computer.

It seems that it's not an Ubuntu problem but a Linux kernel problem. You should search the forums for it, you'll find a lot of complaints. Some solved it with setting the "nomodeset" boot option or one of the "acpi_osi=" options. (check my signature)

---

### Post by GTMoraes on 2011-04-19
Thanks, this is great. Might work =)
I'll be there today night (It's 12:50 atm) and I'll report how things going

Thank you again, more tips are welcome
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by GTMoraes on 2011-04-20
For... some reason, after reinstalling drivers, nothing else worked.
Then I tried reinstalling Natty.
I've inserted the media containing the installation files and things went OK. Selected "Remove Ubuntu Natty" option and installed over it. Everything went fine till then.

System start. Locks up, most of the time with messed graphics. Tried running the failsafeX. Text get out of the box and lines get messed around (like if the box "exploded", but not in hardware-failure means) and computer locks up. Tried starting the Ubuntu Live version. Locks up with a fuzzy screen even before the unetbootin blue box disappear. Now there are no means to install, reinstall, fix it or even recover the logs. "Luckily" he still had his Win7 installation so he can use his computer.

Oh, by the way, I've installed his Natty side-by-side with Windows 7 (previously installed), and it was running smoothly before the update.
What might it be? I have no clues what's going on now
[LEFT]__________________________
[/LEFT]

[SIZE=1][CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | Gigabyte GA78GM-S2H | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | Samsung SyncMaster P2250 | 6:30hrs Battery | Ubuntu Natty
|[COLOR=#7FFF00]Microsoft WMM 4000[/COLOR]|[/SIZE]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[size=1]**Ubuntu Powered.**[/CENTER][/size]

---

### Post by latticeguy on 2011-06-13
My old computer dual boots Ubuntu and Debian.  On upgrading Debian to Squeeze, I started having many similar problems.  Then on updating Ubuntu, they were even worse there.  Black screens, freezing computer, horrible scrolling when it worked at all.  I now have it sort of working, in different ways on each system:

Ubuntu:  removing the xserver-xorg-video-intel package forced xorg to use the fbcon device, and this seems to work OK.

Debian:  The above didn't work so I installed the intel driver from Sid, and used "X -configure" to generate a xorg.conf file to go in /etc/X11/  Works kindof, but still horrible scrolling on web pages.

This seems to be a rare problem since you don't find many instances on web searches, but when it does occur it is horrible.  For the time being I'll work mainly with my AMD system and hope it gets fixed.  I want to use my old machine attached to my TV for web video.

---

