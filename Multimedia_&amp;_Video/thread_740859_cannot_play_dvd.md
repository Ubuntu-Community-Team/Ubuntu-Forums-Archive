---
title: "cannot play dvd"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by Mick8882003 on 2008-03-31
I installed the restricted formats but still cannot play dvds.

Thanks in advance

---

### Post by Speedwiz7770 on 2008-03-31
Would you mind telling us what you installed or what you did?? It's very possible that you might have forgotten some dependencies, or the like.

~Speedwiz7770~

---

### Post by Mick8882003 on 2008-03-31
woops, i installed the restricted formats.

---

### Post by Mick8882003 on 2008-03-31
sorry its late here
sudo apt-get install ubuntu-restricted-extras
i get cannot mount drive error

---

### Post by Speedwiz7770 on 2008-03-31
If you plan on using Totem (default player, I haven't personally tested), i've found this:
```
# sudo apt-get install libdvdread3 totem-xine libxine1-ffmpeg
# sudo /usr/share/doc/libdvdread3/install-css.sh
```
According to GeekyBits, after you restart your system, It should work fine in Totem.

I would personally recommend using VLC Player (google it); plays almost every multimedia format known to man, and it's relatively easy to use.

```
# sudo apt-get install libdvdread3 libxine1-ffmpeg vlc
# sudo /usr/share/doc/libdvdread3/install-css.sh
```

That should get the software end of it working. If it still says the same error, then it might be an internal error, like the drive itself is messed up. If thats the case, then it's a whole new set of problems.

Hope this helps
~Speedwiz7770~

---

### Post by Mick8882003 on 2008-03-31
still cannot get it to play, coming up as a cd player in the file manager.

---

