---
title: "Not having any joy with sound"
date: 2008-08-07
forum: Multimedia Software
---

### Post by DJAVAH on 2008-08-07
Hi all -

First time Ubuntu user here (8.04 64 bit) - please be gentle :)

I'm not having any luck with sound on my work laptop, an Acer Ferrari 5000 series.

When I initially installed Hardy Heron, I had sound working but only through headphones, not the internal speakers. I found a page online that suggested uninstalling ALSA and installing OSS instead, which had the unfortunate side effect of removing the gdm package! :mad:

I've got Gnome back up and running but with no sound, although I have removed the OSS packages and reinstalled ALSA. On my Gnome desktop, by the volume control I get the message:

No volume control GStreamer plugins and/devices found.

I've googled this and tried plenty of the suggestions, but nothing works. Alsamixer doesn't run, I do have the GStreamerPlugin installed as far as I can see and I've even tried updating the ALSA drivers.

I'd really appreciate any help people can offer as I'm close to admitting defeat and reinstalling 8.04, but I'd like to learn from this experience if I can.

Thanks.

---

### Post by xchip on 2008-12-23
I have 8.10 on a Ferrari 5000 and the sound is still not working... 

Did anyone manage to get it working?
Thanks!

---

### Post by linux_tech on 2008-12-23
Gnome-alsamixer is easier to use than alsamixer. Try installing and running it it first
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type

```
gnome-alsamixer

```
check all settings, make sure nothing is muted

To open volume control type:
```
gnome-volume-control

```

---

### Post by xchip on 2008-12-23
awesome!!! it works!! thank you!

---

