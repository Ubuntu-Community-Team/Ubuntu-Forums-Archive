---
title: "DVDs stop playing in Ubuntu 10.04"
date: 2010-06-19
forum: Multimedia Software
---

### Post by Riffronan on 2010-06-19
Whether I'm using VLC, SMPlayer or Movie Player, any DVD I try to watch will work perfectly for 2-3 minutes and then just stop.  GPU temps stay under 55C and both CPUs stay at around 40 and 30 percent.  I just installed the latest Nvidia driver for my Geforce 8600GT (195.36.24)...compiz runs great too.  As much as I hate to say it, VLC plays DVDs non-stop when I boot up in XP so it shouldn't be a hardware issue.  Using k9copy in 10.04 allows me to watch any ripped movie without it stopping but for some reason, watching anything off a disc doesn't last.  Maybe I need a different DVD driver?  I appreciate your time and help (!)

---

### Post by cchhrriiss121212 on 2010-06-20
Try opening vlc in a terminal, then watch a DVD and post the terminal output of error messages when it crashes.
What DVD drive are you using? I had a [similar problem]("http://ubuntuforums.org/showthread.php?t=1367967") a while back, which did not get solved. Some hardware that works on windows will just not work with my linux machine (despite the same hardware working on other peoples machines) due to kernel issues or other mysterious factors unknown to me.

---

### Post by Riffronan on 2010-06-20
The DVD drive is an Optiarc DVD RW AD-7240S.  I'm seeing alot of posts where CDs and DVDs worked fine in 9.10 but not so in 10.04.  I too never had a problem in 9.10 but hey, I'm a sucker for the 'latest and (not so) greatest'  I'm gonna give Das Boot another test run (like you said) by running vlc from terminal and see what errors come up..oh yea, and in the Grub menu, I'm now loading the .17 kernel instead of the .21 or .22  When Ubuntu now shuts down, I now get a crisp splash screen for Ubuntu Studio...with .21 or .22 it comes up a garbled mess

---

### Post by Riffronan on 2010-06-20
Those last two libmpeg2 decoder error is where vlc hiccups and then stops...the DVD ran for like 3-4 minutes..if we can figure this out, maybe this could help a bunch of other folks out with this same issue....surely it's not relate to my specific DVD drive...I wonder if ALSA vs Pulse Audio is the culprit

```

```bob@bob-desktop:~$ vlc options
VLC media player 1.0.6 Goldeneye
[0x9291668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat options
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[0x94f2780] access_file access error: cannot open file options (No such file or directory)
[0xb74b4788] main input error: open of `options' failed: no suitable access module
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 30908828
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/bob/.dvdnav/DVD_VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f20000. Regions: 1 3 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000380
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00004b00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00004b20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00022840
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000276c6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003ac1a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003ac1c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003b71c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003b71e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003c16c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003c16e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003c8580
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003c85a0
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
[0x95ae0c8] main input error: ES_OUT_RESET_PCR called
[0x95ae0c8] main input error: ES_OUT_RESET_PCR called
[0xb74c3bd0] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x978fcc8] pulse audio output: No. of Audio Channels: 2
[0x95ae0c8] main input error: ES_OUT_RESET_PCR called
[0xb74c18a0] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0xb74c18a0] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x95ae0c8] main input error: ES_OUT_RESET_PCR called
[0xb74c8998] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x978fcc8] pulse audio output: No. of Audio Channels: 2
[0xb74c9f80] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[0x978fcc8] pulse audio output: No. of Audio Channels: 6
[0x95ae0c8] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late, increasing pts_delay to 1862 ms
[0x95ae0c8] main input error: ES_OUT_RESET_PCR called
[0xb74c18a0] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0xb74c18a0] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
```

```

---

### Post by cchhrriiss121212 on 2010-06-20
Here's a thread with the same error message:
[http://ubuntuforums.org/showthread.php?t=1511830](http://ubuntuforums.org/showthread.php?t=1511830)
It's a copy protection thing, that effects everything not using Windows.

Make sure you have medibuntu repositories activated and have libdvdcss2 installed.

---

### Post by mc4man on 2010-06-20
What is the title of the dvd you're playing - appears to be a Sony release.
What happens if you go (assumes /dev/sr0 drive
```
vlc dvdsimple://
```

or if you know the title number of main movie then (adjust blue to title #

```
vlc dvd://@[COLOR="Blue"]1[/COLOR]
```

---

### Post by Riffronan on 2010-06-20
already had libdvdccs2...enabled Medibuntu repository which wasn't before enabled...tried vlc dvdsimple://...no joy.  I'm still curious why 9.04 and 9.10 worked without any problems though.  The DVD is Sony's Das Boot...I do appreciate the help

---

### Post by mc4man on 2010-06-20
Well I have Das Boot but it's the superbit version so can't make a direct comparison. (works fine here as do virtually all dvds

Just to double check something - go into home folder (view -> show hidden files), find the .dvdcss folder and delete it.
Then try vlc again

---

### Post by Riffronan on 2010-06-20
I deleted the folder and vlc still quits...

---

### Post by mc4man on 2010-06-20
If you want to 'attempt' to eliminate pulse then you could try this

In vlc settings - audio, choose alsa as the output module

Then before trying again you need to open synaptic and for the moment remove the vlc-plugin-pulse.

(I just yesterday cut pulse out from my lucid install with a 5.1 system, to actually do 'correctly' and completely is a bit more involved then the above

If no improvement then go ahead and re-install the plugin and set vlc back to pulse in audio output - pick pulse, not 'default'

There has been mention elsewhere that there is a bug in dvdnav, I don't buy it based on I've no issue on 3 separate installs with different hardware

One way to test that is to try using a xine engine player which uses a different dvdnav

---

### Post by Riffronan on 2010-06-20
yea, I was wondering about dvdnav and so now I'm gonna try a xine based player to test that out...leery about 'Jack'ing with the audio setup (badpun)

---

### Post by Riffronan on 2010-06-20
Dragon Player never even gets off the ground and gxine works for about a millisecond.  Maybe this'll be some sort of bug fix for 10.04...thanks again for trying

---

