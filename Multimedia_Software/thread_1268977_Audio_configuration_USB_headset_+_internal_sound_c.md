---
title: "Audio configuration: USB headset + internal sound card"
date: 2009-09-17
forum: Multimedia Software
---

### Post by Berduchwal on 2009-09-17
Hi
I recently purchased USB headset:
lsusb
```

Bus 003 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter

```

Up to now I have used my internal sound card:
lspci
```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

```

I have ALSA as my current sound system.

What I want to achieve is to have my internal sound card operating as default but to switch over to the USB one when pluged in.

I have tried to find solution on ALSA web page: [http://alsa.opensrc.org/index.php/MultipleCards]("http://alsa.opensrc.org/index.php/MultipleCards")
but in my view it is not up to date and I can not get it to work.

I have also tried to configure pulse audio but I can not get USB headset to get any sound.

I can set Amarok to use it and it works fine. On other application it does not.

I am stuck I do not know what to do next. Can someone please point me into direction?

---

### Post by markbuntu on 2009-09-17
Try this

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

I have two sound cards, a usb headset and a mic on my webcam. They all work and I can switch them around with a few clicks.

---

