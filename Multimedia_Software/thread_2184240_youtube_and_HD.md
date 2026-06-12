---
title: "youtube and HD"
date: 2013-10-28
forum: Multimedia Software
---

### Post by swipisnt on 2013-10-28
hello guys. so here the problem. when i watching any video on youtube.com and i make it to 720p HD or higher video just stop and i must refres site to watch again. looks like working just on 360p. i find moziila add-ons but first maybe something wrong in my system. any ideas?

---

### Post by SeijiSensei on 2013-10-28
Try the various resolutions of [Big Buck Bunny](http://www.youtube.com/watch?v=YE7VzlLtp-4).  Can you watch at 480p?

Mostly these limitations come from your hardware.  720p runs fine on most modern machines and older ones with NVIDIA or ATI graphics.  Open a Terminal and type "lspci" to see what graphics card ("VGA compatible controller") you have.  For instance, mine is 
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT]
```

---

### Post by shantiq on 2013-10-29
to me also that is the biggest problem on Ubuntu     when  i see any average computer on windows or mac play 1080 and 720 without breaking a sweat

so Seiji when you say hardware    please what does this here indicate?    i have geforce and still only can play up to 480p    after that it drags    1080p freezes


PS   i can play 1080p on smplayer and also on [xbmc ]("http://wiki.xbmc.org/index.php?title=HOW-TO:Install_XBMC_for_Linux")       not on vlc/videos[totem]/mplayer or on YT   ......    and i really do not understand any of this ::]]  i thought the limitation was linux flashplayer and not the hardware ?   am i wrong on this?


> lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS4xx PCI Express Port [ext gfx]
00:11.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 Serial ATA Controller
00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 10)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge
00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
[COLOR=#b22222] 01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2)[/COLOR]
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)



---

### Post by drmrgd on 2013-10-29
I never have any problems playing HD videos on my computer.  I think at 1080 if the network traffic is too high I get a lot of buffering.  Otherwise on 12.04 everything seems to run fine.  Using an NVIDIA card here as well:

```

$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 670] (rev a1)

```

Are you guys using Firefox, Chrome, or some other browser?  Maybe it's a Flash issue or something?

---

### Post by shantiq on 2013-10-29
personally [**[COLOR=#000000]drmrgd[/COLOR]**]("http://ubuntuforums.org/member.php?u=1288128") i have used firefox opera seamonkey midori chromium chrome and same on all of them 480p fine 720p sometimes but mostly not and 1080 with lag so bad it is not worth it ...  my computer is 8 years old with 2.5 gig of ram and Geforce mentioned above; i see windows and macs play hd yt with no trouble whatsoever ...     so i think flashplayer for linux must be the reason in my case; i would like to know and better even like the thread starter how to cure this

---

### Post by SeijiSensei on 2013-10-29
A GeForce 8400 is the minimal hardware required for off-loading video decoding to the graphics chip using NVIDIA's VDPAU technology.  As you observe, you can watch other HD materials through smplayer, presumably with VDPAU as the active video driver.  I presume that means you have upgraded to the proprietary driver as well.

You could activate the hardware acceleration for Flash.  Open a YouTube video and expand it to full-screen.  Next click on the video and choose Settings.  Check the box to activate hardware acceleration, close, and restart the video.  Can you obtain the higher resolutions now?  

Unfortunately there was a problem with the interaction between Adobe's code and the NVIDIA driver that mucked up the colors and led to "[smurfing](http://ubuntuforums.org/showthread.php?t=1949137)" of humans.  After you activate hardware acceleration, try viewing a scene with people in it and see if they all look blue.  If so, you probably won't be able to use hardware acceleration with Flash.  Even this horrendous bug did not deter Adobe from abandoning Linux except for security updates.  There were some efforts at NVIDIA to cope with the problem, but I don't know if they are incorporated into the current driver.  My current machine has an ATI card, so I've fallen behind a bit on NVIDIA developments.

One solution at YouTube is to use the [HTML5 player]("http://www.youtube.com/html5") rather than Flash.

---

### Post by Rawit on 2013-10-30
I had this too... The fix is to remove all the cookies belonging to YouTube.com. If you do that, you can select other resolutions again without hanging.

---

### Post by shantiq on 2013-10-30
hi Rawit   can you please explain with details how to > remove all the cookies belonging to YouTube.com    thanx

PS    ok tried it on seamonkey and for me here makes no difference whatsoever;   altho it loads YT real fast now    [just kept the login cookie]



[ATTACH=CONFIG]247383[/ATTACH]

---

### Post by Rawit on 2013-10-30
I used Firefox + Web Developer Extension -> Cookies - Delete Domain Cookies. This also deletes the login cookie. This + restarting the browser worked for me.

---

### Post by shantiq on 2013-10-30
Thanx Rawit.   Tried it on Firefox too and nooooooooo   for me   .   Might work for other guys no doubt ::]]

---

### Post by SeijiSensei on 2013-10-30
> **Rawit said:**
> I used Firefox + Web Developer Extension -> Cookies - Delete Domain Cookies. This also deletes the login cookie. This + restarting the browser worked for me.

I recommend the [SQLite Manager add-on]("https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/") to massage Firefox databases.  I pointed my copy at ~/.mozilla/firefox/my_default_directory/ and opened the cookies database.  You can manipulate every object that way.  I could sort the cookies by domain, highlight the YouTube ones, right-click and delete them.  You can also edit cookies which can sometimes be helpful.

---

