---
title: "AC3/SPDIF - mplayer vs. VLC"
date: 2009-03-10
forum: Mythbuntu
---

### Post by isalisb on 2009-03-10
Thanks to all those that went before me, I had no trouble getting SPDIF output from an old emu-1212m card that I had on hand.  Everything pretty much worked fine on the first try, until I tried playing a DVD, ripped DVD ISOs have the same problem.

The video looks great but audio is either silent or it is just static, depending on what settings I've tried.

After hours of trial and error, I decided to try VLC, and it plays everything I throw at it.

I have two questions; 
1. VLC can't be ignoring the AC3 passthrough settings can it?
  If it is downconverting to stereo, I wouldn't know yet.
2. Does anyone know what difference there may be between the two apps that would explain this?

I can work with VLC, but the mplayer interface feels more polished with the way it opens and closes from Mythbuntu and LIRC.  And it drives me crazy knowing that one is working and not the other :)

I'm no Linux guru, but I know my way around.

---

### Post by nickrout on 2009-03-10
what mplayer command line are you using? My recollection is you want something like the following (as well as all the other options):

```
-ao alsa:device=iec958 -ac hwac3,

```
where blah is the name of your alsa spdif device. -ac hwac3 means "send any ac3 unaltered to the soundcard"

you might also like to try 

```
-ac hwdts,hwac3,
```

which should also account for any dts soundtracks.

---

### Post by isalisb on 2009-03-11
> **nickrout said:**
> what mplayer command line are you using? My recollection is you want something like the following (as well as all the other options):

```
-ao alsa:device=iec958 -ac hwac3,

```
where blah is the name of your alsa spdif device. -ac hwac3 means "send any ac3 unaltered to the soundcard"

you might also like to try 

```
-ac hwdts,hwac3,
```

which should also account for any dts soundtracks.

That was kind of it.  I found that the things that worked had mplayer commands.  The things that half worked were simply set to Internal.

Is the Internal player different from mplayer?

The following is working great for playing DVDs:

```
mplayer dvd:// -dvd-device %d -fs -zoom -vo xv
```
I haven't needed the -ac switch yet.

Thanks!

---

### Post by nickrout on 2009-03-11
the internal player is the same player that myth uses for livetv or recordings. mplayer is different, it is an external programme, as are vlc or xine. 

Perhaps you should set everything to mplayer if that works with you.

---

