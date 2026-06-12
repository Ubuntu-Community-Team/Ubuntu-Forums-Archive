---
title: "Real Bad Sound Distortion"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by osxdude on 2007-06-12
My Analog Devices (SoundMAX) audio card out has real bad distortion, as the name suggests. I was using headphones and I switched to my iPod because it was so bad.

Any help?

---

### Post by coltrane on 2007-06-21
I get the same thing happening, but only after I switched to the low-latency kernel, tried reinstalling alsa but it still sounds awful.

---

### Post by coltrane on 2007-06-22
Suddenly it now works perfectly, but not sure why. All I done was change the mixer type in 'System-Sounds' menu and rebooted it still did'nt work so changed back and rebooted then it works. Don't know what that was about, but I'm chuffed to bits.:p

---

### Post by Crafty Kisses on 2007-06-22
> **osxdude said:**
> My Analog Devices (SoundMAX) audio card out has real bad distortion, as the name suggests. I was using headphones and I switched to my iPod because it was so bad.

Any help?

I'm not really sure, but you can try "kmix" to lower the volume and change stuff, you should give that a shot:
```
sudo apt-get install kmix
```

---

### Post by coltrane on 2007-06-23
Now I get distortion again myself, not so bad as before, but occasional crackles as if the volume is to high though it is'nt, even with all the sliders down as far as possible in gnome-alsa-mixer still there's distortion.
There wasn't any distortion at all yesterday.
I've only ever had this problem since Feisty and it keeps cropping up al the time.
What's changed with the sound since 6.10?

---

### Post by don_eros on 2007-06-23
Same thing is happening to me (see my post [http://ubuntuforums.org/showthread.php?t=481417](http://ubuntuforums.org/showthread.php?t=481417)).

As I said there, as a quick fix you could try disabling alsa:

```
/etc/init.d/alsa-utils stop
```

For me, that made the distortion go away, even though now I get a low hissing sound. It's still less than ideal, but better than the unusable sound I had before.

I'll keep looking for a fix.

E

---

