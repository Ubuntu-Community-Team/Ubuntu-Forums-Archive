---
title: "How to install mplayer2"
date: 2020-03-30
forum: Multimedia Software
---

### Post by satimis on 2020-03-30
Hi all,

Ubuntu 18.04

Problem on old VCD quality

Just purchased a new ASUS internal DVD writer (DRW-24D5MT 24X DVD Writer).  I can play DVDs, music CDs and VCDs on it.  But some old VCDs are jerking on screen with unclear sound.  I have them fully cleaned with "glass cleaning solution" but without much improvement.  On visual checking they look without damage nor dirt on them.

So I start to convert one of those old VCDs to mp4, running VLC, but the mp4 file created without improvement on quality, still jerking on screen and with unclear sound.

I'm in anticipation that such problem can be improved using another application.

On installing mplayer2 with following commands
$ sudo apt update -y
$ sudo apt install -y mplayer2```

.....
Package mplayer2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mplayer:i386 mplayer

E: Package 'mplayer2' has no installation candidate

```
Please advise where can find 'mplayer2'

Thanks in advance.

Regards
satimis

---

### Post by tea for one on 2020-03-30
Isn't the package just called **mplayer** rather than **mplayer2**?

---

### Post by satimis on 2020-03-30
> **tea for one said:**
> Isn't the package just called **mplayer** rather than **mplayer2**?
According to my finding;

Differences from MPlayer to mplayer2
[https://github.com/mplayer2/mplayer2.org/blob/master/source/differences.rst](https://github.com/mplayer2/mplayer2.org/blob/master/source/differences.rst)
Improvements over MPlayer

satimis

---

### Post by tea for one on 2020-03-30
The link you provided is dated 20 June 2012, almost 8 years ago.

I would suspect that those features are probably now incorporated into **mplayer**.

Anyway, there is only one way to find out and that is to install **mplaye**r and see if it does what you need.

By the way, there is also **smplayer** with a GUI.

Good luck

---

### Post by slickymaster on 2020-03-30
*Thread moved to **Multimedia Software**.*

---

### Post by mc4man on 2020-03-30
mplayer2 is long dead, 6+ yrs.
Try either MPlayer or what 'superseded' mplayer2, mpv
mpv is currently being actively developed, MPlayer is basically dead with just some bug fix maintenance.

---

### Post by ipv on 2020-03-30
> **satimis said:**
> Just purchased a new ASUS internal DVD writer

no buffalo ;)

> **satimis said:**
> Please advise where can find 'mplayer2'


i only recommend 2 media players, if you want one with all the jazz go vlc.

if you do not need the bells & whistles that vlc comes with go mpv.

---

### Post by satimis on 2020-03-30
> **tea for one said:**
> The link you provided is dated 20 June 2012, almost 8 years ago.

I would suspect that those features are probably now incorporated into **mplayer**.

Anyway, there is only one way to find out and that is to install **mplaye**r and see if it does what you need.

By the way, there is also **smplayer** with a GUI.

Good luck
Thanks.  It is on repo

$ apt policy smplayer```

smplayer:
  Installed: (none)
  Candidate: 18.2.2~ds0-1
  Version table:
     18.2.2~ds0-1 500
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

```
satimis

---

### Post by satimis on 2020-03-30
> **ipv said:**
> no buffalo ;)
no buffalo

It is available.  The retailer advised me taking the internal ASUS DVD writer to replace my defective one which is Sony internal DVD writer, and SATA interface is faster than USB connection.

The new DVD writer is working without problem.  Some of my old videos came with several disks and I run following command merging their mp4 files;```

$ ffmpeg -i "concat:input1.mp4|input2.mp4|input3.mp4" -c copy output.mp4

```
It works better than the GUI of VLC

> 
i only recommend 2 media players, if you want one with all the jazz go vlc.

if you do not need the bells & whistles that vlc comes with go mpv.
What I'm going to do is to see whether I can repair following defects on my very old VCDs;
jerking, choppy, stutter

satimis

---

### Post by SeijiSensei on 2020-03-30
If mpv won't work, I doubt we can suggest anything better that will.

---

### Post by CelticWarrior on 2020-03-30
> **satimis said:**
> What I'm going to do is to see whether I can repair following defects on my very old VCDs;
jerking, choppy, stutter

You can't and it will be a waste of time, energy and money.

The expected lifespan for optical media we had predicted in the 80s proved to be much less. CDs and DVDs do degrade quite fast if the right (or wrong in this case) conditions are met. And unlike what happened with laserdiscs (google "LD rot") the defects are seldom visible to the naked eye.

---

### Post by mc4man on 2020-03-30
Certainly burned media has a limited life. Most likely affected by ,
post burn storage & care.
quality of burner drive, quality of burns as far as errors. (no burn is absolutely perfect..
And most important, the quality of blank media.

Here in my burning heyday (2001-2008) I only used made in japan dvd's for single layer, made in singapore for dual layer. Mainly Tiayo Yuden, Verbatium, and some mij Sony, never from large pancake packs.
Drives were only plextor and benq.
As I'm in the current us "epicenter" spending a lot of time home so broke out some discs from storage, all are fine so far at 12 - 19 years...

---

### Post by mc4man on 2020-03-30
You could always try dvdisaster to rip your vcd's to image (if it will do that media
If it encounters bad sectors it will try x number of times to read.

---

### Post by satimis on 2020-04-04
Hi all,

I have solved the problem by ripping the VCD .dat file to .mpg.  Afterwards converted .mpg to .mp4

Steps performed as follow;

Insert VCD on DVD Writer

start k3b (it is on repo)
-> Tools -> Rip Video CD -> Start Ripping
Rip File to (select the folder)
-> Start Ripping
wait to finish
a .mpg file created

On Terminal run```

$ ffmpeg -i input.mpg output.mp4

```

That is all.  I have tried 2 damaged VCDs with jerking sound and screen.  The .mp4 files created are perfect without such problems.

An magnificent movie
The Guns of Navarone (film)
[https://en.wikipedia.org/wiki/The_Guns_of_Navarone_(film)](https://en.wikipedia.org/wiki/The_Guns_of_Navarone_(film)) 

Anyway lot of thanks for your help.

Regards
satimis

---

