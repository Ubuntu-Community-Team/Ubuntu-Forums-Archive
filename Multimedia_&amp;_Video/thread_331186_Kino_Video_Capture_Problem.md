---
title: "Kino Video Capture Problem"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by se2schul on 2007-01-04
When I try to capture video using Kino, it will only capture the first 4 or 5 seconds of video before stopping the capture.  Any ideas about what could be wrong?

Thanks.

---

### Post by Yfrwlf on 2007-01-18
> **se2schul said:**
> When I try to capture video using Kino, it will only capture the first 4 or 5 seconds of video before stopping the capture.  Any ideas about what could be wrong?

Thanks.

You can capture video?  Luckyyyyyyyyy! =P

I'd try changing codecs, screw around with options, make sure you have enough space...stuff like that. =P  If I could get mine working then I could perhaps give more info. ^^

---

### Post by olafbooij on 2007-05-16
Hi se2schul (if you're still listening...),

Just reporting I had the same symptoms with kino... but after some rebooting, changing firewire device (I've got a firewire-pci card with two ports and a soundcard with one port) , it started working all of a sudden.

One thing that is worth trying is using dvgrab to capture video.
Try running the following command in a shell:
```
dvgrab --format raw test.dv 
```

Also, try changing the device kino uses: go to edit->preferences->IEEE1394 and change the dv1394 device to /dev/dv1394/0 or /dev/dv1394/1 .

Olaf

---

### Post by Yfrwlf on 2007-05-16
Update: Try VLC for capturing video, worked great for me. ^^

---

