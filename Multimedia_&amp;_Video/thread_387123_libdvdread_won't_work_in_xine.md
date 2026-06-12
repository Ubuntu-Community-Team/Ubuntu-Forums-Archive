---
title: "libdvdread won't work in xine"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by ebike on 2007-03-17
Hi All,

I just finished a re-installation of mythtv to my brand new Ubuntu box from initially a gentoo box.

Mostly everything is working except DVD playback and a mono issue.

The problem is I get this error from libdvdread while trying to play a DVD.

> libdvdread: Could not open input: Permission denied
libdvdread: Can't open /dev/hda1 for reading
libdvdread: Device /dev/hda1 inaccessible, CSS authentication not available.
libdvdnavVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnavVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Encrypted DVD support unavailable.
2007-03-18 10:06:41.342 Connecting to backend server: 192.168.0.3:6543 (try 1 of 5)
2007-03-18 10:06:41.437 Using protocol version 31

I do not know why it is trying to access my hard-disk /dev/hda1 instead of my cdrom on /dev/cdrom ?? I cannot see any config options to tell libdvdread where to look.

Can anyone help with this. I will open another thread on the mono issue.

Thanks.

---

### Post by solar george on 2007-03-18
You'll need to install libdvdcss, you can use automatrix to do that easily.
[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by yabbadabbadont on 2007-03-18
Or you can install it using a script that is installed when you install libdvdread3  (which you may already have installed).  If you are using Edgy, it is /usr/share/doc/libdvdread3/install-css.sh  If you are using Dapper it is /usr/share/doc/libdvdread3/example/install-css.sh  The script will download and install libdvdcss2 for you.  You have to use sudo to run the script.

---

### Post by ebike on 2007-03-18
Thanks that did the trick...

Cheers:)

---

### Post by Chemroydal Tissue on 2007-06-07
I'm having the same problem, and running the script (and changing the settings in Xine) did not work. Any other suggestions?

BTW, the script in Feisty is:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

EDIT #2: A reboot seems to have resolved the error. Why that worked, when the log said it was pointing to libdvdcss all along, I don't know. Anyway, it's the first time I've had to reboot, except when updating the kernel. Kind of disappointing.

---

