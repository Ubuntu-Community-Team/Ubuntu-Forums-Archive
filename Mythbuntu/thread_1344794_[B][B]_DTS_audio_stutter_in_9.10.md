---
title: "[B][/B] DTS audio stutter in 9.10"
date: 2009-12-03
forum: Mythbuntu
---

### Post by dibuntux on 2009-12-03
Hi, I have finally set audio to S/Pdif out and manage to get it sound on my Denon AVR1610 ampli. All is fine as long as it is Dolby of any kind... with .mkv files encoded with DTS audio I get stuttering, noise and choppy audio.
I'm using the Internal player.
The system is connected with coaxial S/Pdif and the audio device is Nvidia ALC888 onboard.

Any ideas? TIA

Mythbuntu 9.10 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9500GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
HVR1110 DVB-t
dibuntux is online now Report Post   	Edit/Delete Message

---

### Post by concordfta on 2009-12-03
yes, it's the internal player.  I played the file with mplayer and it worked fine.

---

### Post by dibuntux on 2009-12-04
Thanks! I realize that mplayer is not installed anymore by default (since the internal) - to run VDPAU I have to install a special version or just apt-get install mplayer?
And what command line you have to use for VDPAU? TIA

---

### Post by codered867 on 2009-12-04
You can set up mplayer to be your default player for mkv files if you want or all files for that matter. Goto  Utilities/Setup->Setup->Media Settings->Video Settings->Player Settings here you can setup a default player. If you want to use mplayer I would suggest a line like:
```
mplayer -fs -quiet -zoom -vo vdpau -fs %s
```
You will also have to define the rule to use for the file-type which will be found at Utilities/Setup->Setup->Media Settings->Video Settings->File Types

---

### Post by dibuntux on 2009-12-16
Sorry for the long delay... did not know what ro reply...

I have a strange problem: 
1) yes, mplayer solve the problem as you suggested - thank you!
2) on some files, mplayer says that the file is not found. Tried renaming the file, but nothing.
3) Unfortunately the file I was using for test was one or those, so confusion happened - the rule section of Video Settings>File types is not very clear (not all options are readable with standard mythbuntu theme) 

TIA

---

### Post by dibuntux on 2010-01-28
Problem with DTS audio is still there:

1) files play ok with VLS or Mplayer but...
2) I use storage group, so the above are not an option
3) I'm using Auto build 0.22 PPA and I'm up-to-date, still no DTS
4) also FLVs do not have audio using SPDIF - every time I have to change from SPDIF to standard analog output to play those youtubed and other videos...

Any ideas? TIA

---

### Post by flaterichd on 2010-02-25
I can confirm this.

DTS audio stutters in about 80% of the videos. I wouldn't even call it a stutter. It just seems that it is being cut off on quiet audio bits, and when there is loads going on or there are explosions the audio comes back. So it sounds very choppy.

I am using: 
Mythbuntu 9.04 (going to install 9.10 soon)
Onkyo TX-SR706
Gigabyte GA-E7AUM-DS2H (NVIDIA 9400 integrated chip)
HDMI connection with pass through enabled

Also tried SPDIF connection, which is not handled by NVIDIA chip as far as I understand. Exactly the same behaviour - DTS audio choppy.

Plays fine in Mplayer, also plays fine using PS3.

I also tried remuxing video in ts, avi - same result. 

Couldn't find much differences between DTS streams (bitrate etc) in videos with choppy audio and not choppy audio.

This is really a killer bug, as many videos are DTS only, and I really don't want to be converting them to DD.

Not much information on the net, apart from this thread...

---

### Post by flaterichd on 2010-02-25
Seems to be the same issue:

[http://www.mythtv.org/pipermail/mythtv-users/2009-December/275150.html](http://www.mythtv.org/pipermail/mythtv-users/2009-December/275150.html)

---

### Post by dibuntux on 2010-02-26
I already tried, as per your referred post suggestion, disabling DTS SPDIF passthrough: yes, it does play correctly, but my Denon does not recognize it as DTS anymore.

I believe that disabling DTS SPDIF passthrough will result in the audio stream just being played as AC3 audio...

So the problem is still there...

Even more so, the fact that MPlayer does not work on 0.22 with storage groups. 

We have to wait for 0.23? Any other ideas?

---

### Post by flaterichd on 2010-02-26
Surely it is not just us with this problem? 

Although lack of information in MythTV Trac and around on the internet leads me to believe it could be a combined problem with MythTV and receiver, or something along those lines...

I would post a bug request on MythTV Trac, however:
1. I need to find out the rules for posting bugs on MythTV Trac
2. I need to install 9.10 and confirm the problem still exists

---

