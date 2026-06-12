---
title: "Logitech C270 Webcam no sound"
date: 2011-02-10
forum: Multimedia Software
---

### Post by phorgan1 on 2011-02-10
I'm on Linux dell 2.6.35-26-generic #46-Ubuntu SMP Sun Jan 30 08:10:51 UTC 2011 i686 GNU/Linux

My new web cam from logitech works fine on video, but nothing on sound.

I've read several posts with the same problem, but their solutions don't work for me.  I plug in the camera, and the microphone is not recognized:

```
[  611.264188] usb 2-4: new high speed USB device using ehci_hcd and address 6
[  611.613398] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0825)
[  611.710392] input: UVC Camera (046d:0825) as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input15

```

Someone suggested going to preferences/sound and enabling '0825 Analog Mono'.  Of course it's not there.  Someone else suggested adding audio to /etc/hotplug/blacklist.  That didn't change anything.

Anyone have an idea?  HELP!

---

### Post by phorgan1 on 2011-02-15
All I had to do is sudo modprobe snd_usb_audio and the right device appeared.  After that I had to unmute it and select it for the software I was using, yay!

---

### Post by sashko_s on 2012-10-02
[https://help.ubuntu.com/community/Webcam#See%20also](https://help.ubuntu.com/community/Webcam#See%20also)

---

### Post by sandyd on 2012-10-02
**Necromancy - thread closed**

As per the [Ubuntu Forums code of conduct]("http://ubuntuforums.org/index.php?page=policy"), please do not post in threads more than one year old

Thanks!

---

