---
title: "The impossible HDMI sound problem..."
date: 2009-01-06
forum: Multimedia Software
---

### Post by xJoo Unitx on 2009-01-06
I've done some research on this topic... and I've failed.  I updated the Alsa sound drivers and installed the Nvidia 180.17 graphics driver. Video is fine on my samsung tv, perfect 1080p resolution on my HDMI cable, but still no sound

aplay -l still shows now HDMI output

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

any ideas? I'm pretty new to linux in general, and upgrading the two drivers is really as far as I've gotten

---

### Post by xJoo Unitx on 2009-01-06
Any ideas?

---

### Post by 2hot6ft2 on 2009-01-06
There are others trying to figure that out as well and here's the thread so you can see what progress has been made. Since you only gave some of your pc's specs like nvidia I think you're in the same boat.
[http://ubuntuforums.org/showthread.php?t=957581](http://ubuntuforums.org/showthread.php?t=957581)

---

### Post by damis648 on 2009-01-06
Open the volume control preferences and enable all channels on all devices. Somewhere in there exists the HDMI output. (This was how I found mine)

---

