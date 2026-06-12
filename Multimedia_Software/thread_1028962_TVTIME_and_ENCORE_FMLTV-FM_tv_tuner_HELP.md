---
title: "TVTIME and ENCORE FMLTV-FM tv tuner HELP?"
date: 2009-01-02
forum: Multimedia Software
---

### Post by Mr Pockets151 on 2009-01-02
I had tvtime working sorta.  I was getting a picture on my card but no sound.  SO I googled and did some stuff and now when I run tvtime in a terminal I get this error ```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/mrpockets/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory

```

if I run xawtv i get this```
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-9-generic)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

```How can I check that my card is being loaded and that I have the correct files?

lspci gives me this.....```
04:06.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

``` Can I start from scratch?

---

### Post by wolfen69 on 2009-01-02
see if [this]("http://www.linuxtv.org/wiki/index.php/Saa713x_devices") helps.

---

