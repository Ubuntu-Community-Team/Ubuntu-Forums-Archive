---
title: "Screen Res options"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by dykesy61 on 2006-06-11
Hi - I am new to this, and can't get my screeb res up to more than 1024
I have run other linux systems on 1280
I have an Nvidia GeForce Tornado - no idea what capacity it has
a) how do I find out?
b) how can I get better res?

any help appreciated - thanks

---

### Post by tseliot on 2006-06-11
Please, post the output of the following command:
```
lspci
```

---

### Post by dykesy61 on 2006-06-12
phil@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03 )
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media I O] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa st Ethernet (rev 91)
0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller  180 SATA/PATA  [SiS] (rev 01)
0000:00:07.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference C ard (rev 01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

---

### Post by dykesy61 on 2006-06-14
I have now managed to sort it - found out the capcaity of my screen and video card, and edited xorg.conf, and it works!

No reason for not staying with Ubuntu now!

---

### Post by Thought_Criminal on 2006-06-14
Man you are lucky, I can't get my resolution to go larger than 640x480, well I got it to 1280x1024 once but when I restarted X it crapped back out to 640x480 and the changes I made to get it to display 1280x1024 don't make any changes now.

Should I start a new thread for my problem or can I use this one?

---

### Post by dykesy61 on 2006-06-14
actually I found that according to the log file it could not render higher than 1024x768
so I am sticking with it
I think its due to my screen ???

anyone else??

as to whether you can use this thread, it seems to be the same or a similar problem!

---

### Post by sandlam on 2006-06-14
Hi there,

I got the same problem with you guys...
i installed ubuntu 6.06 desktop version to my fujitsu S2020 notebook /w ATI Radeon IGP 320M.
In the Resolution page, there are only 1024X768, 800x600 and 640x480, also, the refresh rate cannot be change.
Furthermore, for the default theme, there is some display error too although it is very miner... (there is some colorful dash on those button, like "OK", "Cancel", when you put a mouse on it, those dash will be cleared.)
I'm still finding the solution...

Can anyone help?

Thank you very much!

---

### Post by cbaumann on 2006-06-15
I've changed my resolution editing the xorg.conf. To be exact, in ```
Section "Screen"
``` ```
Subsection "Display"
``` 

and then 

```
Modes "1280x1024" "1024x768" "800x600"
```

This might help you with your resolution. Remember to create backup of your config before messing with it around. :)

Regards,

---

### Post by burgermann on 2006-06-15
The solution offered by cbaumann doesn't work here.

I edited /etc/X11/xorg.conf and wrote the suggested modes by all depth settings, but this made no change at all. Any help is appreciated.

---

### Post by Thought_Criminal on 2006-06-15
Ok I think I figured out my problem.
I loaded the kde environment and went into the GUI to configure my video card and noticed that there were 2 monitors listed, I set the video driver to 'nvidia' and then restarted X and I then had a full range of resolutions and refresh rates.  I then rebooted and it was back to being stuck at 640x480 and a refresh rate of 60 (I think) so I got mad and went back to mess with my video card settings and noticed that one of the monitors was gone from the GUI.  The monitor that was left was a generic one.  I ran throught the GUI and set up that monitor and now it is good. 

The only problem I am having now is the video is choppy and slow.
I installed the nvidia driver but it is still pretty bad. Last night I went into xorg.conf and made some changes and that totally jacked the xserver.  I removed the xorg.conf file and renamed the back-up of that file that I made and it still wouldn't work.  I then ran the dmsg reconfigure-xserver (or whatever) and it wrote a new xorg.conf file and x still wouldn't start so I will reload I guess.

---

