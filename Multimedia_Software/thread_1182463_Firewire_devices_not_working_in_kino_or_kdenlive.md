---
title: "Firewire devices not working in kino or kdenlive"
date: 2009-06-09
forum: Multimedia Software
---

### Post by Newtothegame on 2009-06-09
Hey All,

I have spent the past two hours trying to figure this out and I am at a loss. I am trying to get a Firewire video device to work in ubuntu studio. I will post what i have found:

FIREWIRE STACK
video1394              26216  0 
dv1394                 28904  0 
raw1394                35976  0 
ohci1394               42548  2 video1394,dv1394
ieee1394              110176  4 video1394,dv1394,raw1394,ohci1394

50-udev-default.rules
# Firewire
KERNEL=="dv1394[0-9]*",		NAME="dv1394/%n", GROUP="video"
KERNEL=="video1394[0-9]*",	NAME="video1394/%n", GROUP="video"
KERNEL=="raw1394",		GROUP="disk"

ls -l /dev/raw1394

crw-rw---- 1 root disk 171, 0 2009-06-08 22:09 /dev/raw1394

ran dmesg: got:
[ 2381.411347] __ratelimit: 293 callbacks suppressed
[ 2381.411349] ohci1394: fw-host0: isochronous cycle too long
[ 2381.421723] ohci1394: fw-host0: isochronous cycle too long
[ 2381.432097] ohci1394: fw-host0: isochronous cycle too long
[ 2381.442471] ohci1394: fw-host0: isochronous cycle too long
[ 2381.463221] ohci1394: fw-host0: isochronous cycle too long
[ 2381.479718] ohci1394: fw-host0: isochronous cycle too long
[ 2381.510849] ohci1394: fw-host0: isochronous cycle too long
[ 2381.521219] ohci1394: fw-host0: isochronous cycle too long
[ 2381.548093] ohci1394: fw-host0: isochronous cycle too long
[ 2381.595716] ohci1394: fw-host0: isochronous cycle too long

Please help.

I am so confused
-Newtothegame

---

### Post by pablosanchezuy on 2009-06-10
well i have a similar situation on 9.04 64bit .
i have a compaq 6820s with no firewire port, so i got a express card to connect a panasonic PV-GS80 with similar results.

lsmod | grep 1394
video1394              26216  0 
dv1394                 28680  0 
ohci1394               42036  2 video1394,dv1394
raw1394                35592  0 
ieee1394              108288  4 video1394,dv1394,ohci1394,raw1394

ls -l  /dev/raw1394 
crw-rw-rw- 1 root video 171, 0 2009-06-10 01:28 /dev/raw1394

The curious thing is last year i got some videos from the same camera with the same express card, on 8.04 i guess (7.10?), with this same notebook .

So tomorrow is my son's birthday , and so far i have no tape for it as i can't
download them to disc. 
Kino's status bar displays : " WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!"
Running kino as root (sudo) gives the same message.

Pablo .

EDIT - i'm chewing my tongue . By accident i restarted the notebook with the camera plugged in and voila, kino is working.
So this is to it, keep it plugged on startup ?

Pablo

---

### Post by Newtothegame on 2009-06-10
> **pablosanchezuy said:**
> well i have a similar situation on 9.04 64bit .
i have a compaq 6820s with no firewire port, so i got a express card to connect a panasonic PV-GS80 with similar results.

lsmod | grep 1394
video1394              26216  0 
dv1394                 28680  0 
ohci1394               42036  2 video1394,dv1394
raw1394                35592  0 
ieee1394              108288  4 video1394,dv1394,ohci1394,raw1394

ls -l  /dev/raw1394 
crw-rw-rw- 1 root video 171, 0 2009-06-10 01:28 /dev/raw1394

The curious thing is last year i got some videos from the same camera with the same express card, on 8.04 i guess (7.10?), with this same notebook .

So tomorrow is my son's birthday , and so far i have no tape for it as i can't
download them to disc. 
Kino's status bar displays : " WARNING: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!"
Running kino as root (sudo) gives the same message.

Pablo .

EDIT - i'm chewing my tongue . By accident i restarted the notebook with the camera plugged in and voila, kino is working.
So this is to it, keep it plugged on startup ?

Pablo

Hey Pablo, 

I do know you need the camera plugged in and on to get the raw1394 port to boot/look for the camera. I read it some place.
 
As for myself. Still no luck, on or off. Also I am about to make another post considering video drivers. Seems I built a video box with intent to run Ubuntu, and so far its Pointless. 

-Newtothegame

---

### Post by mey on 2009-06-12
I guess you already tried this ?

sudo chmod 777 /dev/raw1394

---

