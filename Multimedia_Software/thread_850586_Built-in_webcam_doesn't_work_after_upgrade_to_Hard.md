---
title: "Built-in webcam doesn't work after upgrade to Hardy"
date: 2008-07-05
forum: Multimedia Software
---

### Post by Narf on 2008-07-05
I have an Acer Aspire 5100-5023 notebook and I recently upgraded to Hardy.

I've had some problems with Gutsy when I first installed it, but my webcam was working flawlessly. The upgrade to Hardy went smoothly and everything works fine, except for some network lag while using wireless and my webcam not working.

Some related details:

> narf@laptop:~$ sudo modprobe gspca
narf@laptop:~$ dmesg | tail -n39
[41499.111390] usbcore: registered new interface driver hci_usb
[41582.097072] usbcore: deregistering interface driver gspca
[41582.097316] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: driver gspca deregistered
[41583.007608] usbcore: registered new interface driver gspca
[41583.007858] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[41587.796449] uvcvideo: Failed to query (135) UVC control 2 (unit 5) : -110 (exp. 2).
[41588.742031] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[41605.429165] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[41605.880550] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[41606.686503] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[41607.490638] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[41607.943782] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[41608.393388] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[41609.164206] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[41609.650818] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[41641.151244] usb 1-1: USB disconnect, address 3
[54760.964015] uvcvideo: Failed to query (135) UVC control 2 (unit 5) : -110 (exp. 2).
[54762.055881] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[54829.922313] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[54832.735595] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[54839.295806] uvcvideo: Failed to query (135) UVC control 2 (unit 5) : -110 (exp. 2).
[54848.962542] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[54851.683904] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[54864.756681] gstreamer-prope[4209]: segfault at 9 rip 7f298a41fdb7 rsp 7fff970589e8 error 4
[54868.608047] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[54921.331224] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[54951.585592] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[54951.725988] uvcvideo: Failed to query (135) UVC control 2 (unit 5) : -110 (exp. 2).
[54951.866354] uvcvideo: Failed to query (135) UVC control 6 (unit 5) : -110 (exp. 2).
[54952.008494] uvcvideo: Failed to query (135) UVC control 3 (unit 5) : -110 (exp. 2).
[54952.151021] uvcvideo: Failed to query (135) UVC control 7 (unit 5) : -110 (exp. 2).
[54952.289253] uvcvideo: Failed to query (135) UVC control 9 (unit 5) : -110 (exp. 2).
[54952.785040] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[54952.927159] uvcvideo: Failed to query (135) UVC control 2 (unit 5) : -110 (exp. 2).
[54953.069313] uvcvideo: Failed to query (135) UVC control 6 (unit 5) : -110 (exp. 2).
[54953.211466] uvcvideo: Failed to query (135) UVC control 3 (unit 5) : -110 (exp. 2).
[54953.350062] uvcvideo: Failed to query (135) UVC control 7 (unit 5) : -110 (exp. 2).
[54953.488663] uvcvideo: Failed to query (135) UVC control 9 (unit 5) : -110 (exp. 2).
[54953.489553] gqcam[4247]: segfault at 7582a0 rip 7f903ed3aaf8 rsp 41319ba0 error 4
narf@laptop:~$ ls /dev/video*
/dev/video0
narf@laptop:~$ lsusb
Bus 003 Device 002: ID 5986:0100 Bison Acer OrbiCam
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
narf@laptop:~$ 

I'd appreciate any suggestion given. :)

---

### Post by omnialive on 2009-04-08
I am having the same incompatibility with my Acer 5100, but I did a fresh install of Intrepid Ibex. I might see about installing Gutsy instead. Shame no one has answered this one. It obviously has something to do with the uvc/video driver differences between the OSes

---

### Post by muhyta on 2010-07-24
+1.
Does anybody "win" this bug?

p.s. sorry for my English.

---

### Post by varunendra on 2010-07-24
Hardy is not supported anymore. If you are still using it, better make a fresh install of karmik or lucid.
If this problem still prevails then, you should start a new thread.
Just an opinion :)

---

### Post by robert shearer on 2010-07-24
Hardy is **still** supported.

From Wikipedia..
Ubuntu 8.04 (Hardy Heron), released on 24 April 2008, was Canonical's eighth release of Ubuntu. It was the second Long Term Support (LTS) release. Ubuntu 8.04's support will end in **April 2011** for desktops and April 2013 for servers.

---

### Post by varunendra on 2010-07-24
> **robert shearer said:**
> Hardy is **still** supported.

From Wikipedia..
Ubuntu 8.04 (Hardy Heron), released on 24 April 2008, was Canonical's eighth release of Ubuntu. It was the second Long Term Support (LTS) release. Ubuntu 8.04's support will end in **April 2011** for desktops and April 2013 for servers.

Oops...., my mistake#-o
I simply used a 2yr calculation (now I realize I should've made it 3 instead!):-#


But if it is still supported, there should be fixes & updates released. Then why is such an old issue still persistent? I mean the above guys must have searched over the net in the meanwhile...!! (to be honest- I didn't, I'm happy with my Karmik u c!!)

Anyways, sorry for the mistake!

---

### Post by philinux on 2010-07-24
> **varunendra said:**
> Oops...., my mistake#-o
I simply used a 2yr calculation (now I realize I should've made it 3 instead!):-#


But if it is still supported, there should be fixes & updates released. Then why is such an old issue still persistent? I mean the above guys must have searched over the net in the meanwhile...!! (to be honest- I didn't, I'm happy with my Karmik u c!!)

Anyways, sorry for the mistake!

Check this out.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by varunendra on 2010-07-24
> **philinux said:**
> Check this out.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Yes I've got it!
I'll shut up now....

(I think I should spend more time in learning rather than making answers I'm not sure about...:oops:)

---

### Post by Iowan on 2010-07-24
> **varunendra said:**
> But if it is still supported, there should be fixes & updates released. I had updates awaiting for this (Hardy) machine this morning. :)

---

