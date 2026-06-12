---
title: "Android Phones file transfer"
date: 2020-08-16
forum: Mobile Technology Discussions (CLOSED)
---

### Post by MaximB on 2020-08-16
Hi,
Today I bought Samsung Galaxy A51 phone and the file transfer to Linux problem got worse,
The phone is connected via USB C cable, and the connection is very unstable.
Sometimes it won't even recognize the device at all and won't mount it.
Sometimes it will get stuck in the middle of file transfer, or when calculating folder's space.
The file transfer rate is also sometimes very slow (specially if I have lots of small files).
I transfer files to the internal storage, not SIM (in this case).
Why it happens and is there a way to solve this?

---

### Post by TheFu on 2020-08-16
Bad USB cable?  Try a different cable from a different batch.
Also, would be good to know the OS, release, DE, ... heck, just post **inxi -Fz** output so we get all that data at once, please.

---

### Post by MaximB on 2020-08-16
Tried several cables, some of them do not work at all with A51 (they worked with my older phone),
Only the official one and the one from OnePlus work
The A51 is out of the box, bought it today.
And my PC is new as well...
 
maxim@Maxim-HQ:~$ sudo inxi
CPU: 12-Core AMD Ryzen 9 3900X (-MT MCP-) speed/min/max: 2196/2200/3800 MHz Kernel: 5.4.0-42-generic x86_64 Up: 15h 12m 
Mem: 10905.3/64296.8 MiB (17.0%) Storage: 18.19 TiB (43.4% used) Procs: 445 Shell: bash 5.0.17 inxi: 3.0.38 
and here:
[https://termbin.com/bnmi](https://termbin.com/bnmi)

The transfer is so slow...
Maybe I put it at the slow USB slot?
I got at the box blue, black. and at the motherboard red and blue USB slots.
The motherboard is

---

### Post by T6&amp;sfpER35% on 2020-08-16
look at KDE connect

---

### Post by MaximB on 2020-08-16
Thanks,
It did paired with my device, and I gave the correct permissions.
However for some reason when I try to upload folders and files from the PC to mobile, it complains about not finding the files (although I shared the downloads folder on the mobile and can see the files).

---

### Post by TheFu on 2020-08-16
A few other ideas...

MTP mode enabled on Android?  
My android devices just show up when i run caja (the mate file manager).
Once I used **adb push**. That's fine for getting lots of files on a device.

Most of the time, I'll just just use the nextcloud client to "pull" xfer files overnight from my nextcloud server to any client.
If I'm in a hurry, I&#8217;ll use an sftp client.

---

