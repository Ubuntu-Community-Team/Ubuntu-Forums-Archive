---
title: "Myth TV or do I have a choice?"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by WillC36 on 2007-05-18
]Helllo everyone,

I've currently been scouring the forums on how to setup Myth TV, but what I'm wonder is, is this my only choice?
I am running Ubuntu 7.04 and relatively new to Linux.  I own a Happauge PVR-150 and will be purchasing a 2nd hard drive for storing recorded content.  

What I wish to do is simply watch TV on my computer with my capture card and hit a record button if want to record a show.  I don't need scheelduing.  So is MythTV my best choice?

Also should Myth be my best choice I'm a bit confused as to which I install.  This will be running on a stand alone pc performing downloads, video conversion, email, surfing etc etc.  So do I do a combined backend/frontend, frontend and regular desktop, backend and regulard desktop or combined backend/frontend/regular desktop?

Any help is greatly appreciated.

Thanks for your time

Will

---

### Post by newlinux on 2007-05-18
You would want a combined frontend/backend/regular desktop if this is standalone myth machine that you will use graphically for other purposes.

You do have other choices. Freevo for another full system. Or you could simply use something like VLC or XAWTV to watch live TV and the "at" command to schedule recordings:

[http://ubuntuforums.org/showthread.php?t=431793](http://ubuntuforums.org/showthread.php?t=431793)

---

### Post by Bohlio on 2007-05-18
You can watch TV with VLC?? Please explain how :-) 
I have a tuner card (not sure about the model) and all I want is to be able to watch TV, recording isnt a priority for me.

---

### Post by Russty of Oz on 2007-05-18
I am using Kaffeine, which is fine for using  TV  on the computer monitor, and you can do scheduled recordings if you wish to and also instant recordings.  But it is much easier to set up than Mythtv that is why I am using it.  If only I could get nvtv out to work!  I will begin another thread for that one.

---

### Post by newlinux on 2007-05-18
> **Bohlio said:**
> You can watch TV with VLC?? Please explain how :-) 
I have a tuner card (not sure about the model) and all I want is to be able to watch TV, recording isnt a priority for me.

File->Open Capture Device-> PVR. You can also use VLC to stream that content live across the network.

You could use ivtv-tune to change channels with a PVR-150.

---

### Post by Bohlio on 2007-05-18
do you know how to configure my device to work with it? 
thank you :-)

---

### Post by newlinux on 2007-05-18
What tuner card do you have? do you know what device it is (/dev/video0 or similar)? If it is a V4L card you could just use tvtime.

---

### Post by newlinux on 2007-05-18
[http://www.videolan.org/doc/streaming-howto/en/ch10.html](http://www.videolan.org/doc/streaming-howto/en/ch10.html)

---

### Post by Bohlio on 2007-05-18
Im sorry to ask such basic questions, but i dont even know how to find that out... :-(
When i ordered the system from dell, the only thing my invoice said about it was that it was a TV tuner, I never really figured out what model it was (sad, yes i know)
Is there some terminal command that i can type in to see what type it is and if its working?

---

### Post by Bohlio on 2007-05-18
Well, I just installed TVTime, as it seems like a simple enough application for me to use, but It wont start. I think its because of the video card and drivers I am using. I have an ATI X300 and am using the drivers in the Restricted Drivers Manager. I did a little looking and came up with this...
> 1. tvtime not starting when using the Radeon FireGL drivers

With the Radeon FireGL drivers, the user has the option of having OpenGL use an overlay surface, giving 3D graphics without tearing, or video overlay surfaces for multimedia players. This can be set in the Device section for the fglrx of your /etc/X11/XF86Config-4 using:

    Option  "VideoOverlay"       

or

    Option  "OpenGLOverlay"      


I think that may be my problem. Will changing to VideoOverlay effect my graphics performance in any other programs?

---

### Post by newlinux on 2007-05-18
what does 

```
lspci
```

output?

You also might be able to find out by looking at the output of

```
dmesg | more
```

 right after a boot up.

Before troubleshooting TVtime, you should verify you have a card that will work with linux, let alone TVtime or VLC.

---

### Post by Bohlio on 2007-05-19
I dont know what my tuner is in here, If it even detects it. could it possibly be the ATI Unknown device?
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Multimedia controller: ATI Technologies Inc Unknown device 4d53
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

```

Edit: Uhhh Ohh, I found a pretty old unsolved thread on this, apparently the ATI TV wonder shows up as an unknown device. and they never got the problem worked out in that thread.
[http://ubuntuforums.org/showthread.php?t=411785](http://ubuntuforums.org/showthread.php?t=411785)

---

### Post by newlinux on 2007-05-19
Yeah, you probably have one of the ATI TV wonder cards. Some are supported. Some aren't. They use different chipsets which you would get working differently. You'd have to know which one you had to know how to get it working.

Here is some info. Sorry, I probably can't be of much more help.

[http://linuxtv.org/v4lwiki/index.php/ATI/AMD](http://linuxtv.org/v4lwiki/index.php/ATI/AMD)

---

### Post by Bohlio on 2007-05-19
You've helped tremendously already. Thank you soo much!
The best part about Ubuntu really is the support of the people in the community :-)

I'll dig back into this problem in the morning, Thanks once again.

---

### Post by newlinux on 2007-05-19
> **Bohlio said:**
> I dont know what my tuner is in here, If it even detects it. could it possibly be the ATI Unknown device?
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Multimedia controller: ATI Technologies Inc Unknown device 4d53
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

```

Edit: Uhhh Ohh, I found a pretty old unsolved thread on this, apparently the ATI TV wonder shows up as an unknown device. and they never got the problem worked out in that thread.
[http://ubuntuforums.org/showthread.php?t=411785](http://ubuntuforums.org/showthread.php?t=411785)


I just looked at that guys thread, and I don't think his card is supported. He went through some headaches for nothing, most likely. Some of the ATI Wonder cards are, some aren't. ATI linux support in general is spotty.

---

### Post by Bohlio on 2007-05-19
Alright, thats not a huge deal. I dual boot XP and Ubuntu, so i can always switch when i wanna watch TV. Thank you for all your help.

---

