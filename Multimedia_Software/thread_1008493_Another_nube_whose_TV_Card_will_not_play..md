---
title: "Another nube whose TV Card will not play."
date: 2008-12-11
forum: Multimedia Software
---

### Post by phreon on 2008-12-11
I have a Tv card that seems to be recognized by Hardy. I have tried MythTV, MPlayer, Kaffiene, and TVtime and none work. TVtime displays blue screen with "No Signal".
Can anyone suggest something to try. I have been searching and working on this for a week. 

In a terminal I run "tvtime -v" it shows the following.

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/al/.tvtime/tvtime.xml
cpuinfo: CPU Intel(R) Pentium(R) 4 CPU 2.66GHz, family 15, model 2, stepping 7.
cpuinfo: CPU measured at 2660.257MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10400090
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1600x1200.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is Metacity and is EWMH compliant.
xcommon: You are using metacity.  Disabling aspect ratio hints
xcommon: since most deployed versions of metacity are still broken.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 325: NV17 Video Texture.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/al/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'saa7134', card 'Philips EUROPA V3 reference des' (bus PCI:0000:02:00.0).
videoinput: Version is 526, capabilities 5010015.
videoinput: Width 720 too high, using 704 instead as suggested by the driver.
videoinput: Maximum input width: 704 pixels.
tvtime: Sampling input at 704 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (57).


Thanks
P

---

### Post by howefield on 2008-12-11
Have you checked that your card is compatible with linux ?

[http://www.linuxtv.org/wiki/index.php/Supported_Hardware](http://www.linuxtv.org/wiki/index.php/Supported_Hardware)

---

### Post by phreon on 2008-12-11
Hi howefield,

The Philips SAA7134/SAA7135HL chips are supposed o be part of the Hardy Kernel.

lspci -v gives:


02:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
	Subsystem: Philips Semiconductors EUROPA V3 reference design
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at 54000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

Thanka
P

---

### Post by howefield on 2008-12-11
yeah, I had that same card in my computer, (it is a philips computer) and could never get the card to work although to be honest I didn't try particularly hard as I already had a hauppauge which I knew did work, so I swapped them around.

---

### Post by phreon on 2008-12-11
I have read many forum threads and many google threads where folks have had success with the saa7134 using TVTime, Kaffein, MythTV, and Mplayer. I have just not been able to do it so I am appealing to the Ubuntu Forum gods for help. If you let me know what to check, or to do, I will do it and report my findings.
Thanks
P

---

### Post by phreon on 2008-12-12
I looked in the /dev/video0 file using nano and it is empty. Shouldn't this file contain specifics about the TV card in my system?

---

### Post by wolfen69 on 2008-12-12
have you tried vlc player? in vlc, go to file>open capture device>video4linux tab>OK.

---

### Post by phreon on 2008-12-12
I thought vic was for video conferencing on a network?

---

### Post by wolfen69 on 2008-12-12
> **phreon said:**
> I thought vic was for video conferencing on a network?

vlc is a great all purpose media player that ALOT of people use. it is very simple, yet powerful solution for everything from music, video, streaming on a network, radio, tv, DVD's, etc. read about it [here]("http://www.videolan.org/vlc/"). i use it for TV and most multimedia.

---

### Post by phreon on 2008-12-12
Hi wolfen69,
I installed vlc. It did not work.
Gave me an error.

Unable to open 'dvb://'

I am totally frustrated with trying TV on Ubuntu. I have tried every tv app available.

Can't tell what to try....

---

### Post by wolfen69 on 2008-12-12
what is the make and model# of your card?

---

### Post by phreon on 2008-12-12
It is a SmartCard TV card. A Chinese made card sold on ebay. It workes well in Win XP, it is detected in dmesg, and when I run from a terminal tvtime -v it appears that tvtime sees it. I just get no signal. I am betting something simple needs to be set because it is detected by the kernel.
Thanks
P

---

### Post by wolfen69 on 2008-12-12
perhaps [this]("http://ubuntuforums.org/showthread.php?t=1000462") thread will help.

---

### Post by laceration on 2008-12-12
I installed a dvb card that uses SAA7134 awhile back.  Unfortunately I don't remember exactly what I did or write it down.  I do know that the drivers being native in the kernel was not enough.

-I had to get a hold of the firmware and put it in /lib/firmware/2.6.??-??-generic/
-I had to create a channels.conf to get the channels for the dvb card to tune in to.  This involved a couple of programs called dvbtools or something like that.

For instance, for mplayer you put the channels.conf file in /home/pheron/.mplayer/ and use the first value on each line in channels.conf like this:
```
mplayer dvb://KOAD-HD
```

**[http://www.linuxtv.org](http://www.linuxtv.org)** should have the info on how to setup your card and how to get and use the tools to scan your airwaves and create your channels.conf.  Check documentation of other programs you want to use on how to get dvb working.  I remember some were more trouble than they were worth.

---

### Post by laceration on 2008-12-12
I had opened this thread awhile before I read it and didn't see the latest posts.  You may have a hard time finding the firmware for your device.  Good luck.  Frankly this is not an area where Linux has achieved the ease of use that Windows has.  You can't expect plug 'n play and then program software to configure it for you.  It takes a little work.

---

