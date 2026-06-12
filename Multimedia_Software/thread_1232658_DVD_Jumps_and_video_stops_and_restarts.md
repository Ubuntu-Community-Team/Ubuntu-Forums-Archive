---
title: "DVD Jumps and video stops and restarts"
date: 2009-08-05
forum: Multimedia Software
---

### Post by nickzeff on 2009-08-05
I have a very frustrating problem that is driving me crazy.

I am trying to play a DVD, but after a few seconds the video slows down or stops, then jumps forward. The audio also becomes out of sync.

I am running in 9.04.

This is happening in ALL players: VLC, Totem, mplayer, gxzine - you name it, it's not working.

It doesn't look like it is a dma problem (as per [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)), since my dmesg contains the following (but I could be wrong):


[INDENT][    2.136494] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T11N, A103, max UDMA/33
[    2.152455] ata2.00: configured for UDMA/33[/INDENT]


I am working on a Dell D820 laptop. I have tried slotting a completely different DVD drive in my laptop and playing the disc but the problem persists, so it's not the drive.

When I put the disc I am trying to play in a Windows laptop, it plays absolutely fine, so it's not the disc itself.

Anyone, ANYONE able to help please?

---

### Post by TMAN 1 on 2009-08-05
Never heard of this problem before,but I am sure someone will be able to help.
I am curious to this solution myself.

---

### Post by nickzeff on 2009-08-06
Thanks Tman.

Hopefully someone will have some suggestions...?

---

### Post by nickzeff on 2009-08-07
*bump*

---

### Post by nickzeff on 2009-08-07
Oh Well.

I'm really not sure how to solve this one. This DVD issue is a deal breaker I think.

At the end of the day I've had to put so many hacks in place to get Ubuntu working in a satisfactory manner, I think I might try Windows 7 if I can't get a resolution. I know it's locked down by Micro$oft, but I know that many things will just "work".

If anyone can offer ideas I would gladly appreciate it.

---

### Post by ohzopants on 2009-08-07
I have a similar problem with some video files (mostly x264 files) and I've been able to fix it by setting my cpu to a faster speed using the frequency scaling applet.

It seems like I need at least 1.8GHz to play some files, but I'd be amazed if you needed that much power for just a dvd.

---

### Post by nickzeff on 2009-08-07
Thanks ohzopants, but even when I hike up the CPU to 2GHz, the problems persists. The picture just slows down after 10 seconds or so while the audio continues. Then the video goes into fast forward to catch up with the audio track.

*bangs head against wall*

---

### Post by mc4man on 2009-08-07
Maybe post your display adapter, jaunty has had issues with intel and ati, some with nvidia

```
sudo lshw -C display
```

You could try using X11 output rather than Xv
For instance in vlc
go tools -> preferences, click on the video icon and in the output dropdown box switch from default to X11

(( While the laptop I'm on now could easily run jaunty I use hardy instead. Karmic looks like it may be an excellent release, jaunty, well I personally have nothing positive to say.

---

### Post by nickzeff on 2009-08-07
> **mc4man said:**
> Maybe post your display adapter, jaunty has had issues with intel and ati, some with nvidia

```
sudo lshw -C display
```

You could try using X11 output rather than Xv
For instance in vlc
go tools -> preferences, click on the video icon and in the output dropdown box switch from default to X11

(( While the laptop I'm on now could easily run jaunty I use hardy instead. Karmic looks like it may be an excellent release, jaunty, well I personally have nothing positive to say.
Yeah. I'm using nVidia.

I have installed the latest VLC 1.0.1 and put X11 as the output. Makes no difference.

Thanks for the suggestion though.

Incidentally, if I increase the cache size to about 2500ms in VLC the video problems seem to decrease, but the audio continues to stutter.

---

### Post by mc4man on 2009-08-07
Have you tried changing the audio output in vlc from default to something specific, maybe alsa.

You could start vlc from the terminal with this and then try a dvd, The output will be quite extensive
Maybe pick thru and see if anything jumps out, noting that in debug mode vlc will always show some things that appear to be problems but aren't
```

vlc -vv or vlc -vvv
```

Or output to file for easier reading (home folder

```
vlc -vv > vlc_output.log 2>&1
```

 I have a year old dell laptop with the run of the mill nvidia 8400M GS and while there were no issues like you have, decided to return to hardy.
((modded hardy to be as or more capable than jaunty with better overall performance and A/V quality, particuarly with 3rd party apps

Do have high hopes for karmic

---

