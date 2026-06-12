---
title: "Problem with Canon Ixus 700"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by isterios on 2006-01-09
When I plug my Canon Ixus 700, the following popup appears:
"Import photos form camera?"

and when I click on "Import photos":
"camera not ready. Multiple 'identify camera' requests failed: OS error in camera communication."

I restarted the cam, Ubuntu, idem.

I tried to use gtkam:
the canon is detected and:
"Step #4 failed! (returned 0, expected 64) Camera not operationel."

A lsusb shows:
Bus 003 Device 008: ID 04a9:30f2 Canon, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Can you help me?

Thks.

---

### Post by ProMaster on 2006-01-19
Hi Isterios,

I just bought a Canon IXUS 700 last weekend and stumbled onto the same problem. I did some investigation and found out that the Opensuse distribution does work with the camera. Further investigation showed that the main problem lays with the LIBGPHOTO2_2 driver. The one on Ubuntu is 2.1.6 and the one on Opensuse is 2.1.99. 

I haven't found a good DEP file for this driver, but I did find an RPM. With ALIEN I made it into a DEP and installed it. Unfortunately I got all kinds of dependency problems with other programs. I am sure that this is the way to go though.

So, I guess we'll have to wait for the LIBGPHOTO driver to be updated in one of the APT repositories, or compile the drive ourselfs.

---

### Post by Simian on 2006-02-03
I have a Ixus 700 and want to use it with Ubuntu too. I don't suppose either of you have figured out a way yet. If or when you do can you plaese post a howto on this forum. Thanks in advance :)

---

### Post by meastp on 2006-02-24
Same issue! Would love to hear from you when you figure it out...

---

### Post by isterios on 2006-03-09
Ok so you need to install GTKAM (sudo apt-get install gtkam)

1. So when you plug your Ixus, the default Ubuntu application is launched. **DO not use it, just close it directly**.

2. Launch GTKAM, and evrything should work.

(in fact it seems there is a conflict between the drivers use by gtkam and the driver used by the default ubuntu application. The default application locked the device).

---

### Post by Simian on 2006-03-10
Thanks for getting back to us. I'll give that a try :)

---

### Post by ProMaster on 2006-05-09
Eureka!!! Yesterday evening I got it to work. And the solutions is quite easy. I threw away the libcanon* file from gphoto directory and.... it worked. It seams the libcanon* file has a bug and interferes with the USB drivers. As you don't need the libcanon* driver you can chuck it away. (my advise, move it instead of deleting. Just in case).

---

