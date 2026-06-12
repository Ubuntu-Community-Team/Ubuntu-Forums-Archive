---
title: "Kubuntu dual monitors -- help!"
date: 2010-03-28
forum: Multimedia Software
---

### Post by madhuxs on 2010-03-28
Hi,
I am new to Linux.
I am running Kubuntu (64bit) on machine with a 1GB ATI Radeon HD 4650 graphics card.
I downloaded and installed the the ATI Catalyst&#8482; Proprietary Display Driver from the manufactures website. The driver installation created shortcuts to &#8220;ATI catalyst control center&#8221; and  &#8220;ATI catalyst control center (administrative)&#8221;. I see the options to enable dual monitors when open the control center is opened, but a pop-up window informs me that I need to login using the &#8220;ATI catalyst control center (superuser)&#8221; to make the changes. But I am unable to login to the administrative catalyst control center. When I run &#8220;ATI catalyst control center (administrative)&#8221; there is a password prompt, entering the password shows a quick flash of  &#8220;Authentication failure&#8221; and the window closes. I confident that I am entering the correct password, as I use the same password to make other changes with sudo.

Anyways, I modified the device section of xorg.conf as below, based on an older post to no avail. 
Any ideas how to get dual monitors working? 
Thanks,
M.

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
  Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "DFP (TMDS), CRT" 
  Option "DFP1Hsync" "24-94" 
  Option "DFP1VRefresh" "50-76"  
  Option "CRT2Hsync" "24-94" 
  Option "CRT2VRefresh" "50-76" 
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "RightOf" 
  Option "MetaModes" "1920x1080-1920x1080" 
  Option "MergedXineramaCRT2IsScreen0" "true" 
EndSection

---

### Post by Kubunteando on 2010-03-29
Which version of the catalyst drivers are you using?

---

### Post by Kubunteando on 2010-03-29
It seems AMD Catalyst Control Center uses amdxdg-su to get superuser access. In my case with Karmic 64bits and catalyst 10.3 it does not find the executable.

For some people this has worked:

Easy fix for me was:
Rightclick the K menu and select Menu Editor.
Search for AMD Catalyst Control Center Administrative and change the command "amdxdg-su -c amdcccle" to "kdesudo amdcccle"

---

### Post by IconK7 on 2010-08-12
Had same problem, first with ATI Catalyst Control Center installed from Hardware Drivers/KPackageKit, then I downloaded from ATI website. The Easy Fix worked for me too ("amdxdg-su -c amdcccle" to "kdesudo amdcccle").

Dual Display working as advertised.

(using Kubuntu 10.4 64-bit with Radeon HD 5850)

---

### Post by Vasteel4511 on 2011-01-15
Hi All,

I had the same problem getting into the Catalyst Control Center in admin  mode, changing the menu shortcut didn't help but doing 'sudo amdcccle' from terminal went in OK.

Kubuntu 10.10 64bit on Dell Studio 15, Radeon 5740

---

### Post by r0g on 2011-01-24
Cool, glad to hear you've all got it up and running under KUbuntu :)

I have two questions...

Firstly: Have any of you used the Catalyst software under Gnome to do multiple desktops? And if so did it work smoothly?

Secondly: How's the performance with HD video content and Compiz effects? No really interested in games but I do like my desktop cube! ;)

Cheers,

Roger.

---

### Post by perixx on 2011-03-09
Kubunteando,

you saved my day, huge thx! This thread should get marked as 'solved' and become 'sticky'... will save hours or more of lifetime for a lot of people, I feel!

Edit:

For manual configuration purposes, I'm adding a clean dual-screen xorg.conf here, which might help some people:
```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "0-DFP2"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1600x1200"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "0-DFP1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1600x1200"
        Option      "TargetRefresh" "60"
        Option      "Position" "1600 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP2" "0-DFP2"
        Option      "Monitor-DFP1" "0-DFP1"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   3200 3200
                Depth     24
        EndSubSection
EndSection
```

I've also read about XranR will not work with fglrx, so it might need to get disabled in xorg.conf and /etc/ati/amdpcsdb:
[http://ubuntuforums.org/showthread.php?t=1164888&highlight=fglrx+dual+screen](http://ubuntuforums.org/showthread.php?t=1164888&highlight=fglrx+dual+screen)

---

