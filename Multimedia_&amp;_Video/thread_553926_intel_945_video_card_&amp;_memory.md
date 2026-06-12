---
title: "intel 945 video card &amp; memory"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by raiwo on 2007-09-18
i have a laptop(toshiba satellite-A200)with intel 945 video card wich uses shared memory. When itry to watch a video with VLC i get an error message:```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  86
  Current serial number in output stream:  87

```

is there easy tool to check how much memory is in use of video card and how to add it?

i found this following advice:
> A remedy for such issues is adding in /etc/X11/xorg.conf something like the following to your video device section:
```
Option "VideoRam" "65536"
Option "CacheLines" "1980"
```
his will instruct your onboard video using 64M of shared RAM, so it will be adequate for running some "demanding" X apps.
Of course if your onboard video can use more than 64M, adjust the "65536" value accordingly.

source: [http://mandrivausers.org/index.php?showtopic=40523&pid=310291&mode=threaded&start=](http://mandrivausers.org/index.php?showtopic=40523&pid=310291&mode=threaded&start=)

unfortunetanely this advice kills my wireless for some reason, perhaps i am not adding it in right place?

so is there an easy tool to check & modify these settings?

---

### Post by raiwo on 2007-09-18
i just noticed this problem exists only if i have desktop effects on, turning them off & everyting works fine.

---

### Post by RomeReactor on 2007-09-18
Hi. Maybe [this]("http://ubuntuforums.org/showthread.php?p=3346241#post3346241") can be of help.

---

