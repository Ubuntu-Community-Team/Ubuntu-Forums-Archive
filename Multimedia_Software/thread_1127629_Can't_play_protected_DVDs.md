---
title: "Can't play protected DVDs"
date: 2009-04-16
forum: Multimedia Software
---

### Post by noerknhar on 2009-04-16
Hey guys.

I'm kinda frustrated right now. For the last 2 hours I've been googling, aptituding (new word. nice, huh?) and stuff to make some of my original DVDs be played by VLC.

I've found out that libdvdcss2, libdvdread3 and libdvdnav4 have to be installed, configured etc. I've done that (even ran that install.sh-thingy that came with one of 'em). But still: some DVDs (like 5 now?) won't play. "The Bourne Ultimatum" is just one of them but even that one should be playable with these libs installed.

Could anyone give me a hint on maybe what I've forgotten? Or something else to try? I really have no clue how to fix my problem...

Thanks in advance :)

---

### Post by Peasantoid on 2009-04-16
Run VLC from a terminal (command is "vlc") and post the output. I've had this problem too; wondering if we're in the same boat.

---

### Post by SuperSonic4 on 2009-04-16
In some newer dvds there is newer copy protections

---

### Post by noerknhar on 2009-04-16
> **SuperSonic4 said:**
> In some newer dvds there is newer copy protections

That's true. I think this is an x-protect-issue that should have been fixed by now. At least I was able to watch X-Men2 now (I don't know which of the thousands of packages I've installed has helped with that). Doesn't help with Bourne, but that's another story.


For the vlc-output:
> [00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: THE_BOURNE_ULTIMATUM
libdvdnav: DVD Serial Number: 374a4233
libdvdnav: DVD Title (Alternative): G4_R0
libdvdnav: Unable to find map file '/home/noerknhar/.dvdnav/THE_BOURNE_ULTIMATUM.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 41.5% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 45.3% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 56.9% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 69.6% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 76.5% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 89.4% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 96.0% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 99.5% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 100.0% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 99.2% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 99.5% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 99.6% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 99.5% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 99.4% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 99.5% failed
[00000408] main input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 99.6% failed


These main input errors occur because I try to skip past the point that the DVD freezes (directly at the beginning, after chosing your language. That copyright-blabla.)
By the way. When I tried playing the DVD using mplayer, there were CRC-errors all over the place and the video that was shown on the screen looked like a mixture of the green matrix letters, a swarm of bees and all pictures of Da Vinci. This certainly is a copy protection issue.

After hours of googling for solutions, installing of packages, sudoing of scripts and nearly completely destroying apt (dont ask, srsly, dont... ;) ) I could use some good news right now. :(

---

### Post by noerknhar on 2009-04-21
...anyone?

---

### Post by medwyn on 2009-04-21
If you are not opposed to trying a different player I would suggest gxine; it's played any dvd that I have tried.

---

### Post by mdpalow on 2009-04-29
see link in my signature below.

mdpalow

---

