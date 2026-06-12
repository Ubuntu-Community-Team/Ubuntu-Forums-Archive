---
title: "Ripping Insanity DVDs with Acidrip"
date: 2012-08-26
forum: Multimedia Software
---

### Post by kc5hwb on 2012-08-26
Hi All
A while back I switched from AcidRip to Handbrake because I like the quality better of the overall output, and the fact that it outputs to .m4v which Acidrip apparently won't do.

Anyway, I cannot rip the Beachbody Insanity DVDs with Handbrake because the video comes up out of order when played after ripping.  When scanned by Handbrake, the DVD shows to have 99 tracks, and many of them are about 40 minutes long, which is the length of this 1 DVD I am trying to rip.  Doing a quick Google search for this issue, it appears that the DVD is encrypted (big surprise, but FYI I ripped all of the P90X DVDs with Handbrake and they all came out perfectly).  According to [this article]("http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html") Handbrake is "unencrypted -- removal of copy protection is not supported"  I assumed this is why Handbrake wasn't working.

However, Acidrip doesn't seem to work either, and I think Acidrip supports the ripping of encrypted files.  Here is the debug log from Acidrip:

```
AcidRip message - DVD read ok
AcidRip message - Pushed events onto queue
AcidRip message - Playlist contains 2 item(s)
AcidRip message - Running unlink frameno.avi 2> /dev/null
AcidRip message - Removing frameno.avi if it exists
AcidRip message - Running mencoder dvd://13 -dvd-device /dev/dvd  -alang English   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts abr:br=128  -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=1981 -vf pp=de,crop=0:0:0:0,scale=480:-2    -o "/home/jape/insanity_disc_2.avi"
AcidRip message - Encoding film
MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
There are 99 titles on this DVD.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: en
number of subtitles on disk: 1

success: format: 2  data: 0x540000 - 0x8ebb7000
No matching DVD audio language found!
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
AcidRip message - Playlist completed
AcidRip message - Mencoder interrupted by user
```

Am I missing a codec or something?  Or does Acidrip not decrypt?

This is a brand-new install of Ubuntu 12.04 64-bit.  Previously I had tried with my Ubuntu 11.10 32-bit machine, and was having the same issues.

Thanks for any suggestions.

---

### Post by JohnAStebbins on 2012-08-28
This isn't your classical encryption problem.  This is a structural obfuscation issue.  They have mastered the disc with 99 titles.  98 of which have the chapters mixed in random sequence and 1 is in the correct order.

Generally, HandBrake will attempt to parse the DVD menus in order to find the correct title (dvdnav option must be enabled in preferences).  But there are some discs on which this does not work.

One way to find the correct title is to play the disc in vlc.  Manually navigate the DVD menu to start the correct title.  Then look at vlc's title menu to see which title number is being played. Then in HandBrake, select that title in the title combo box.

---

### Post by kc5hwb on 2012-09-07
Strangely, VLC wont' even play these dics on my Ubuntu box.  VLC will play them on my Windows box, but it takes almost 5 full minutes for them to load.  They really did a number on these discs...

UPDATE:  Handbrake won't open these DVDs either.  I thought that I had opened them before, but now they won't even scan the DVDs at all.  So there doesn't seem to be any way to open/play these on my Ubuntu box, but VLC DOES read them in Windows.

Do I need a codec or something?

---

### Post by BicyclerBoy on 2012-09-07
I might be wrong but..
The windows build of VLC includes static libdvdcss, the linux version does not.
Your stdout messages indicates libdvdcss is not installed.

Have a read:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
especially the install-css bit..

---

