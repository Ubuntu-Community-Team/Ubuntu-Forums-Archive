---
title: "Ati TV-Out Video Problem MythTV"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by RJ17 on 2007-02-07
I am trying to use my S-Video to watch mythtv on 6.10 with at Radeon 9800 XT.  Currently the TV out works and clones the display on my tv.  Everything displays  fine on the TV except video.  The video will only display on my LCD and where the video is on my TV it is blank.  This is also true for VLC.  

Any help would be appreciated.  If you need any other info to help let me know and I will post it.

---

### Post by NiksaVel on 2007-02-16
I don't use mythtv but have EXACTLY the same problem...  anyone?  I am pretty sure I found a post about this somewhere when I wasn't looking for that, but I can't find anything helpful now...

someone pls help

---

### Post by superm1 on 2007-02-16
This is due to the way video overlays work.

The aticonfig utility that comes with the ATI drivers allows you to set the overlays.

```
aticonfig --help
.
.
  --ovon, --overlay-on={0|1}
        Choose which head the hardware overlay should be visible on.  The
        hardware overlay can be used for either OpenGL, video, pseudo-color
        or stereo.
.
.

```

So to set the overlay to the secondary display:
```
aticonfig --ovon=1
```

If you run this as root, it will write the change to your xorg.conf and make it permanent every time that X starts
```
sudo aticonfig --ovon=1
```

---

