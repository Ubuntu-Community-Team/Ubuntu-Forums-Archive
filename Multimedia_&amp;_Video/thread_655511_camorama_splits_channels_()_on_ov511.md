---
title: "camorama splits channels (?) on ov511"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by xurizaemon on 2008-01-01
Hi

Using camorama (only), my ov511 camera splits the image into what looks like three separate images for each of the RGB channels.

(This was [discussed in a previous thread]("http://ubuntuforums.org/showthread.php?t=2271") and it looked like foolsh gave the answer in [a remote page]("http://home.insightbb.com/~foolsh/"), but his answer is now a 404.)
 * [http://ubuntuforums.org/showthread.php?t=2271](http://ubuntuforums.org/showthread.php?t=2271) (prev thread)
 * [http://home.insightbb.com/~foolsh/](http://home.insightbb.com/~foolsh/) (404)

Here's camorama:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=54933&stc=1&d=1199217471[/IMG]

Here's XawTV:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=54936&stc=1&d=1199217471[/IMG]

Here's gqcam:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=54935&stc=1&d=1199217471[/IMG]

dmesg says,
```

[162212.416333] usb 4-2: new full speed USB device using uhci_hcd and address 30
[162212.584153] usb 4-2: configuration #1 chosen from 1 choice
[162212.720720] Linux video capture interface: v2.00
[162212.725042] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/ov511/ov511.c: USB OV511 video device found
[162212.726894] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/ov511/ov511.c: model: D-Link DSB-C300
[162213.009632] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/ov511/ov511.c: Sensor is an OV7610
[162213.247520] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/ov511/ov511.c: Device at usb-0000:00:1d.3-2 registered to minor 0
[162213.247565] usbcore: registered new interface driver ov511
[162213.247570] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver

```

lsusb says,
```

Bus 004 Device 030: ID 05a9:0511 OmniVision Technologies, Inc. OV511 WebCam

```

---

### Post by Nixblicker on 2008-05-06
Hi,

same effect here on a Lenco APC400 with ov511 driver 0.19 on Hardy.

Any new clues or hints, anyone?

Cheers, Nix

---

### Post by Skymaker on 2008-05-13
Hi,

i have the same problem, so i searched archive.org for the site: [http://web.archive.org/web/20070702175646/home.insightbb.com/~foolsh/ov51x.htm](http://web.archive.org/web/20070702175646/home.insightbb.com/~foolsh/ov51x.htm)

But this did not solve my problem... the webcam works with xawtv, but not with camorama or amsn :(

---

