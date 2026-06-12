---
title: "[SOLVED] No audio anymore from totem, rhythmbox"
date: 2008-10-23
forum: Multimedia Software
---

### Post by HXn on 2008-10-23
All of the sudden, totem and rhythmbox won't play audio (mp3, ogg).  Audio was working fine when I first installed the gstreamer plugins that you are prompted with when first trying to play an mp3 in totem.  Rhythmbox and totem in firefox all played fine.

I tried installing ubuntu-restricted-extras and esound.  Still nothing.

When I run totem and rhythmbox from the terminal, there are no errors.  Both players just sit there, transport bar doesn't move.  Same with totem in firefox.

I know audio is working in general as I can hear audio from youtube, last.fm, and other flash players.

Any ideas?

Thanks

---

### Post by HXn on 2008-10-23
Had to restart X.  Not sure if ubuntu-restricted-extras solved the problem or esound.  If anyone else has this problem, I would recommend

```
sudo apt-get install ubuntu-restricted-extras
```

and restart - see if that works first.

---

### Post by BLTicklemonster on 2008-10-23
My audio went out since last night for no reason. Everything is exactly the same as it was before. I wonder if the updates are messing with anything? I know every time I ever got networking the way I wanted it, an update would mess it back up again, so I've given up on networking here again. I use a thumbnail drive and walk around the house if I want to share anything.

*EDIT: restarted, and still no audio. I'll try restricted extras, but I don't see how that will work, I've had this thing up running with them since Hardy came out. Nope, already have them.

Oh well.

---

### Post by BenWilson on 2008-10-23
> **HXn said:**
> Had to restart X.  Not sure if ubuntu-restricted-extras solved the problem or esound.  If anyone else has this problem, I would recommend

```
sudo apt-get install ubuntu-restricted-extras
```

and restart - see if that works first.

I didn't have to restart, but this worked like a charm for me!

---

### Post by Interpreter on 2008-10-24
You just "locked your soud drivers" which results in various applications not being able to access the sound thingy in the first place, thus, movies or mp3s wont even start and play "mute", in fact they will not play at all.

If you're facing that problem (the sliders aint moving and such...)

..go here and have a looksee
[http://ubuntuforums.org/showthread.php?t=942230]("http://ubuntuforums.org/showthread.php?t=942230")

---

### Post by jaypifer on 2009-07-31
ubuntu-restricted-extras worked for me, too.  Thanks!

No restart needed for me either.

---

