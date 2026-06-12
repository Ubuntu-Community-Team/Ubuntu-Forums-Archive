---
title: "Problem with USB audio device and JACK"
date: 2012-09-22
forum: Multimedia Software
---

### Post by fx1040 on 2012-09-22
Hello everyone,

I recently discovered a strange problem with connecting an USB audio device (Alesis MultiMix 4, using the TC PCM 2900 Audio codec) to the JACK audio server on a newly installed Ubuntu Studio 12.04.1.

If I tried to start JACK with the device hw1,0 (USB Audio) JACK refused to start and gave error messages like:
```
Audio device hw:1,0 cannot be acquired
```Choosing the same device using ALSA in Audacity worked without any problems, however. (Rather strange, because as far as I know Jack uses ALSA as well). 

Starting JACK as root worked pretty well too, without complaints and input/output connections to the USB device. So I checked the permissions of /dev/hidraw0 (which was created everytime I plugged in the USB device). I changed them with
```
sudo chmod 777 /dev/hidraw0
``` and voila: I could start JACK even as an normal user.

To solve the issue permanently, I wanted to create a UDEV-Rule for the permissions of /dev/hidraw0. But after rebooting my Workstation and un- and in plugging the USB device JACK started as if he never did otherwise. The file permissions of  /dev/hidraw0 rather restricted again, but nonetheless no UDEV rule needed here. I cannot explain the phenomenon, maybe JACK needed more rights to initialize the device one time.

So if you run in a similiar problem, try the chmod statement above, maybe it helps you too.

:guitar:

Good luck!
fx1040

---

