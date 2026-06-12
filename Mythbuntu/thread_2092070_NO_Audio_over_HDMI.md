---
title: "NO Audio over HDMI"
date: 2012-12-06
forum: Mythbuntu
---

### Post by jl3comp on 2012-12-06
I'm setting up a new FOXCONN nt-3550 and pairing it with an HD Homerun and my Epson Home Cin 8100 and Yamaha receiver for a hometheater & DVR.

I installed Mythubuntu and got everything running while testing - or so I thought bcs I was testing with headphones.  When I hooked it up to my receiver via HDMI - there is NO AUDIO.  I tried every which way in the MythTV setup.....and only got sound from the headphone jack and the internal speaker.

Under my SETTINGS Tab for MYTHUBUNTU....there is nothing  referring to AUDIO/SOUND....which is where I would expect to find it.   Under the SETTINGS MANAGER Tab, again...nothing relating to sound.  Every other hardware section is  represented there so I would expect to find SOUND or AUDIO.

How do I add Audio to my MYTHUBUNTU install? My Linux knowledge is ...um.....BASIC (but I'm learning ;))

 I ***-U-ME there's a string I needed to run in  Terminal....or an Audio driver to add? Sorry, but nothing on Foxconn site or Newegg's that  tells me anything about the Audio....maker....chip....driver....ZIP! So I can't provide that info.:redface:

---

### Post by nickrout on 2012-12-06
In mythfrontend go into settings and setup wizard (I think that's what it's called, i am not in front of a machine now).

On the second page it scans for audio devices, and you can test each one and see what works.

---

### Post by jl3comp on 2012-12-06
That's what I've done.  MOST options gave no sound at all.  A few pushed sound to the internal speaker and the headphone jack only.

I think my issue is the complete lack of any reference to Sound/Audio in MYTHUBUNTU itself.  In a Windows environment, that would be because there is no software installed.  I doubt Linux is that different in this regard.  

BUT...I'm new to Linux and don't know how to proceed.  I know some things are added to the Linux install through single lines in TERMINAL (which, I admit....I'm utterly clueless about).  Others are added via more of a Windows-type install.

Not sure which I need to do -- 

LB

---

### Post by jl3comp on 2012-12-06
[B][I]WOW!!!!!!!

reply from FOXCONN:

[/I][/B]
I will try to download MYTHUBUNtU and try it  here.  I will let you know.  But which version are you using?  Please  let me know.  Thanks! 

Thanks!. 

Best regards, 
Foxconn support team.

**THAT'S Customer Support!!![-o<[-o<[-o<[-o<[-o<[-o<**

---

### Post by nickrout on 2012-12-06
That is pretty extraordinary support :)

Mythbuntu doesn't have an audio settings dialog that I have been able to find. 

Can you open a terminal and type the following commands and post the outputs? Close mythfrontend (escape until you get out of it). Then click the menu at the top left, accessories, terminal. Or you can ssh in from your desktop, then you can easily cut and paste the output into your reply here.

```
aplay -l
aplay -L
ls -l  /proc/asound/
```

---

### Post by nickrout on 2012-12-06
PS I struck a poster theother day who had a new audio card that wasn't supported in his version of linux, but he was using 10.04. Perhaps you could tell us what version you are using and also the output of ```
lspci
```

---

### Post by jl3comp on 2012-12-06
Thanks again .....here goes:

**aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**aplay -L**

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
default:CARD=SB
    HDA ATI SB, ALC888 Analog
    Default Audio Device
sysdefault:CARD=SB
    HDA ATI SB, ALC888 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC888 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC888 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC888 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC888 Digital
    Hardware device with all software conversions

**ls -l  /proc/asound/**


total 0
dr-xr-xr-x 3 root root 0 Dec  6 19:50 card0
dr-xr-xr-x 6 root root 0 Dec  6 19:50 card1
-r--r--r-- 1 root root 0 Dec  6 19:50 cards
-r--r--r-- 1 root root 0 Dec  6 19:50 devices
lrwxrwxrwx 1 root root 5 Dec  6 19:50 Generic -> card0
-r--r--r-- 1 root root 0 Dec  6 19:50 hwdep
-r--r--r-- 1 root root 0 Dec  6 19:50 modules
dr-xr-xr-x 2 root root 0 Dec  6 19:50 oss
-r--r--r-- 1 root root 0 Dec  6 19:50 pcm
lrwxrwxrwx 1 root root 5 Dec  6 19:50 SB -> card1
dr-xr-xr-x 2 root root 0 Dec  6 19:50 seq
-r--r--r-- 1 root root 0 Dec  6 19:50 timers
-r--r--r-- 1 root root 0 Dec  6 19:50 version

**lspci**

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6310]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

---

### Post by jl3comp on 2012-12-06
Oops....

MYTHUBUNTU 12.04, 64bit

---

### Post by nickrout on 2012-12-06
OK this looks relevant:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/199293](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/199293)

Try running alsamixer in your terminal, it is a command line graphical mixer. Any device that has M underneath it is muted and you need to press the M key to unmute it. The sliders are for volume. Esc to exit.

---

### Post by jl3comp on 2012-12-07
***GOT IT!!!   WhoooWhoooo!!!***  :popcorn:

Thank you NICKROUT for the help....couldn't have done it with out it!

I have ALWAYS loved forums and the willingness of others to help out.  AMAZING EVERY TIME!!!

_**alsamixer**_  worked.  Had to switch to S/PDIF (which puzzled me at first....but HDMI didn't show up, so I gave S/PDIF a try).....then back to MYTH TV FRONTEND setup...page 2.....

Thanks and Happy Holidays!!!


ALSO....big SHOUT OUT to **[COLOR="Red"]Foxconn[/COLOR]** for the extrordinary support!!!  You made a happy customer who will now put your product atop his shopping lists going forward!  KUDOS!!!!

---

### Post by BicyclerBoy on 2012-12-08
That looks like a box of trouble for a HTPC build because of audio & video decode/driver problems..

To get the HDA HDMI audio:
You might get lucky with kernel 3.5 & the open source Radeon driver (using by default)
[http://wiki.x.org/wiki/RadeonFeature#Feature_Matrix_for_Free_Radeon_Drivers](http://wiki.x.org/wiki/RadeonFeature#Feature_Matrix_for_Free_Radeon_Drivers)

I believe your fusion E-350 CPU is a N.Island r600g.

Just recently it **had** even looked like AMD had dropped linux support.

---

### Post by jl3comp on 2012-12-08
Actually I have to say I'm very pleased with the box thus far. My issues were completely self inflicted... And caused by my desire to have a Linux OS instead of Windows.....but not the knowledge to do the install. 

I started out Linux-clueless... ...and yet was able to get it up and running ***THANKS in large part to my fellow forum members*** here & at a couple of other sites. In conjunction with my Epson projector & HD Homerun Prime... This tiny Foxconn unit gives this cable-reducer (paying $14 for basic cable only) basic TV with PVR capability in under 30 seconds....along with the ability to surf, etc if I so desire. I'd be lucky to see a Windows logo in that amount of boot time.

With basic Linux knowledge, I think this setup would have been fairly straight-forward.

Thanks again all!
Larry

---

### Post by BicyclerBoy on 2012-12-08
Don't get me wrong..
Most mythtv/mythbuntu people here are interested in low power cheap mobos & even more interested in others successes.

Have you tried using VA-API with MythTV ?

---

### Post by jl3comp on 2012-12-08
No...what is that? (and if I came across snippy, BicyclerBoy....it wasn't intended.  I appreciate ALL help on these sites....truly.  As I said earlier....without the others that cared enough to send replies....I would have had no choice but to load Windows and been annoyed every time I booted up and waited.....and waited....;))

I'm a COMPLETE NOOB to Linux.  This was my first taste other that a brief "boot from cd" try a few years back.  I've been a PC guy forever....and building my own since the first early Pentium days.  But the where's, how's and why's of Linux have to be spoon fed on the "....for Dummies" level at this point.

I will stay with it.  I was like a little kid on Christmas....it was quite a rush..... when the sound first roared from the surround system yesterday.  I've always loved a mental challenge.

.....and then there's the whole..."sticking it to the man" thingie :guitar:

---

### Post by BicyclerBoy on 2012-12-08
Need to be careful, the problem solving & the challenge becomes more enjoyable than the end result...

I should add about HDMI audio & radeon N.Island ..you need kernel >=3.5 and grub boot parameter:
radeon.audio=1

VA-API is an API for video decode in h/w.

There are few things in linux more confusing than history of the ATI/AMD drivers altho the intel poulsbo must run close 2nd.

There are multiple drivers for AMD radeon gfx. You are probably using the default "radeon" open source driver.

The AMD catalyst driver provides an XvBA interface to VA-API.
XvBA is AMD video decode using UVD & shaders for linux.

The radeon driver (open source) uses 3d engine (not UVD yet).
The radeon driver supports VA-API & VDPAU.
This VA-API support is not complete & does not yet use the UVD engine (decoder ASIC).

To use VAAPI with the proprietary Catalyst XvBA needs package:
xvba-va-driver

I doubt you would get much satisfaction from VA-API without later kernel &, sadly, the proprietary driver.
The xorg-edgers ppa is a good place to update graphics drivers & still be reasonably mainstream.

or this ? (I have not used this.)
[https://launchpad.net/~wsnipex/+archive/xbmc-xvba](https://launchpad.net/~wsnipex/+archive/xbmc-xvba)

Can test the VA-API configuration with
vainfo

---

### Post by jl3comp on 2012-12-10
At this point....everything is running well.  I think I'll let it be...

for now.  ;)

---

### Post by nickrout on 2012-12-10
> **jl3comp said:**
> At this point....everything is running well.  I think I'll let it be...

for now.  ;)Very wise!

---

