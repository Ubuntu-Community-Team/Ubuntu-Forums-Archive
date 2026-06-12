---
title: "mp4live can't select video standart"
date: 2010-05-22
forum: Multimedia Software
---

### Post by triastanto on 2010-05-22
Hello there, this my first post, :)

I'm having trouble using mp4live (mpeg4ip-server 1.6 & Darwin Streaming Server 6.0.3 is up and running) on Ubuntu 9.10.
I have two webcam as listed on Cheese preferences:
```
PROLiNK PCC3220 (/dev/video0)
UVC Camera(046d:08c5) (/dev/video1)
```'Transmit' option are checked and saved as default.sdp in /usr/local/movies.
After I pressed the 'Start' button I can't see any stream on rtsp://localhost/default.sdp on VLC media player but samples_*.mp4.

```
dani@dani-ubuntu:~$ mp4live
01:23:54.879-mp4live-3: mp4live version 1.6 V4L2

(mp4live:31645): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
01:23:54.998-mp4live-3: audio profile checking default:g711
01:24:00.413-mp4live-3: Failed to select video standard for /dev/video0 - Invalid argument
01:24:00.417-rtp-6: Created database entry for ssrc 0x75612c5d (1 valid sources)
01:24:00.417-rtp-6: Created database entry for ssrc 0x5be0af46 (1 valid sources)
01:24:00.419-mp4live-3: Control "hue" not supported
01:24:01.163-mp4live-3: send_iov error - returned -1 1460
01:24:01.163-mp4live-3: send_iov error - returned -1 1460
01:24:01.163-mp4live-3: send_iov error - returned -1 38
01:24:01.287-mp4live-3: send_iov error - returned -1 392
01:24:01.413-mp4live-3: send_iov error - returned -1 1460
01:24:01.413-mp4live-3: send_iov error - returned -1 1460
01:24:01.413-mp4live-3: send_iov error - returned -1 1460
01:24:01.413-mp4live-3: send_iov error - returned -1 1460
01:24:01.413-mp4live-3: send_iov error - returned -1 748
01:24:01.533-mp4live-3: send_iov error - returned -1 1341
01:24:01.658-mp4live-3: send_iov error - returned -1 1460
01:24:01.658-mp4live-3: send_iov error - returned -1 331
01:24:01.781-mp4live-3: send_iov error - returned -1 1340
01:24:01.911-mp4live-3: send_iov error - returned -1 1460
01:24:01.911-mp4live-3: send_iov error - returned -1 1246
01:24:02.029-mp4live-3: send_iov error - returned -1 654
01:24:02.149-mp4live-3: send_iov error - returned -1 1460
01:24:02.150-mp4live-3: send_iov error - returned -1 694
01:24:02.273-mp4live-3: send_iov error - returned -1 1460
01:24:02.273-mp4live-3: send_iov error - returned -1 240
01:24:02.398-mp4live-3: send_iov error - returned -1 1460
01:24:02.398-mp4live-3: send_iov error - returned -1 1435
01:24:02.521-mp4live-3: send_iov error - returned -1 1452
01:24:02.646-mp4live-3: send_iov error - returned -1 1460
01:24:02.646-mp4live-3: send_iov error - returned -1 1460
01:24:02.646-mp4live-3: send_iov error - returned -1 146
01:24:02.769-mp4live-3: send_iov error - returned -1 1460
01:24:02.769-mp4live-3: send_iov error - returned -1 442
01:24:02.890-mp4live-3: send_iov error - returned -1 1460
01:24:02.890-mp4live-3: send_iov error - returned -1 1460
01:24:02.890-mp4live-3: send_iov error - returned -1 147
01:24:03.013-mp4live-3: send_iov error - returned -1 1460
01:24:03.013-mp4live-3: send_iov error - returned -1 244
01:24:03.019-rtp-6: Dropped membership of multicast group
01:24:03.019-rtp-6: Dropped membership of multicast group
01:24:03.019-rtp-6: Dropped membership of multicast group
01:24:03.020-rtp-6: Dropped membership of multicast group

```Is something wrong with this:
```
01:24:00.413-mp4live-3: Failed to select video standard for /dev/video0 -  Invalid argument
```Thank you.

---

### Post by no2498 on 2010-05-22
i do not know if this will help but
i can not use 2 cams at 1 time
or have both plugged in at the same time
i need to unplug 1 of them

---

### Post by triastanto on 2010-05-23
Tried that but the error remains the same :(

Not only when I pressed 'Start' button but also when checked the 'Preview Video Source' options, it showed,

```
12:07:26.752-mp4live-3: Failed to select video standard for /dev/video0 - Invalid argument

```

---

