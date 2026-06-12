---
title: "tvtime on gutsy says &quot;Cannot open capture device /dev/video0&quot;"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by mmcmonster on 2008-01-16
Hi.  I'm trying to set up tvtime on a Gutsy system with a Hauphauge PVR-150.

I already did "sudo chmod a+rw /dev/video0".

When I start tvtime, it states "ivtv: Invalid arguement" and "Cannot open capture device /dev/video0".

If I "cat /dev/video0 > ~/test.mpg", the resultant file is the correct TV channel, so I know I can read from /dev/video0 and the capture card is working.

```

$ tvtime -v
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/karthik/.tvtime/tvtime.xml
cpuinfo: CPU Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz, family 6, model 15, stepping 13.
cpuinfo: CPU measured at 2200.162MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10300000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1280x1024.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is compiz and is EWMH compliant.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 280: NV17 Video Texture.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/karthik/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'ivtv', card 'Hauppauge WinTV PVR-150' (bus 0000:01:0a.0).
videoinput: Version is 65536, capabilities 1030051.
videoinput: Maximum input width: 720 pixels.
videoinput: Card failed to allocate capture buffers: Invalid argument
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (62).

```Any ideas?

---

### Post by wolfen69 on 2008-01-16
your card will not work good (not easily) with tvtime. (i know, i have the same card) read on:

I have a Hauppauge 150 card running on my Gutsy box, and I get live tv by: 

sudo apt-get install ivtv-utils 

open VLC player

File -> open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -c25 (25 is channel number)

which changes the channel.

ivtv-tune -h

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

---

### Post by mmcmonster on 2008-01-17
Thank you.  I knew about the command line way to change channels, but never heard about the java application.  It works fine.  One gripe: The java application has no way to fine-tune a channel.  As it is, some channels don't show up at all, and some others are more fuzzy or in black-and-white. :-(

I guess I'll avoid tvtime for now. :-(  I had problems installing mythtv in the past, but I'll give it a whirl again. :-)

---

### Post by drzipp on 2008-02-18
I have this video problem as well but this appeared only when I went to Gutsy (7.10). It worked fine in Feisty. Mythtv, tvtime, etc. worked fine with no special configs.

I am using a Hauppage pvr 500.

What is the problem? I think is this is an OS issue?

---

