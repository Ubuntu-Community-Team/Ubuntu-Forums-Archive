---
title: "Installing Broadcom Crystal HD drivers - how?"
date: 2014-09-13
forum: Multimedia Software
---

### Post by zhangweiwu on 2014-09-13
I've tried to get crystal hd working on my netbook for four (4) years with no luck - this post is my latest renewed effort on 14.04. I've pretty much given up, and just watch non hi-def videos on it. But if someone can chime in with some answers, I'm all ears.
```

# lspci | grep -i crystal
02:00.0 Multimedia controller: Broadcom Corporation BCM70015 Video Decoder [Crystal HD]

# apt-cache search crystalhd
firmware-crystalhd - Crystal HD Video Decoder (firmware)
gstreamer1.0-crystalhd - Crystal HD Video Decoder (GStreamer plugin)
libcrystalhd-dev - Crystal HD Video Decoder (development files)
libcrystalhd3 - Crystal HD Video Decoder (shared library)

```
I installed firmware-crystalhd first, then:
```

# modprobe crystalhd
# lsmod | grep crystal
crystalhd              54883  0 

# tail /var/log/syslog
Sep 13 11:00:26 lyonesse kernel: [ 5653.447449] crystalhd: module is from the staging directory, the quality is unknown, you have been warned.
Sep 13 11:00:26 lyonesse kernel: [ 5653.448795] Loading crystalhd 0.9.27

```
Okay, what to do next? According to this post [http://multimedia.cx/eggs/installing-crystalhd-drivers-in-linux/](http://multimedia.cx/eggs/installing-crystalhd-drivers-in-linux/) I should see /dev/crystalhd
```

# LANG=en ls /dev/crystalhd
ls: cannot access /dev/crystalhd: No such file or directory

```
I installed gstreamer1.0-crystalhd but it unsurprisingly doesn't work. Some say&#8224; there is a log message if it works - without even referring to the fact that I don't have that log message, I know it doesn't work because Totem can't decode 720p smoothly (H.264 in MKV file)

Searched everywhere no mentioning of instructio on how to use Crystal HD on any of the Linux flavours, not even ArchLinux instructions. Someone discussed about CrystalHD on OPENSUSE on Feb 2014 (this year) in Russian:
[http://www.linux.org.ru/forum/linux-hardware/10208997](http://www.linux.org.ru/forum/linux-hardware/10208997)

--
&#8224;
[quote=http://ubuntuforums.org/showthread.php?t=1931291#post_message_11750868]

According to this (German) page [http://geekparadise.de/2011/04/cryst...u-kompilieren/](http://geekparadise.de/2011/04/cryst...u-kompilieren/)
tail -f /var/log/syslog should spit out the line "crystalhd 0000:02:00.0: Opening new user[0] handle" as soon as a video is decoded by the Crystal HD hardware. There is also an indicator applet [http://code.google.com/p/indicator-crystalhd/](http://code.google.com/p/indicator-crystalhd/)
[/quote]

---

### Post by kostkon on 2014-09-13
Sorry to ask that, but did you reboot after installing the firmware?

---

