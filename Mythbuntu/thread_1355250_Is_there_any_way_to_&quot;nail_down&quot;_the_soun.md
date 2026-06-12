---
title: "Is there any way to &quot;nail down&quot; the sound card?"
date: 2009-12-14
forum: Mythbuntu
---

### Post by NightStorm on 2009-12-14
This weekend I lost all sound from MythTV (on a fresh install of Mythbuntu 9.10) after I plugged in a Logitech Orbit webcam.  Unplug it and the sound works again.  It looks like the microphone in the webcam causes the system to setup the webcam as sound device 0 and move the motherboard's built in sound card up a notch.

Plugging things like USB devices in and having it break makes the whole thing kind of fragile.  I was wondering if there was any way to prevent this (other than "Don't do that")?

TIA,

       - Bruce

---

### Post by nickrout on 2009-12-14
so does this happen when you plug the camera in AFTER bootup, or just when its plugged in when you boot up?

Usually plugging something else will not change the device nodes of something that is already loaded, but if there are two devices plugged in at boot, it can be a lttery to decide which one gets which device.

Try looking at a udev rule to sort it. googling dev rules will find lots of info.

---

### Post by NightStorm on 2009-12-14
> **nickrout said:**
> so does this happen when you plug the camera in AFTER bootup, or just when its plugged in when you boot up?

Usually plugging something else will not change the device nodes of something that is already loaded, but if there are two devices plugged in at boot, it can be a lttery to decide which one gets which device.

Try looking at a udev rule to sort it. googling dev rules will find lots of info.

It happens if the box is booted after the device is plugged in.
I was just reading in another thread where tdcarlo point out [this]("http://ubuntuforums.org/showthread.php?t=753434") link, which I think is what you are saying.

Thanks!

---

### Post by nickrout on 2009-12-14
> **NightStorm said:**
> It happens if the box is booted after the device is plugged in.
I was just reading in another thread where tdcarlo point out [this]("http://ubuntuforums.org/showthread.php?t=753434") link, which I think is what you are saying.

Thanks!

Actually even simpler I think. Work out what modules are being loaded for each device. Then in /etc/modprobe.d/alsa-base add or edit some options lines at the bottom, eg:

```
options snd-ymfpci index=0
options snd-hda-intel index=1,2
```

In this case the snd-ymfpci device will always be the first alsa device, and snd-hda-intel will come after it.

The following link, although for gentoo, has some good documentation:

[http://www.gentoo.org/doc/en/alsa-guide.xml](http://www.gentoo.org/doc/en/alsa-guide.xml)

---

