---
title: "GeForce 7300 GT and DVI"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by gerscht on 2006-07-24
Hi there,
I'm trying to get the DVI connection on my GeForce 7300 GT to work... just plugin it in doesn't do the trick :???: 
I've got the newest bin drivers installed, everything is working just fine (direct rendering etc.)
Is there anything I have to chnage in xorg.conf?

Thanks in advance!

---

### Post by tseliot on 2006-07-24
Try this;

```
sudo nano -w /etc/X11/xorg.conf
```

Add this option to the Section Device:
```
Option         "ConnectedMonitor" "DFP"
```

CTRL+X to exit (save the file)

Turn off your computer.

Connect the monitor to the DVI cable.


Turn on your computer.

---

### Post by gerscht on 2006-07-24
Works perfect :D , Thanks!

---

### Post by neurostu on 2008-06-16
Will that fix allow you to connect a monitor to the DVI and a seperate to the VGA?

---

