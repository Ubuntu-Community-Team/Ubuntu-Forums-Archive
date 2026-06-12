---
title: "latest upgrade: PC reset as backend starts"
date: 2008-07-18
forum: Mythbuntu
---

### Post by dibuntux on 2008-07-18
My system (specs follows) was perfect with mythbuntu 7.10 and then with 8.04 for more than a year. Then one of the latest package change (nvidia driver? kernel .19? other?) put me in the unrecoverable condition of the PC resetting as soon as mythbackend starts: hard reset - something not seen since the '90s...
So, after trying everything, I decided to install the new 8.04.1 from scratch, formatting the disk. I finish the install, updating the system with latest packages, including nvidia driver & the other supplemental packages in myth, and at the restart - again, it reset at the starting of mythbackend.
The system then restart again, loading just the front end - if you exit on a terminal and start manually mythbackend -> RESET.

Now I'm trying reinstallin without updating packages...let's see...

My system:
MSI K7T Turbo 512 MB SDRAM PC133 Athlon XP 1700+
Nvidia FX5200 connected in DVI to a 720p DLP projector
Hauppauge HR1100 DVB-T + Analog TV PAL
Technisat SkyStar 2.6
DVD-ROM Matsushita

Any ideas?

---

### Post by ian dobson on 2008-07-18
Hi,

What happens when you try and access you DVB card from outside mythtv, with something like szap/w_scan?

8.04 updated the kernel/drivers could it be that you're having problems with one of your drivers? 

Maybe try removing the SkyStar/Hauppauge cards then starting the backend to see if thats the problem.

Regards
Ian Dobson

---

### Post by dibuntux on 2008-07-18
Thanks for your fast reply - it appears to be some kind of interrupt problem - I reinstalled 8.04.1 Alternate for the 3rd time and I got auto-reset, auto power down as soon as X login appears (NOT gracefully) and HAL init fail after entering X.
Now I'm trying with old 8.04 live - and I can only see the Analog card part of the Hauppage HVR1100 - DVB-T cannot open device and SkyStar not even listed.

So, ok I will remove the HVR1100 and try with only the SkyStar - Still this is very strange: the same hardware combination had worked for months!

---

### Post by dibuntux on 2008-07-21
No luck. I reinstalled with only the skystar and it does the same: it resets the PC as soon as the backend start. 8.04.1 with no restricted drivers loaded. The hardware is OK, this is a SW mess...

---

### Post by ian dobson on 2008-07-21
Hi,
What happens if you try with no card installed?

Regards
Ian Dobson

---

### Post by dibuntux on 2008-07-21
I installed again using 8.04.1 Desktop standard install, instead of alternate. Kept all settings to very standard. Just the Skystar install.
I came up with a perfectly working system.
I added Nvidia drivers -> ok
I added channels & input to the system -> ok, could watch TV
I added medibuntu restricted support (w32, dvd, etc.)
Try to watch TV again -> system power OFF!

and it does not get on again... you have to pull the AC cable and reinsert, then you can power the box again. It starts up OK, you got the menu and...

I wanted to revert to no medibuntu restricted support, switch to settings and... power OFF again! 

So, ok it could be the mainboard and/or power supply - but they had worked ok for years! mmmmhhhh

---

### Post by dibuntux on 2008-07-22
"...when you have analyzed everything, and excluded the impossible, what is left, even though improbable, must be the truth"
Sherlock Holmes

It was a (sudden become) defective Power Supply!!!!!!!!!!

Changed it - 8.04.1 with all upgrades working fine with Skystar 2.6

Tomorrow I will add again the Hauppage HVR1100

Thanks for Helping...

---

