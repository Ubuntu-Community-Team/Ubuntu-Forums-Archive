---
title: "buttons are cross-hatched"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by moshuptrail on 2006-12-09
After installing Dapper on a laptop with a Radeon 320M I am seeing the large-size buttons appear to be cross-hatched (horz. & vertical marks over them).  When I move the mouse over the botton (no clicking) it clears up.

Here's the "screen section from my xorg.conf:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection
```

Any ideas?

---

### Post by Anthem on 2006-12-10
This is a known bug with the UbuntuLooks theme and the 320m video card.  I believe it has been fixed in Edgy Eft.

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/34435](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/34435)

---

### Post by moshuptrail on 2006-12-10
Thanks for that info.  I don't want to upgrade to edgy quite yet, but I can live with it.  It's a little bit of comfort (very little) knowing it's not some config value I need to change.

---

### Post by Anthem on 2006-12-11
> **moshuptrail said:**
> Thanks for that info.  I don't want to upgrade to edgy quite yet, but I can live with it.  It's a little bit of comfort (very little) knowing it's not some config value I need to change.
If you check Launchpad, I believe the fix has been included in Dapper Backports.  So it would be available to you right now.  Don't know what the package name is, though.

---

