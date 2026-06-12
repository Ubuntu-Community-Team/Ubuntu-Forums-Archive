---
title: "Hauppauge WinTV card not working"
date: 2005-11-30
forum: Multimedia &amp; Video
---

### Post by nwlinkvxd on 2005-11-30
I'm running Breezy with the 12-9-686 stock kernel. I'm trying to set up this machine as a PVR on MythTV

My tv card is a Hauppauge WinTV NTSC, model 61381 Rev. D123

Running bttv by itself gives this:
FATAL: Error inserting bttv (/lib/modules/2.6.12-9-686/kernel/drivers/media/video/bttv.ko): Operation not permitted


Output from dmesg regarding bttv:
[4294698.290000] bttv: disagrees about version of symbol tveeprom_hauppauge_analog
[4294698.290000] bttv: Unknown symbol tveeprom_hauppauge_analog


Trying to run xawtv:
This is xawtv-3.94, running on Linux/i686 (2.6.12-9-686)
WARNING: No DGA support available for this display.
can't open /dev/video0: No such device
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device
v4l2: open /dev/video0: No such device
v4l: open /dev/video0: No such device
no video grabber device available


Trying to run zapping:
trying device: /dev/video
trying device: /dev/video0
trying device: /dev/v4l/video0
trying device: /dev/v4l/video
trying device: /dev/video1
trying device: /dev/video2
trying device: /dev/video3
trying device: /dev/v4l/video1
trying device: /dev/v4l/video2
trying device: /dev/v4l/video3


lspci shows:
0000:02:03.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
0000:02:03.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)


I'll post more as soon as anything's suggested to me. I've been Googling on this for a few days and have searched endlessly on these forums but I can't find anything that applies to my situation.

Help!

---

### Post by nwlinkvxd on 2005-12-01
I just wanted to say that I resolved my own issue by reading the end of this page:
[http://ivtvdriver.org/index.php/Troubleshooting](http://ivtvdriver.org/index.php/Troubleshooting)

And then realizing that something was wrong with the kernel I had installed. I rolled back to 12-9-386 and voila, the tv tuner works fine.

---

### Post by dbeckham32 on 2005-12-02
I have the Hauppauge WinTV 250 card in my PC under Breezy and it works great. However, installing the driver was tricky.

I'm using the IVTV driver, not the one you mentioned so the instructions here may not be 100% applicable. Nonetheless, it might be worth a shot.

I found these 3 websites to be extremely helpful in getting my WinTV card up and running.

[http://www.abarbaccia.com/](http://www.abarbaccia.com/)

[http://www.cs.rit.edu/~css8044/?q=ivtv](http://www.cs.rit.edu/~css8044/?q=ivtv)

[http://www.slash32.com/ubuntu-myth.html](http://www.slash32.com/ubuntu-myth.html)

---

