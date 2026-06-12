---
title: "Looking for  SIS 661/741/760 PCI/AGP drivers"
date: 2010-07-07
forum: Multimedia Software
---

### Post by clementeb on 2010-07-07
Hello,

I have just installed ubuntu 10.04 but I have some problems with scrolling and often the computer freezes although the mouse pointer can move.
Someone kindly suggested that it might be related to the graphic card drivers. The card is integrated in the motherboard.
Any suggestions?
Cheers

---

### Post by MusicalAlchemy on 2010-07-17
[SIZE=3]I had the same problem.  SIS graphics cards are made strictly for windows and they refuse to release a driver for them.  Some guy created drivers for this very problem though, and you can download it at the following site.  

[http://www.winischhofer.eu/linuxsispart4.shtml#download](http://www.winischhofer.eu/linuxsispart4.shtml#download)   

Just find the one that matches your card and download it.  Then, since I'm not sure how familiar you are with Linux, press [COLOR=Red]Alt[/COLOR] and [COLOR=Red]F2[/COLOR] simultaneously then type in  [/SIZE][SIZE=4][COLOR=Red]gksudo nautilus[/COLOR][/SIZE]. [SIZE=4] [SIZE=3]This will open a root browser. Be certain you don't delete or move  something accidentally, being root can be potentially extremely  dangerous to your system.  Then go to [COLOR=Red]file system[/COLOR], then [COLOR=Red]usr[/COLOR], then[COLOR=Red] lib[/COLOR], then [COLOR=Red]xorg[/COLOR], then [COLOR=Red]modules[/COLOR], then [COLOR=Red]drivers[/COLOR], and copy and paste the downloaded driver into there.  You may have to change the end extension of it to[COLOR=Red] .so[/COLOR] .  I had to when I did this with my system.  [COLOR=Black]

This should fix your problem, but you will have to restart your system once you paste it in there.
[/COLOR][/SIZE][/SIZE]

---

### Post by clementeb on 2010-07-19
Thank you very much for your message and the link. It's amazing how some people can work hard for the benefit of everyone!
I do have basic/intermediate knowledge of computers and ubuntu/debian, but the page you mention is a bit too complex for me yet and I am a bit at loss when having to choose what to download.
If I run the ```
sudo lspci
``` command I get [HTML]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA [SiS] (rev 01)
00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter[/HTML]

So I suppose the video card is :
[HTML][SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter[/HTML]

Which drivers should I download? I am using ubuntu 10.04, do I just need to add the repositories and install the whole Sisctrl package?
Or in case this is not the way, how do I find the drivers you mention in your reply to my first post?
Cheers,

Clemens

---

### Post by MusicalAlchemy on 2010-07-19
[SIZE=3]Indeed, it's the way the world should be with everything.  If you agree with that, you should check out The Zeitgeist Movement.  Anyway, I've only been using Linux/Ubuntu for about 6 months myself.  So I'm not totally sure on this, but I would try the one that says [X.org  7.1 (gcc 4.x) ]("http://www.winischhofer.net/cgi-bin/downloadpage.cgi?dllink=http://www.winischhofer.net/sis/sis_drv.o_xorg_7.1.0_gcc4_290906-1.tar.gz")
first.  Just click on it, save the file, and then follow the instructions I have previously given with that file.  Unless, you are using the 64bit version like I am.  With the information you have given, your computer is capable of a 64 bit operation system.  If you installed that version, you will want to download the one that says [X.org  6.8.2 (gcc 3.?; 2005/06/24) ]("http://www.winischhofer.net/cgi-bin/downloadpage.cgi?dllink=http://www.winischhofer.net/sis/sis_drv.o_xorg_6.8.2_amd64_240605-1.tar.gz")
[COLOR=Black]Let me know how that works.[/COLOR]
[/SIZE]

---

### Post by clementeb on 2010-07-20
Wow, thanks for the help.
Things seem to be working fine now. 
By the way, the Zeitgeist movement seems quite interesting.
Cheers,

Clemens

---

### Post by TheOverlord on 2010-07-25
[SIZE=2]Hello i have some problems with the same graphics card ... i tryed everithing that is written here or the site that you guy gave but when i insert the two sites 

[/SIZE]
[LIST]
[*]For binaries: **deb [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./**
[*]For source: **deb-src [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) .**
[/LIST]
[SIZE=2]and after registering the gpg i get the following error.

W: GPG error: [http://www.winischhofer.net](http://www.winischhofer.net) ./ Release: The following signatures were invalid: NODATA 1 NODATA 2

what should i do?:(


[/SIZE]

---

### Post by MusicalAlchemy on 2010-07-26
[SIZE=3]To Clementeb, I'm glad of was able to help you.   

To TheOverlord, I'm sorry, but I have no idea what the problem could be with your situation.  As previously stated, I'm still relatively new to Linux so I don't quite comprehend what you are saying it is doing.  Is it not letting you go to the site?  Sorry I'm of no help right away.[/SIZE]

---

### Post by keith8594 on 2010-08-07
Hello MusicalAlchemy,

I had the exact same problem, and with your kind advice, you've managed to help me out too.

Many thanks,

Keith

---

### Post by MusicalAlchemy on 2010-08-09
I'm glad I could be of assistance.

---

### Post by jorn1233 on 2010-09-13
Hi man i did what you said, it works, but now I can only choose between 800x640 and 640x480 for desktop resolutions and I still can't enable the desktop effects.

any suggestions??

regards, Jorn

---

### Post by MusicalAlchemy on 2010-09-14
I'm not sure what could be causing that except maybe your graphics card is a newer one that the driver is updated enough to handle, as the guy stopped updating them a few years ago.  Or maybe you were a lucky person to receive a low grade card (seems all the sis are low) in your computer. ha. What type of computer do you have, that might help myself or someone else to determine the problem.  As for the decktop effects, I can't use them on my system either as the card isn't powerful enough.  As stated before, I don't know if there is any good SIS card, or at least any good one put in a pre made computer.

---

### Post by augustoschwartz on 2011-07-29
> **clementeb said:**
> Hello,

I have just installed ubuntu 10.04 but I have some problems with scrolling and often the computer freezes although the mouse pointer can move.
Someone kindly suggested that it might be related to the graphic card drivers. The card is integrated in the motherboard.
Any suggestions?
Cheers

========================
Saudações caras!
Consegui resolver o problema com a instalação deste driver em formato [.deb].

Link para baixar: [http://www.4shared.com/get/LdQ_IFSZ/xserver-video-sis671_ubuntu810.html](http://www.4shared.com/get/LdQ_IFSZ/xserver-video-sis671_ubuntu810.html)

:KSDepois da instalação reiniciei a máquina e trabalhou bem.:KS

Minha placa é esta:

[HTML] usuario@usuario-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 IDE interface: Silicon Integrated Systems [SiS] Device 0183 (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)
 [/HTML]Greetings guys!


I managed to solve the problem with the installation of this driver in format [. Deb].

 Link to download: [http://www.4shared.com/get/LdQ_IFSZ/xserver-video-sis671_ubuntu810.html](http://www.4shared.com/get/LdQ_IFSZ/xserver-video-sis671_ubuntu810.html)

 :KSAfter installation rebooted the machine and worked fine.:KS

 My card is this:


[HTML] usuario@usuario-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:08.0 IDE interface: Silicon Integrated Systems [SiS] Device 0183 (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS]  661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)
 [/HTML]

---

