---
title: "Trouble getting Ubuntu 8.04 to recognize wireless devices"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by Eeeff on 2008-12-13
Recently installed Ubuntu 8.04 iso on my Dell Inspiron 1720 from the Ubuntu website. Everything works lovely except it doesn't seem to recognizing my wireless card.
I'd download the updates providing I had internet, haha.

Any help?

---

### Post by Ayuthia on 2008-12-13
> **Eeeff said:**
> Recently installed Ubuntu 8.04 iso on my Dell Inspiron 1720 from the Ubuntu website. Everything works lovely except it doesn't seem to recognizing my wireless card.
I'd download the updates providing I had internet, haha.

Any help?

We need some help identifying your wireless card.  Can you post the results of:
```
lspci -nn
```

---

### Post by Eeeff on 2008-12-13
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

---

### Post by Ayuthia on 2008-12-13
You will want to try this link:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)
It will tell you where to download the wl driver that you need to get your wireless card to work.  The only difference is that the driver name has changed so the instructions for:
```
tar -xzf hybrid-portsrc-x86_64_5_10_27_6.tar.gz
```
is now:
```
tar -xzf hybrid-portsrc-x86_64_5_10_27_11.tar.gz
```

The other option is to try out 8.04.1 or 8.10 where the wl driver is installed by default for your card.

Let us know if you have any problems.

---

### Post by Eeeff on 2008-12-13
Currently trying to un-tar the file, not working out so well.

defford@Elizabeth:~/wdriver$ tar -xzf hybrid-portsrc-x86-32_5_10_27_11.tar.gz
tar: hybrid-portsrc-x86-32_5_10_27_11.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

That's the output. Don't know why it won't recognize, I've tried it several times.

---

### Post by Eeeff on 2008-12-13
Ok, got past the last post, but now onto a new problem. I've checked my spelling several times but when trying to create my wl.ko file this comes out...

defford@Elizabeth:~$ make -C /lib/modules/<2.6.24-19-generic>/build M='pwd' clean
bash: 2.6.24-19-generic: No such file or directory


When I type in my kernel without the brackets I get a completely different response, I get

defford@Elizabeth:~$ make -C /lib/modules/2.6.24-19-generic/build M='pwd' clean
make: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.24-19-generic/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.24-19-generic/pwd/Makefile'.  Stop.
make: *** [_clean_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

---

### Post by Ayuthia on 2008-12-13
> **Eeeff said:**
> Currently trying to un-tar the file, not working out so well.

defford@Elizabeth:~/wdriver$ tar -xzf hybrid-portsrc-x86-32_5_10_27_11.tar.gz
tar: hybrid-portsrc-x86-32_5_10_27_11.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

That's the output. Don't know why it won't recognize, I've tried it several times.

Can you check and see if you are in the correct directory?  If it is, can you post the results of:
```
ls
```I just want to see what files are there.  I might have missed the spelling of the file.

---

### Post by Eeeff on 2008-12-14
defford@Elizabeth:~/wdriver$ ls
hybrid-portsrc-x86-64_5_10_27_11.tar.gz  lib  Makefile  src

---

### Post by Ayuthia on 2008-12-14
The driver you downloaded is a 64-bit driver.  Are you using 64-bit?  If so, please try:
```
tar -xzf hybrid-portsrc-x86-64_5_10_27_11.tar.gz
```
That was the problem.  The guide that you were using was for 32-bit.

---

### Post by Eeeff on 2008-12-14
So is there a guide for 64-bit?
How can I find out if I'm using a 64-bit or 32-bit system?

---

### Post by Ayuthia on 2008-12-14
> **Eeeff said:**
> So is there a guide for 64-bit?
How can I find out if I'm using a 64-bit or 32-bit system?

At the terminal, type:
```
uname -m
```
If it says x86_64, then it is 64-bit.  If it shows i386, i586, or i686, it is 32-bit.

The instructions are the same for 32-bit and 64-bit with the exception of the filename.  You should be able to use the rest of the instructions just fine.

---

### Post by Eeeff on 2008-12-14
Ok, so I have a 32-bit driver, I deleted my 64-bit version, and now I replaced the 64 in the code with a 32, and it is back to not recognizing the file

---

### Post by Eeeff on 2008-12-14
These are the two commands that happen now when I first use the ls command, and then I do that step in the guide.

defford@Elizabeth:~/wdriver$ ls
hybrid-portsrc-x86-32_5_10_27_11.tar.gz

defford@Elizabeth:~/wdriver$ tar -xfz hybrid-portsrc-x86-32_5_10_27_11.tar.gz
tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by Eeeff on 2008-12-14
double post

---

### Post by Ayuthia on 2008-12-14
This should work:
```
tar -xvvf hybrid*.tar.gz
```
This has a wildcard (*) that should allow the system to find the file.

---

