---
title: "Can't get my TV Tuner card to work on Ubuntu.  (Brooktree bt878)"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Marlonsm on 2009-05-03
I have a generic TV Tuner card and I'm I can't get it to work.
It comes from ViewTech, but when I type lspci, that's what I get about the card:

```
04:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

I've already searched Google and the forums, I've seem people that got this problem solved, but I still had no success.

When I run xawtv, that's what I get:
```
xawtv
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.28-11-generic)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
v4l2: WARNING: framebuffer base address mismatch
v4l2: me=(nil) v4l=(nil)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

```

And with TVTime
```
tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml

```


What can I do?

This card (after lots of tries installing the drivers, worked on Windows XP).

---

### Post by Marlonsm on 2009-05-04
Bump.
I really want that card working, besides a few games, it's the only thing that Windows can do that Ubuntu can't.

---

### Post by Cresho on 2009-05-04
put your output here.  I am curious

```
xawtv -hwscan
```

---

### Post by Marlonsm on 2009-05-04
here it is:
```
 xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.28-11-generic)
looking for available devices
port 280-311
    type : Xvideo, image scaler
    name : NV17 Video Texture

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video ( *** UNKNOWN/GENER
    flags: overlay capture tuner 

```

---

### Post by Cresho on 2009-05-04
right click on mouse on desktop Create document->empty file
open up the file with Applications->text editor
and put this in
```

#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 -d /dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;
```

save as "tvtime.sh" no quotes please and close text editor
right click on the file and properties->permissions-> tick "allow executing file as program"

you can create a new entry in the menu system and access the sh file directly.

or double click on it to execute it run.  let me know whats going on.  you may make the string simpler if you cannot use the above like this


```

#!/bin/bash
tvtime --g 480x360 -d /dev/video0
```

---

### Post by Cresho on 2009-05-04
if you search google for "Cresho tvtime record transcoder", you can find out How I use tvtime to record shows or video inputs.

and also if you look further for example if you have 1 cam, hdtuner and tvtuner, you can actually see how I managed to not let these cards switch between video1 and video0 and video2

---

### Post by Marlonsm on 2009-05-04
It didn't work.

TV Time opened, showing a blue screen, written "no signal"

---

### Post by Cresho on 2009-05-04
it works......your hardware works fine.  now you need to configure your tv time tuner to work for brazil and not usa.  you need to learn how to use tvtime.\

hardware works and tvtime works and i just set it up for you.  tv time works with right clicks.  If I was there, i can get it to work but i cant.  you just now need to set up your software since it all works.


blue screen says it has a signal but it puts up a blue screen because it is a feature so you cannot see static.

tvtime defaults to card video0 so my sh file is not needed.  but you need to configure the software.

---

### Post by Cresho on 2009-05-04
I forgot to mention that you need to set the

frequency first.  cable, over the air,

then you do a scan for channels

then you configure your audio if you have no sound

---

### Post by Marlonsm on 2009-05-04
Thank you. :)

It's half working now!

At least now I know there is a way to make it work.

I only have two problems now, both on xawtv and on tvtime.
-No sound (the sound in my card is kind of weird, it does not use the computer's output, it has its own, so I have to use a dongle to connect it to my speakers).
-Despite the channel I choose to see, it'll only show channel 62 (Discovery).

But it think that if I mess up with the configuration it'll end up being solved.

---

### Post by Cresho on 2009-05-04
connect your video out of the pci into your video line in of your pc.  you can then use the mixer to open the audio channel.

for cable, use HRC and try others in ntsc cable mode.  for each one, do a channel scan

---

### Post by Marlonsm on 2009-05-04
> **Cresho said:**
> connect your video out of the pci into your video line in of your pc.  you can then use the mixer to open the audio channel.
I don't think that's the problem. The dongle seems to be working fine.
I've connected a music player to the computer the same way the TV Tuner sound should be connected and it worked.
So the problem with the sound is that the Tuner is not outputting the sound.

> **Cresho said:**
> for cable, use HRC and try others in ntsc cable mode.  for each one, do a channel scan
I still didn't get the channel selection to work.
The only channel that was working (62) was the last one I've watched in Windows. Now, I've booted on Windows and changed the channel to 5. Back to Ubuntu, the Tuner isn't working anymore.

EDIT: Booting on Windows and changing the channel to 64 also made TV stop working on Ubuntu, but if I put the channel back to 62, it start working again.

---

### Post by Cresho on 2009-05-05
appearantly, you need to correctly choose your channel mode in tvtime.  After finding the correct channel mode for your area works on, you scan your cahnnels.  You may need to scan for each channel mode.  after this happens, it correctly will create the xml file needed with all information.  you use your up down arrow keys to change channel.


About your sound:  This is easy but I am not there to correctly configure your hardware so this is either going to take too long bouncing information back and forth or you can do further research.

what I do suggest you do is get tvtime running with your only channel working, then you do a alsamixer in terminal and open up the audio channels.

also, you can give your "#amixer controls" without quotes or number sign terminal output here to see what your audio card supports.  also you can give your lspci and lsusb output here because we need to see what audio is actually available.

---

### Post by Marlonsm on 2009-05-05
Here:

amixer controls:
```
amixer controls
numid=34,iface=MIXER,name='Master Playback Switch'
numid=33,iface=MIXER,name='Master Playback Volume'
numid=9,iface=MIXER,name='Headphone Playback Switch'
numid=35,iface=MIXER,name='PCM Playback Volume'
numid=18,iface=MIXER,name='Front Mic Boost'
numid=19,iface=MIXER,name='Front Mic Playback Switch'
numid=17,iface=MIXER,name='Front Mic Playback Volume'
numid=2,iface=MIXER,name='Front Playback Switch'
numid=1,iface=MIXER,name='Front Playback Volume'
numid=4,iface=MIXER,name='Surround Playback Switch'
numid=3,iface=MIXER,name='Surround Playback Volume'
numid=7,iface=MIXER,name='Center Playback Switch'
numid=5,iface=MIXER,name='Center Playback Volume'
numid=8,iface=MIXER,name='LFE Playback Switch'
numid=6,iface=MIXER,name='LFE Playback Volume'
numid=13,iface=MIXER,name='Line Playback Switch'
numid=12,iface=MIXER,name='Line Playback Volume'
numid=11,iface=MIXER,name='CD Playback Switch'
numid=10,iface=MIXER,name='CD Playback Volume'
numid=15,iface=MIXER,name='Mic Boost'
numid=16,iface=MIXER,name='Mic Playback Switch'
numid=14,iface=MIXER,name='Mic Playback Volume'
numid=21,iface=MIXER,name='PC Speaker Playback Switch'
numid=20,iface=MIXER,name='PC Speaker Playback Volume'
numid=23,iface=MIXER,name='Capture Switch'
numid=22,iface=MIXER,name='Capture Volume'
numid=30,iface=MIXER,name='IEC958 Default PCM Playback Switch'
numid=26,iface=MIXER,name='IEC958 Playback Con Mask'
numid=27,iface=MIXER,name='IEC958 Playback Pro Mask'
numid=28,iface=MIXER,name='IEC958 Playback Default'
numid=29,iface=MIXER,name='IEC958 Playback Switch'
numid=32,iface=MIXER,name='IEC958 Capture Default'
numid=31,iface=MIXER,name='IEC958 Capture Switch'
numid=25,iface=MIXER,name='Channel Mode'
numid=24,iface=MIXER,name='Input Source'

```

lsusb:
```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:7904 Hewlett-Packard 
Bus 002 Device 002: ID 062a:6725 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lspci:
```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
04:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
04:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
04:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
04:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```

The part I'm not understanding is that having or not having TV signal on Linux seems to be depending on the last channel I've watched in Windows. (I've tried 3 channels: 5, 62 and 64, it only worked if the last channel I've watched was 62)

---

### Post by Cresho on 2009-05-05
your television tuner is set on the last channel viewed.  When I watch tvtime in linux and I go back to windows and open up the television tuner, I watch the last channel I saw from linux.  This is not the problem.  The problem comes if your television tuner can decode your area signal.  I have 4 television tuners here at my house and out of those 4 pci tuners , only 1 can decode cable and the other can decode ATSC but each of thse 2 are dual in nature so I actually have 8 tuners but they are dual in nature for each.  I have 4 available 2 used at a time so I can watch television from atsc or cable at the same time but I cannot view 4 channels at the same time.

For your audio, it works.  I see your audio device available.  what you need to do is grab the line out from your tv tuner (unless it is digital) and plug it into your sound audio card line in.  I forgot to mention i need to see your ls /dev and also in terminal use alsamixer and upen up your inputs.  you need to play with this.  alsamixer in terminal.  You get a better response than the gui mixer.  This is how I initially fix my problem the first time and after that I don't need to play with it anymore and use the gui mixer.  Ubuntu is going through some changes regarding pulseaudio.  Until then, we are stuck with crap!

one last thing, if you are using a digicam for your pc, this will switch between /dev/video0 to 1 for either.  It will randomize and this could be a problem as well.  I have a fix for that as well.

I put up a pic so you can see both my tuners running.  Sorry for the low quality pic.

---

### Post by Marlonsm on 2009-05-05
here is ls /dev:

```
ls /dev
adsp                null        snd      tty40           usbdev2.3_ep01
agpgart             nvidia0     sndstat  tty41           usbdev2.3_ep82
audio               nvidiactl   sr0      tty42           usbdev3.1_ep00
block               oldmem      stderr   tty43           usbdev3.1_ep81
bus                 parport0    stdin    tty44           usbdev4.1_ep00
cdrom               pktcdvd     stdout   tty45           usbdev4.1_ep81
cdrw                port        tty      tty46           usbdev5.1_ep00
char                ppp         tty0     tty47           usbdev5.1_ep81
console             psaux       tty1     tty48           usblp0
core                ptmx        tty10    tty49           usbmon0
cpu_dma_latency     pts         tty11    tty5            usbmon1
disk                ram0        tty12    tty50           usbmon2
dsp                 ram1        tty13    tty51           usbmon3
dvd                 ram10       tty14    tty52           usbmon4
dvdrw               ram11       tty15    tty53           usbmon5
ecryptfs            ram12       tty16    tty54           v4l
fd                  ram13       tty17    tty55           vbi0
fd0                 ram14       tty18    tty56           vcs
full                ram15       tty19    tty57           vcs1
fuse                ram2        tty2     tty58           vcs2
hidraw0             ram3        tty20    tty59           vcs3
hpet                ram4        tty21    tty6            vcs4
initctl             ram5        tty22    tty60           vcs5
input               ram6        tty23    tty61           vcs6
kmem                ram7        tty24    tty62           vcs7
kmsg                ram8        tty25    tty63           vcs8
log                 ram9        tty26    tty7            vcsa
loop0               random      tty27    tty8            vcsa1
loop1               rtc         tty28    tty9            vcsa2
loop2               rtc0        tty29    ttyS0           vcsa3
loop3               scd0        tty3     ttyS1           vcsa4
loop4               sda         tty30    ttyS2           vcsa5
loop5               sda1        tty31    ttyS3           vcsa6
loop6               sda2        tty32    urandom         vcsa7
loop7               sda5        tty33    usb             vcsa8
lp0                 sda6        tty34    usbdev1.1_ep00  video0
mapper              sequencer   tty35    usbdev1.1_ep81  xconsole
mem                 sequencer2  tty36    usbdev2.1_ep00  zero
mixer               sg0         tty37    usbdev2.1_ep81
net                 sg1         tty38    usbdev2.2_ep00
network_latency     shm         tty39    usbdev2.2_ep81
network_throughput  snapshot    tty4     usbdev2.3_ep00

```

video0 is there (I think that's what you want to know)

I've checked and the TV system in Brazil is very simmilar to USA, so the config should be the same.

What I still can't understand is what hapened today:
Yesterday night I could see the TV image on Linux(only channel 62, tho), I powered off the computer
Today, when I powered the computer on, both TVTime and xawtv were indicating no signal.
I booted Windows and left it on channel 64 and came back to Ubuntu
I still didn't get images, but the "no signal" message was gone
I booted Windows again and left it on 62
Back on Ubuntu, I can now see only channel's 62 image, despite the channel I choose to see.

The image shows Discovery (62) even if I want to see channel 3(or any other one).

And about the sound, I've connected the audio out on the TV card to an working audio in on my sound card. I've also tried connecting the audio out directly to the speakers. But I still got no sound.

---

### Post by Cresho on 2009-05-06
come to think of it, I ran into this problem as well.  after screwing around with the alsamixer in terminal, I noticed I had no sound in certain channels.  So in tvtime, I switched between sap, stereo, mono and this is how I got sound to work.  There are many problems in jaunty jackalope that I decided to stick with the LTS hardy heron.  I have no problems.  Thought I mention this info.

---

