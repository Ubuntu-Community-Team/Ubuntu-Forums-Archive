---
title: "webcam getting even worse"
date: 2009-12-10
forum: Multimedia Software
---

### Post by libihero on 2009-12-10
my webcam worked perfectly in intrepid.  i downloaded jaunty and it didnt work with cheese and other programs at all, just skype.  now after an update it doesnt even work with skype :(
any help?

---

### Post by RedSingularity on 2009-12-12
Which webcam are you using?

---

### Post by libihero on 2009-12-12
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by RedSingularity on 2009-12-13
Look in synaptic and see if v4l1 is installed.  If not, install it and reboot.  Then try your webcam.

---

### Post by andresmh on 2009-12-13
My webcam was working on Jaunty for a couple of months but I think since the last kernel update it stopped working. Bummer. What a pain.

I have a Thinkpad x300 with a built-in webcam.

I tried gstreaming-properties, it does turn on the LED indicator but no image shows up. I also tried Cheese and Skype.

This is what I get in gstreamer-properties. It doesn't seem to get out of that.
[IMG]http://img138.imageshack.us/img138/1503/screenshot31.png[/IMG]

```

$ lsmod | grep uvcvideo
uvcvideo               59080  1 
videodev               36736  2 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev

```

---

### Post by andresmh on 2009-12-13
My webcam was working on Jaunty for a couple of months but I think since the last kernel update it stopped working. Bummer. What a pain.

I have a Thinkpad x300 with a built-in webcam.

I tried gstreaming-properties, it does turn on the LED indicator but no image shows up. I also tried Cheese and Skype.

This is what I get in gstreamer-properties. It doesn't seem to get out of that.
[IMG]http://img138.imageshack.us/img138/1503/screenshot31.png[/IMG]

```

$ lsmod | grep uvcvideo
uvcvideo               59080  1 
videodev               36736  2 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev

```

---

### Post by jmate24 on 2009-12-13
have you tried installing the full version of karmic? do a fresh install. Be sure to backup all of your data.

mine works, I use a lenovo ideapad y510.

jmate24--:D

---

### Post by libihero on 2009-12-13
my installation was a fresh one and i tried it twice
i do have libv4l :(

---

### Post by RedSingularity on 2009-12-13
Do you have gspca installed?

---

### Post by andresmh on 2009-12-13
I think the breakage was caused by the latest kernel.

---

### Post by RedSingularity on 2009-12-13
> **andresmh said:**
> I think the breakage was caused by the latest kernel.


That could be......i have had it happen before.

---

### Post by andresmh on 2009-12-13
I've opened a bug for it on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496266](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496266)

Please feel free to add your story there to gather more attention. Thanks!

---

### Post by libihero on 2009-12-13
i searched for gspca and it didnt even show up...

---

### Post by no2498 on 2010-02-26
andresmh
try settine the top part of that window to ( xwindow ( no xv) click the top test till you get a fuzzy pic
now play with the bottom test

---

