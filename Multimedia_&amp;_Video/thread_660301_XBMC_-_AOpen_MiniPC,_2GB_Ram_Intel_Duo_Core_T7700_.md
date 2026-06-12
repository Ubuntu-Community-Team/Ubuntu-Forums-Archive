---
title: "XBMC - AOpen MiniPC, 2GB Ram Intel Duo Core T7700 (2.4Ghz) CPU Success Story"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by gunja99 on 2008-01-06
Dear all. It seems most of the posts round here are people seeking answers, and I wanted to post my recent success story.

Basically I purchased a 40inch HDTV Samsung last year, and I wanted to be able to replace my XBox (XBMC) with something that did HD (1080/720) content. I purchased an AOpen MiniPC 965-DR, and installed Windows Media Centre on it. Now whilst this was OK, I read recently that XBMC was in progress of being ported to Linux (as the XBox hardware can't cope with HD content). Well I thought, WOW lets try it (as XBMC is by far the best Media Centre I've ever used, and I've used a few.)

Well I did initially have some problems removing the overscan, but it's all fine now, so here's some hints for people who may wish to do the same:

XBMC is better off using the 32bit version of Ubuntu (I'm using 7.10 32bit NOT amd64).
To get SPDIF digital output working, simply open the sound control panel, and check all the inputs/outputs. You will get a new tab on mixer entiitled Switches. Theres one option on there (starts with an E and some numbers). Check it, and sound will start to work, no need to re-install all the drivers as I had read.

I got the latest SVN version of XBMC, added Checklist.txt to the XBMC folder, and ran build.sh. And it works.

Now I got the PC logging in automatically, and running XBMC on startup. Only one thing left is to get the remote control working with Lirc, but I've done enuf for today, overcome so many problems in that'd been holding me back for two weeks, that I don't care the remote doesn't work today. It will do, when I get some time to check it out.

The one thing XBMC is missing is PVR functionality, but this'll come once they get out of Alpha/Beta stages, or they may just link to Myth. For music, and videos it's way easier than anything else. I couldn't get gstreamer to work with h264/mkv content, but don't care NOW!

---

### Post by PJSingh5000 on 2008-01-25
gunja99,

Congratulations on your success, and it's nice to see you are sharing your knowledge with the rest of us.  I have a slightly off-topic question related to your pc hardware...  I also have a AOpen MP-945.  I have installed Kubuntu Gusty 64.  Everything is working great, except I am not able to record audio using the microphone port in the back of the PC.  Have had success using your mic?  If so how did you get it to work?

---

### Post by super_hill on 2008-06-23
I have install the ubuntu 8.04 hardy in the same aopen mini pc, and I also can't record sound ...

---

### Post by PJSingh5000 on 2008-06-24
To be able to use a microphone, I unfortunately had to purchase a Logitech USB headset/microphone.

To use the Logitech USB headset/microphone, I plug it in and run a script, "sound-headset".  To use the on-board sound-chip, I unplug the USB headset/microphone and run a script, "sound-intel."  I've created icons on my desktop to launch these scripts, so I just have to click an icon to change between on-board sound support and the USB device.  Note that you will have to restart already running programs to take advantage of the audio device you choose, but newly started programs will simply use the selected audio device.

*sound-headset*

```
#! /bin/sh -f
asoundconf set-default-card Headset
for name in $(ps ux | awk '/artsd/ && !/awk/ {print $2}'); do kill "$name"; done
for name in $(ps ux | awk '/kmix/ && !/awk/ {print $2}'); do kill "$name"; done
kmix
```

*sound-intel*

```
#! /bin/sh -f
asoundconf set-default-card Intel
for name in $(ps ux | awk '/artsd/ && !/awk/ {print $2}'); do kill "$name"; done
for name in $(ps ux | awk '/kmix/ && !/awk/ {print $2}'); do kill "$name"; done
kmix
```

In Kubuntu, after running either of these scripts, you can launch KMix to adjust properties (like mic volume) of the device you are using.  I'm not sure what the equivalent program in Ubuntu is... it might be gamix.  You will have to modify the above scripts for that program.

---

