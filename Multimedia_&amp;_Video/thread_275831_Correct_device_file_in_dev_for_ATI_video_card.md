---
title: "Correct device file in /dev for ATI video card"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by crokett on 2006-10-11
Trying to find out what device file(s) are used in /dev for my ATI Radeon AIW.  xawtv will show what is playing on my camcorder or vcr I have hooked up so I know it is working..  I am trying to get cinelerra to use the correct device.  xawtv is supposed to default to /dev/video0 but that does not exist on my system.  Can't find a conf file anywhere for xawtv and the man page isn't much help.

---

### Post by lokalhost on 2006-10-12
Heading to bed, hopefully these snippets put in in the right direction

```

cat /etc/modprobe.d/aliases | grep video
alias char-major-81-* videodev
alias char-major-171-1 video1394

```

```

ls -lath /dev | grep 81,
crw-------   1 user root    81,   0 Oct  4 08:32 video0
crw-------   1 user root    81,  64 Oct  4 08:32 radio0
crw-------   1 user root    81,  24 Oct  4 08:32 video24
crw-------   1 user root    81, 224 Oct  4 08:32 vbi0
crw-------   1 user root    81,  32 Oct  4 08:32 video32
crw-------   1 user root    81,  32 Oct  4 08:32 video4linux

```

---

### Post by crokett on 2006-10-12
Here is the output I have


```

sudo cat /etc/modprobe.d/aliases | grep video

alias char-major-81-* videodev
alias char-major-171-1 video1394

ls -lath /dev/| grep 81

crw-rw-rw-  1 root tty       3,  81 2006-10-11 19:02 ttyu1
crw-rw-rw-  1 root tty       3, 181 2006-10-11 19:02 ttya5
crw-rw----  1 root dialout   4,  81 2006-10-11 19:02 ttyS17
crw-rw-rw-  1 root tty       2,  81 2006-10-11 19:02 ptyu1
crw-rw-rw-  1 root tty       2, 181 2006-10-11 19:02 ptya5
```

As far as I know, tty is a serial port? Not sure what the others are,

---

### Post by crokett on 2006-10-12
Not sure if this helps but xawtv includes an option to display HW thusly:```
crokett@Hawking:~$ xawtv -hwscan
This is xawtv-3.94, running on Linux/i686 (2.6.15-27-386)
looking for available devices
port 73-73                              [ -xvport 73 ]
    type : Xvideo, video overlay
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

```

I am not sure what this means.

---

### Post by lokalhost on 2006-10-12
Try this:

mknod /dev/video0 c 81 0
chmod 0666 /dev/video0
ln -s /dev/video0 /dev/video

---

### Post by crokett on 2006-10-12
> **lokalhost said:**
> Try this:

mknod /dev/video0 c 81 0
chmod 0666 /dev/video0
ln -s /dev/video0 /dev/video

I will try that but discovered why I can't record with xawtv - (actually found this in man pages for another program that uses xawtv)

```
 Xvideo X11 Extention for video  devices.	  Note	that  the
	      Xvideo  extention	 does  support	overlay only, you
	      can't capture images/movies if the Xvideo extention
	      is used.	On the other hand this is the only way to
	      scaled video overlay (i.e. fullscreen without black
	      borders  @  1024x748)  if both hardware and xfree86
	      driver support  it.   See	 README.xfree4	for  more
	      details and hints on how to setup Xvideo.
```

So looks like I have another proglem to fix too...

---

### Post by crokett on 2006-10-12
It did not work.  Here is the output I get from xawtv:  ```

This is xawtv-3.94, running on Linux/i686 (2.6.15-27-386)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

```

The video 4 linux conf util gives similar message.  It appears everything I need is installed except /dev/vdieo0 isn't created.  Any ideas?  I really don;t want to have to reinstall windows just to be able to capture video.

---

