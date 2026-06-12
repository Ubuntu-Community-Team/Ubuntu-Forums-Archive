---
title: "Logitech Z-10 usb Speakers"
date: 2008-06-08
forum: Multimedia Software
---

### Post by bturcotte on 2008-06-08
Just installed Ubuntu 8.0.4 and noticed my Logitech Z-10 usb speakers didn't work, as alsa by default does not allow snd-usb-audio to occupy slot 0.  Very quick fix.

```
sudo gedit /etc/modprobe.d/alsa-base 
```

Scroll down through the code and comment out:

```
 #options snd-usb-audio index=-2 
```

Save and exit.

System -> Preferences -> Sound

Set all drop-downs to "ALSA -.."
Set "Default Mixer Tracks" to "Z-10 USB Speaker"

Restart.

---

