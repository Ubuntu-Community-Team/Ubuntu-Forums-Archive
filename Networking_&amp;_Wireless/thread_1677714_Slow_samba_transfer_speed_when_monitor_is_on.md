---
title: "Slow samba transfer speed when monitor is on"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by Viciou§ on 2011-01-29
Hi!

I am running Ubuntu 10.04 2.6.32-27 on a htpc.
Hardware: Dell Optiplex 745, Intel C2D, nVidia GT210, 2TB SATA drive, RT2860 wireless card.

The problem i'm having is when transferring files from a computer in my network (Win XP SP3 or Win 7) to the htpc.
Both windows computers have gigabit wired network connections.
The htpc have a wireless n connection.
The wireless connection speed and link quality is excellent (300 Mb/s bit rate at -51 dbm signal)

I have a rsync script that I run on the htpc to transfer new files from my windows 7 computer.
I can reach speeds up to 5-6 Mb/s when running the script on the htpc. Average transfer speed is 3,5 Mb/s.
It doesn't matter if I mount using cifs or gvfs and samba.
When the script runs I notice that CPU iowait is pretty high, ~50-60%.

The other day however I noticed transfer speeds of about 10-12 Mb/s when copying from my Windows 7 computer to the htpc (copy ran on Win7 to the smb share on the htpc).
This speed increase happens when the monitor times out (happens after 10 min inactivity in ubuntu, can't set this).
As soon as I woke up the monitor the transfer speed dropped to 4 Mb/s again :(
I tested with the script on the htpc as well and got the speed increase as soon as the monitor went black.

Can anyone explain this?
If I remember correctly I also reached theese higher speeds when I recently installed ubuntu on the computer (pre nVidia drivers).
Could it be that they interfere in some way?

**Edit:** I have now confirmed some of my suspicions. When removing the nVidia GT210 card and using the onboard intel graphics I get transfer rates of ~8-9 MB/s (50 Mbyte in ~5s). Is it the nVidia drivers causing this or something in the configuration that applies when using the nVidia card?

---

### Post by Viciou§ on 2011-01-30
Bump.

Quick summary:
Wireless N transfer rates max out at 5 Mb/s with nVidia card and proprietary drivers.
Wireless N transfer rates reach ~9 Mb/s without nVidia card running on built-in Intel graphics.

When the monitor turns off after 10 minutes of inactivity, running on nVidia drivers, I can upload at 8-12 Mb/s to the computer.
When monitor turns back on the transfer rates drops to half of that.

---

### Post by sikander3786 on 2011-01-30
The issue might be related to Power Supply Unit of your computer. It might be running out of power when graphics are running from Nvidia card thus slowing down not only the wireless speeds but all the hardware in your computer.

At least that is only what I could think of. Which PSU is there? How many watts?

---

### Post by Viciou§ on 2011-01-30
It's a 275W 76 % efficiency psu according to Dell (SFF model).
Hardware inside:
WD Green 2TB Disk (low power).
Asus EN210 PCI-E card (passively cooled, no fan).
Cheap Sweex wireless N card, low profile.
Intel C2D E6300 1.86 GHz.
Slim line DVD.
Dell motherboard.
1 GB RAM, 2*512 MB.

Haven't really thought about the PSU before.
Always thought that when the computer runs without a problem the PSU shouldn't be a problem.
But I guess I will have to try a beefier PSU, have a spare 460 W lying around.

---

### Post by sikander3786 on 2011-01-30
Yes I would recommend a 400+ W PSU with your hardware. Let us know how that goes so others might benefit from your experience ;-)

---

### Post by Viciou§ on 2011-01-31
Tested with the 460 W PSU but same thing happens.
Transfer speeds today with 460 W PSU:
~3-4 Mb/s when monitor/display is on.
~8-9 Mb/s after monitor is "shut down" from system.
This PSU is good, ran Phenom2 quad 955 BE, ati 4890, 4xddr3, 2 sata on it.

Ran a quick psu calculator and came up with ~200 W usage on the htpc system.

So it's not a PSU related problem at least :(
Does anyone have an idea as how to troubleshoot this further?

---

### Post by Viciou§ on 2011-02-03
Anyone? :(

---

