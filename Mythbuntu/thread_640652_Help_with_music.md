---
title: "Help with music"
date: 2007-12-14
forum: Mythbuntu
---

### Post by volkswagner on 2007-12-14
I have my entire cd collection ripped to my hard drive in wma lossless format.  I am unable to even see my library after running "scan for music" on mythbuntu frontend.

When I browse to my music directory (FAT32 partition on same drive as OS) and double click a .wma file totem gives error unable to play.  If I right click and choose play with VLC no error and it looks as if it is playing "time line moves in GUI" but I get no sound.

This is Mythbuntu AMD_64 version running on AMD X2 BE2400 chip. Using onboard audio Audio Chipset  	 Realtek ALC889A.  Sound does work in live and recorded TV.

How can I import library?  How can I get Mythtv to play .wma  music files?

---

### Post by newlinux on 2007-12-14
try playing one of the files with mplayer from the command line and see what the output is and post it back here so we can see it.

---

### Post by volkswagner on 2007-12-14
Well I am trying my darndest.  Since this music was ripped in windows there a spaces everywhere, directories, albums, artists, songs.  Not sure how to get around it here is what I have so far.

eric@FamilyRoom:/windoze/music/John Mayer/Continuum$ mplayer 03_Belief.wma
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) X2 Dual Core Processor BE-2400 (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing 03_Belief.wma.
File not found: '03_Belief.wma'
Failed to open 03_Belief.wma.


Exiting... (End of file)



Wait this is better

eric@FamilyRoom:/windoze/music/John Mayer/Continuum$ mplayer 03*
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) X2 Dual Core Processor BE-2400 (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing 03 Belief.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: Belief
 author: John Mayer
==========================================================================
Forced audio codec: mad
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x163.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)
eric@FamilyRoom:/windoze/music/John Mayer/Continuum$ 

Hope this helps

---

### Post by Steveway on 2007-12-14
You don't have the required codecs.
Try installing ubuntu-restricted-extras or look for the needed codec directly.
Also may I ask why you used WMA to rip your CD's? You know, that's a pretty stupid choice.
If you wanted it lossless then flac would be the wisest choice and vorbis would be the best for a lossy compression.

---

### Post by volkswagner on 2007-12-14
Answers are only easy if you know them.  WMA lossless was my pre-UBUNTU days.  If I knew than what I know now......

Thanks for the help.

I will get right on it.

---

### Post by volkswagner on 2007-12-14
I ran

```
sudo apt-get install ubuntu-restricted-extras
```

Tried to play .wma and got same error.  I rebooted and tried the same with the same error.  Ran sudo apt-get install ubuntu-restricted-extras and was returned already the latest version.

Any other items I may need?

What is mad?  How do I check if I have it?

---

### Post by volkswagner on 2007-12-15
> **Steveway said:**
> You don't have the required codecs.
Try installing ubuntu-restricted-extras or look for the needed codec directly.
Also may I ask why you used WMA to rip your CD's? You know, that's a pretty stupid choice.
If you wanted it lossless then flac would be the wisest choice and vorbis would be the best for a lossy compression.

I installed ubuntu-restricted-extras still no change.

What specifics can be offered to help me find the codecs requires?

This is an amd64 install of mythbuntu so I guess the w32 codecs don't apply.  I see in synaptic the w64codecs are installed.

---

