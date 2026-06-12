---
title: "Trouble with sound over HDMI with Nvidia ION"
date: 2010-01-04
forum: Multimedia Software
---

### Post by TaterSalad on 2010-01-04
I am having trouble getting sound over hdmi with my Nvidia MCP7A HDMI. The strange thing is that everything works fine in a Live disc, but once I do a fresh install of that Live disc I get no sound, even though my configuration is exactly the same (as far as I can tell). I've checked the little things like alsamixer volumes, aplay -l, etc etc. Everything looks good to me. I can reproduce on multiple TVs so its not the receiver. Video drivers are the same in both live version and installed. aplay -l detects my device. sound/pci/hda/patch_nvhdmi.c already has my correct vendor id in it. Perhaps the following info can help figure out what my installed environment is lacking. I've been at it for days now and I'm stumped! Any ideas?

**[SIZE="4"]Live Disc Info[/SIZE]**

XBMC Live 9.11 (basically a optimized version of Karmic configured to start XBMC, or Xbox Media Center, see [http://www.xbmc.org](http://www.xbmc.org) for more info)
NOTE: My problem is not specific to the XBMC program. Things like aplay and speaker-test don't work either.

**[SIZE="4"]Hardware[/SIZE]**

Acer Aspire Revo R1600

[http://www.newegg.com/Product/Product.aspx?Item=N82E16883103228&Tpk=AR1600](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103228&Tpk=AR1600)

**[SIZE="4"]XBMC Live installed to hard disk via Ubuntu installer[/SIZE]**

(This setup gives me no sound over HDMI)

(This is a fresh install. No additional changes were made)

alsa-info.sh

[http://www.alsa-project.org/db/?f=ab7cef7c7233f8c42756d36e362df684b9147d38](http://www.alsa-project.org/db/?f=ab7cef7c7233f8c42756d36e362df684b9147d38)

xbmc@XBMCLive:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

xbmc@XBMCLive:~$ aplay -L
default:CARD=NVidia
    HDA NVidia, ALC662 rev1 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


### speaker-test executes but NO SOUND over hdmi. I've also tried other device aliases like -D hdmi:0 -D hw:0,3 -D hdmi -D plug:hdmi, etc, etc

xbmc@XBMCLive:~$ speaker-test -D plughw:0,3 -c2

speaker-test 1.0.20

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.637709
 0 - Front Left

xbmc@XBMCLive:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module 190.53 Tue Dec 8 18:51:41 PST 2009
GCC version: gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8)


[SIZE="4"]**XBMC Live Disc**[/SIZE]

(This setup gives me audio over hdmi perfectly)

(This is running as a Live disc, ie not installed)

alsa-info.sh

[http://www.alsa-project.org/db/?f=c95bebdc433f15147fb0be415be4e61e4d0b72ad](http://www.alsa-project.org/db/?f=c95bebdc433f15147fb0be415be4e61e4d0b72ad) [^]

xbmc@XBMCLive:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


xbmc@XBMCLive:~$ aplay -L
default:CARD=NVidia
    HDA NVidia, ALC662 rev1 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

### speaker-test plays audio over hdmi perfectly. other programs play audio over hdmi.

xbmc@XBMCLive:~$ speaker-test -D plughw:0,3 -c2

speaker-test 1.0.20

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.638693

xbmc@XBMCLive:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module 190.53 Tue Dec 8 18:51:41 PST 2009
GCC version: gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8)


**[SIZE="4"]Additional Information[/SIZE]**

I had an idea to run a diff on the two alsa-info.sh outputs of my installed and live version. (non-working and working, see above) I figured that might give me a clue on what I was missing. Most things should be identical with a few exceptions like timestamps, etc.

MacBook-Austin:Desktop Austin$ diff -crB alsa-info_installed.txt alsa-info_live.txt > alsa-infodiff.diff

alsa-info_installed.txt: [http://pastebin.com/f63afa045](http://pastebin.com/f63afa045) (non-working, same as above)

alsa-info_live.txt: [http://pastebin.com/f7b47d46d](http://pastebin.com/f7b47d46d) (working, same as above)

alsa-infodiff.diff: [http://pastebin.com/f79cf9c15](http://pastebin.com/f79cf9c15)

Only a few things caught my attention. At first I thought I had my playback volumes muted (line 525,532) according to the diff. But then I realized that was just for the mic, so that shouldn't matter. The only other thing that I saw was that my Amp-Out vals differed (line 123, 129). Perhaps, a more trained eye will have better luck.

I also managed to build the driver -with-debug=verbose on the non-working setup and I get the following dmesg | grep ALSA:

[http://pastebin.com/f60bf127c](http://pastebin.com/f60bf127c)

Bug has also been reported here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4865](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4865)

---

### Post by Nullexe on 2010-01-05
Hey, I was having the same issue.  Take a look here
[http://imadethisdesign.blogspot.com/2009/11/htpc-zotac-ion-n330-xbmc-vdpau-1080p.html](http://imadethisdesign.blogspot.com/2009/11/htpc-zotac-ion-n330-xbmc-vdpau-1080p.html)

I'm using the Confluence skin and set the following in System Settings
Audio output: Analog
Audio output device: Internal Audio Digital Stereo (HDMI).

And everything worked great for me.

---

### Post by TaterSalad on 2010-01-05
Nullexe: That didn't actually work for me. But nice project!


I did, however, find a solution. For better performance, I had set my iGPU Buffer to manual and set it to 512MB as recommended by many. This is what was causing the problem. If I change it to automatic, it works! I get audio over HDMI perfectly. Perhaps I need more than 1.5GB of RAM for the 512MB buffer to work. Still strange that it worked in a Live disc. I guess considering a Live disc will allocate RAM much different than an install version, that may have had something to do with.

---

### Post by texadactyl on 2012-04-11
I have a Zotac IONITX F-E (Dual-core Atom 330 with NVIDIA ION GPU generation 1) and the procedure below worked immediately with excellent sound quality!

I am running Xubuntu 11.10, XBMC Eden, Sickbeard, and Sabnzbdplus. We use the XBMC Android "Official" client for remote control on my Android phone and my Android tablet (works over WiFi with XBMC).

Here is the procedure.  It is a bit out of date concerning hardware drivers.  I began by creating /etc/asoundrc.conf:
[http://imadethisdesign.blogspot.com/2009/11/htpc-zotac-ion-n330-xbmc-vdpau-1080p.html?showComment=1334184170484#c9100501667733549342]("http://imadethisdesign.blogspot.com/2009/11/htpc-zotac-ion-n330-xbmc-vdpau-1080p.html?showComment=1334184170484#c9100501667733549342")

---

