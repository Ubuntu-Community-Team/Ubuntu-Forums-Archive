---
title: "Video4Linux and USB Video adapter."
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by TheCelloFellow on 2007-01-05
I have an iREZ USB Live! CapSure video cable. It has RCA-Component and S-Video at one end, and USB plug at the other. I want to use it in conjunction with VLC's Video4Linux features to capture VHS tapes for remastering and editing.

lsusb shows this:
```

Bus 001 Device 004: ID 0573:2000 Zoran Co. Personal Media Division (Nogatech) X10 va10a Wireless Camera
```

How do I set up v4l to use this? Currently the only device file associated with it is /dev/bus/usb/001/004. v4l would much rather use /dev/video, only that file doesn't exist.

Maybe I'm barking up the wrong tree with v4l and VLC. If I am, another solution would be much appreciated.

-CelloFellow

---

### Post by TheCelloFellow on 2007-01-09
Ok, maybe if I speak in player language I can get an answer.

When I lsusb my iREZ USB Live! video cable, I get this:

Bus 001 Device 004: ID 0573:2000 Zoran Co. Personal Media Division (Nogatech) X10 va10a Wireless Camera

How do I set this up so that I can save videos played into the cable? Can I use Video4Linux and VLC?

-CelloFellow

---

### Post by mulvila on 2007-06-06
I am looking for such device that would work in Linux: I assume it is a driver issue. Would like to know if you find a solution.

---

### Post by vraetorian on 2008-03-12
try using /dev/video0 in VLC

It worked for this guy's webcam USB...



His name is david something.. second last post on the page.
[http://ubuntuforums.org/showthread.php?t=495243](http://ubuntuforums.org/showthread.php?t=495243)

---

