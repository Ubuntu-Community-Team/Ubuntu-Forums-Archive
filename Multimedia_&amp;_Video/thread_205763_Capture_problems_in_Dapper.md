---
title: "Capture problems in Dapper"
date: 2006-06-28
forum: Multimedia &amp; Video
---

### Post by tina on 2006-06-28
Hi,

I'm trying to capture DV over Firewire from a Canon camcorder in Ubuntu 6.06. 

I've tried with Kino (as superuser), dvgrab and Cinelerra. I've also tried to detect my device with gscanbus...  If the device is being detected, it's not responding to stop/play or anything in gscanbus. This is also the case in Kino. 

At first in Kino the capture options were inaccessible with the error 

"Warning: raw1394 Kernel module not loaded or failure to read/write /dev/raw1394"
 
So I opened Kino from sudo su and capture options appeared. I RTFM and it seemed very simple but the camcorder is not responding to Kino with play back etc. Nothing appears and nothing happens pressing stop/play etc. 

In Cinelerra, it says it's capturing and but nothing actually happens - but a green screen.

dvgrab reports "error: no DV" 

I'm actually no expert in film making or editing, I'm really new to this but I've been poking around in Linux a bit for a while and would really like to be able to do video in the free world.

I would love some help or ideas.

Thanks,
Tina

---

### Post by tina on 2006-06-29
My capture card is a DVico FireBird XE - it doesn't appear in Sysinfo.

Could the problem be an incompatiblity issue with the card?

Any help is much appreciated.

---

### Post by gratefulfrog on 2006-06-29
Hi!
We've all had pbs with this!

first Check the permissions of your 1394 devices: they need to be +r+w for all:
if they're not +r+w for all, do this:
```
> sudo chmod a+rw /dev/*1394
```

This fix is only temporary until the next reboot, you'll have to do it each time...

Then, try using dvgrab manually setting the camcorder to play after starting capture.

Let me know the error messages!

Take a look at my video help page at:
[http://gratefulfrog.net]("http://gratefulfrog.net/")

maybe that will help!

let me know!
GF.

---

### Post by sascha on 2006-07-28
I have the same problem and I tried your suggestion'sudo chmod a+rw /dev/*1394', and no effect.

Do you have any other suggestions?

---

