---
title: "gdm fails to load; display freezes showing onthing but vertical bars"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Roobert on 2007-10-20
Hi,

I booted into Gutsy this morning, and right before I reached the Ubuntu login screen, the screen turned into a wall of multicolored, vertical stripes, and froze. Using Ctrl+Alt+F2 didn't switch to the command line as usual. I had to hard-reboot, but was met with the same wall of garbage each time. 

If I boot up using kernel version 2.6.20-16, gdm seems to work fine and I can login. I haven't tried going back to 2.6.22 yet, as I wanted to get this post into the forums in case my gdm never comes back. I'm not sure which log files I should check for error messages. If someone can tell me where to look for more info, I report back, if possible.

Graphics Card: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
Driver: Intel experimental modesetting driver

Thanks for any suggestions!

---

### Post by anubhavrocks on 2007-10-20
Post the output of 
```
 cat /var/log/gdm/\:0.log
```

after your GDM fails.

---

### Post by Roobert on 2007-10-25
> **anubhavrocks said:**
> Post the output of 
```
 cat /var/log/gdm/\:0.log
```

after your GDM fails.

Thanks for the reply. This gdm failure comes and goes; when it does occur, I typically do a hard reboot, go into 2.6.22 safe mode, and reboot:

```
sudo shutdown -r now
```

Then gdm runs fine when it restarts in 2.6.22. The next time the error occurs, I'll post the output from /var/log/gdm\:o.log as you mentioned.

More later,

~ E.

---

### Post by Roobert on 2007-10-26
Ok, the crash happened again; this time I copied the :0.log file from /var/gdm. Here it is:

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux El-Computorb 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 26 21:47:07 2007
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(EE) intel(0): Unable to read from DVOI2C_E Slave 236.
(EE) intel(0): ivch: Unable to read register 0x00 from DVOI2C_B:04.
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(EE) intel(0): tfp410 not detected got VID FFFFFFFF: from DVOI2C_E Slave 112.
(II) Module already built-in
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Error in I830WaitLpRing(), timeout for 2 seconds
pgetbl_ctl: 0x1ffe0001 pgetbl_err: 0x0
ipeir: 0 iphdr: 50300003
LP ring tail: 1290 head: ac len: 1f001 start 0
eir: 0 esr: 0 emr: ff7b
instdone: ffc1 instpm: 0
memmode: 0 instps: 24
hwstam: fffe ier: 2 imr: 53c iir: c0
Ring at virtual 0xaf976000 head 0xac tail 0x1290 count 1145
	0000002c: 00000000
	00000030: 7d890002
	00000034: 89800000
	00000038: 00000000
	0000003c: 00000000
	00000040: 7c281088
	00000044: 7c291099
	00000048: 7c2a10aa
	0000004c: 7c2b10bb
	00000050: 7d8c0000
	00000054: 10000000
	00000058: 7d8c0000
	0000005c: 30000000
	00000060: 7d8c0000
	00000064: 50000000
	00000068: 7d8c0000
	0000006c: 70000000
	00000070: 7d020000
	00000074: 0000ba98
	00000078: 6700a176
	0000007c: 7c800002
	00000080: 7d810001
	00000084: 00000000
	00000088: 00000000
	0000008c: 7d8b0000
	00000090: a0000000
	00000094: 7d8d0001
	00000098: 00000008
	0000009c: 3f800000
	000000a0: 7d010000
	000000a4: 80808080
	000000a8: 50300003
	000000ac: 03f02000
Ring end
space: 126484 wanted 131064

Fatal server error:
lockup

```

Anyone have any ideas what any of this means?

---

