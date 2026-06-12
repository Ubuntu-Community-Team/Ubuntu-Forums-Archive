---
title: "Crackly Audio in MythBuntu 7.10"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by Em0ry42 on 2008-02-22
Hi - 

So this is sort of a long story and I figured I'd give you all/most the information:

I happily setup a Feisty/MythTV system in August then upgraded to Gutsy in November and had very few issues after initial setup.  In January I tried to switch TV providers, ended up having a nightmare of a time with a DVB card and just went back to square one and decided to rebuild with MythBuntu.  Thats when all hell broke loose.

At this point:
> MythBuntu 7.10 is running on a:
3.2GhZ P4 HT with 1.5GB DDR333
on an Intel D865*** Board
2.3TB worth of Hard Disk
Audigy 2 ZS Platinum
ATI Radeon 9600 XT
Hauppauge Win-PVR 550 MCE


After beating my head against the wall for a day or so I managed to work out most of the wrinkles with the exception of a crackly audio issue. Two days after I rebuilt and had finally moved around my media files the MoBo/Processor died (I think moving 2 TB worth of data in order to make room for a rebuild just cooked everything.  So I run to the electronics store, spend half a grand and am running a nicer system than I was.

Now:
> MythBuntu 7.10 on a:
2.8GhZ Intel 820 Processor with 2GB of DDR2
on an Asus P5NE-SLI
3.2TB worth of HD
Nvidia GeForce 6200
and Hauppauge Win-PVR 550 MCE

I decided to bail on the Audigy because the integrated sound on this new MotherBoard is good enough for me, and I hoped that a different card may take care of the crackly audio.  I was wrong.

What I've done since:

It seems as though sometimes when I use MythMusic the audio is crackly and sometimes it is not.  At first I assumed that the MCC was using different codecs than what I had with Feisty, and I've been told that the W32Codecs package can be dangerous, so I uninstalled all codecs except libdvdcss (seeing as MythBuntu configured it better than I did in Feisty!!!)

Then I installed gstreamer-ugly gstreamer-bad and the -multiverses for both of those.  No difference.

I even tried plugging my speakers into my MP3 player and the speakers are fine!  I tried opening alsamixer and turning down PCM volume as this is sometimes the crackly audio issue.  It doesn't make a huge difference, I mean as the audio goes down the crackly gets quieter... But doesn't go-away.  It also doesn't help that mplayer and mythtv use the PCM channel for master audio volume (using my remote changes the PCM)

I spend another week reading online and decided to try switching from OSS (which MythBuntu automatically configured me with) to ALSA.  This makes no difference, well since I'm having fun I switch to ESD.  Still no cake.  (BTW it seems there are multiple ways to make this switch and I did these switches using: sudo apt-get install libsdl1.2debian-alsa/oss/esd):shock: I *really* thought this would fix it...

Next I read on the ALSA wiki that sometimes tweaking PCI latency will eliminate crackling. Now this is an area I'm not comfortable in but I thought these wiki's were detailed enough that I could at least give it a go:  I turned down PCI latency for everything to 20 and the Host Bridge to 0.  As well as added the Option PCIRetry True to xorg.conf

No differences.  I tried changing latency for the sound card to everything from 0-90 and it made absolutely no difference. :confused: Shouldn't this make at least some difference?

I really like MythBuntu.  And I DO NOT feel like doing another rebuild of this thing especially seeing as I still get the crackly audio with the LiveCD.  I think these guys have done a great job I just have NO clue what is going on and its frustrating seeing as I had 0 issues before and then as soon as I made the switch to MythBuntu it began.

The other critical info:
```

penney@tv-video:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

penney@tv-video:~$ lspci
...
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
...

```

MoBo manual lists this as a Realtek card.

I've spent hours on #ubuntu with no responses #mythtv refuses to help me saying this isn't their field, and #ubuntu-mythtv is all but dead.

I know there is a lot of information here, a significant amount probably useless but I don't feel like leaving *anything* out.  The crackling audio is to say the least annoying, and seeing as this is a DVR system it is absolutely essential that this get fixed.

If it helps at all, as of last night the thing started locking up (quite randomly) while playing videos, I haven't had time to extensively test it, and based on my past experiences this may have everything to do with the fact Nvidia cards run HOT but right now I feel like I don't know anything.

Any help would be appreciated I just want to get this fixed!

---

### Post by Em0ry42 on 2008-03-02
Apparently MythBuntu re-arranges the audio out channels, Gutsy does not do this.  More specifically - MythBuntu was using the jack labeled by my motherboard and Audigy Center/Woofer as Front channel and since the woofer can't handle the extreme high frequency audio it was crackling.  This is frustrating to say the least as there is no documentation I can find about this and over the last several weeks it may have done damage to my subwoofer.  In any event, anyone who is having this issue:

Make sure MythBuntu is actually outputting to the correct jacks and your speakers are plugged in to the respective jacks.

Anyone have a suggestion as to where I should submit this bug?  MythBuntu *should* use the correct default channels according to the manufacturer.

---

