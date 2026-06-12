---
title: "No sound at Acer Aspire 4530 Ubuntu 8"
date: 2008-08-29
forum: Multimedia Software
---

### Post by roandica on 2008-08-29
hi, my lappy is :

Acer Aspire 4530 RM70
AMD Turion X2 2.0Ghz

NVidia GeForce 9100M G
2GB DDR2 RAM
160GB HDD
Wireless Atheros
Bluetooth 2.0+EDR

Sound Card in WinXP detected = Realtek High Definition Audio

My VGA - Wifi - Bluetooth - webcam = working 100%
Actually i got Speaker ICON at taskbar ... can adjust volume .. but NO SOUND T_T ...

Have any Idea ... 

Thank You very much

note : i read already another wayout from this forum ... but still cant solved ...

---

### Post by arch0njw on 2008-08-29
The suggestions at these posts has helped me under Kubutnu:

[http://www.kde-forum.org/artikel/13487/3/kde-sound-system-not-working-i-have-sound-and-it-d.html](http://www.kde-forum.org/artikel/13487/3/kde-sound-system-not-working-i-have-sound-and-it-d.html)
[http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-kubuntu-499520/](http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-kubuntu-499520/)

---

### Post by roandica on 2008-08-29
> **arch0njw said:**
> The suggestions at these posts has helped be under Kubutnu:

[http://www.kde-forum.org/artikel/13487/3/kde-sound-system-not-working-i-have-sound-and-it-d.html](http://www.kde-forum.org/artikel/13487/3/kde-sound-system-not-working-i-have-sound-and-it-d.html)
[http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-kubuntu-499520/](http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-kubuntu-499520/)

i very confused .. because if i run alsamixer .. it detected ALC888 but in aplay -l detected chip ALC883 ... which one original my sound card model ? thx

---

### Post by arch0njw on 2008-08-29
Run "lspci" and post the results, please.

---

### Post by roandica on 2008-08-30
> **arch0njw said:**
> Run "lspci" and post the results, please.

00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:15.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0844 (rev a2)
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
0b:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


this my lspci ..

---

### Post by arch0njw on 2008-08-30
roandica,

Looks like your nvidia device isn't being recognized at all.  I did a web search on this line:
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
and got this:
[http://www.google.com/search?q=00%3A07.0+Audio+device%3A+nVidia+Corporation+Unknown+device+0774+(rev+a1](http://www.google.com/search?q=00%3A07.0+Audio+device%3A+nVidia+Corporation+Unknown+device+0774+(rev+a1))

Looks like there are a number of issues with this that seem to stem from needing to install the nvidia proprietary drivers as outlined at this post:
[http://ge.ubuntuforums.com/showthread.php?t=880787](http://ge.ubuntuforums.com/showthread.php?t=880787)

Page 4 has some specific conversation about the sound and how installing the proprietary drivers fixed the problem.  Give that a try and see if that helps.

---

