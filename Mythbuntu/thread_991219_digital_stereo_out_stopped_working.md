---
title: "digital stereo out stopped working"
date: 2008-11-23
forum: Mythbuntu
---

### Post by IndieRockSteve on 2008-11-23
So it worked for awhile, at least a few weeks, then yesterday stopped.

AC3 and mpeg audio work via the digital output, but  stereo (ie like avi, mp3, m4a) don't. They did, in fact they worked earlier in the day yesteday, but then all of a sudden just stopped.

No reboot, nothin'. Can't get it to work in Myth or even mplayer. I've tried playing with every mixer available in alsamixer. Like I said, AC3 and mpeg streams work fine, but mp3/etc is nada.
It's baffling me, anyone have any ideas?

thanks!

---

### Post by Rompalle on 2008-11-24
could it be a codec that needs to be re-installed. Check in MCC.

---

### Post by IndieRockSteve on 2008-11-28
MCC shows all those codecs as installed. I guess I can try reinstalling them.

---

### Post by IndieRockSteve on 2008-11-29
I get this trying to play an mp3 or m4a file...
"AO: AddSamples FAILED bytes=12288, used=1523713, free=12287, timecode=-1"

possibly a driver issue?

---

### Post by Thyferran on 2008-11-29
I've had this problem a number of times too and I'm not exactly sure what causes it. It seems to be that a program crashes and doesn't 'release' the sound system properly or something.

So far the only way I know of fixing it is to do the following:

```

sudo mv /etc/init.d/alsa-utils /etc/init.d/alsa-utils.old
reboot
sudo mv /etc/init.d/alsa-utils.old /etc/init.d/alsa-utils
alsamixer 

```  

Then reset the volume levels on your sound card as everything will be muted. After that it is worthwhile doing a ```
sudo alsactl store
```

If anyone knows of a better way of fixing this one I would love to know.

---

### Post by IndieRockSteve on 2008-11-30
sadly that didn't seem to do it.

you know though, I just noticed that in mythmusic when I "play" a track it doesn't actually look like it's playing, like the clock doesn't move along or anything.

Is there a quick and easy way to do a --reinstall on all packages?

---

### Post by IndieRockSteve on 2008-12-01
bump!

or will I have to re-install and hope this doesn't happen again?

---

### Post by eleniontolto on 2008-12-01
I had this happen to me a while back.  I reinstalled with that hope, and it just happened again.  so...i wouldn't suggest it.

---

### Post by eleniontolto on 2008-12-01
> **Thyferran said:**
> I've had this problem a number of times too and I'm not exactly sure what causes it. It seems to be that a program crashes and doesn't 'release' the sound system properly or something.

So far the only way I know of fixing it is to do the following:

```

sudo mv /etc/init.d/alsa-utils /etc/init.d/alsa-utils.old
reboot
sudo mv /etc/init.d/alsa-utils.old /etc/init.d/alsa-utils
alsamixer 

```  

Then reset the volume levels on your sound card as everything will be muted. After that it is worthwhile doing a ```
sudo alsactl store
```

If anyone knows of a better way of fixing this one I would love to know.

that fixed it!  Thanks!  But I agree...a better fix for this would be nice.

---

### Post by slick666 on 2009-03-15
Filed this one in Launchpad

[http://https://bugs.launchpad.net/mythbuntu/+bug/343306]("http://https://bugs.launchpad.net/mythbuntu/+bug/343306")

---

