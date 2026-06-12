---
title: "Broadcom NetXtreme BCM5705M tg3 not working in kernel 2.6.15-25"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by frankster2000 on 2006-06-29
I've run into something that I just can't seem to figure out.  I've been reading the forums here for about 3 hours, and although I see some stuff that seems related, nothing has helped me really get to the bottom of my troubles.  If someone could point me in the right direction I would greatly appreciate it.

Here's what I've got.
Laptop = Dell Latitude D600 
ubuntu 6.06 

Here's what is happening after I upgraded from Breezy to Dapper.
Everything thing is working, except for my gigabit card.  (The wireless works with the ipw2100 modules.)  Only the wired card isn't working.

In kernel 2.6.12-9 I used the tg3 module and it worked great, but now that I've upgraded to 2.6.15-25, it won't work at all.   Here's some more information to help.

Error gotten when trying to start eth0

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
SIOCGMIIPHY on 'eth0' failed: No such device

output from dmesg when module is loaded.
[17179668.960000] Netfilter messages via NETLINK v0.30.
[17179668.968000] ip_conntrack version 2.4 (4093 buckets, 32744 max) - 232 bytes per conntrack
[17179736.020000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17179741.224000] tg3.c:v3.43f (Jan 9, 2006)
[17179741.224000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179741.252000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:e2:ee:5e
[17179741.252000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[17179741.252000] eth0: dma_rwctrl[763f0000]

Output of lspci
0000:00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
0000:02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

downloaded the following driver from broadcom's website
tg3-3.43f.tar.gz

compiled module, and inserted it with no problems.  (Still get same error)

Here's the version of tg3 in the 2.6.9-12 kernel that I was using.

[4294676.348000] tg3.c:v3.31 (June 8, 2005)
[4294676.348000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294676.371000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0d:56:e2:ee:5e
[4294676.371000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[4294676.371000] eth0: dma_rwctrl[763f0000]

current kernel version
2.6.15-25-686

kernel version that tg3 module works under
2.6.12-9-686

I'm kind of at a loss as to what to do at this point other than just revert back to an older kernel.  I just hate to do that.   Anyone got any ideas?   If any other information you need, I'll gladly get it.   Thanks for any help you can give me.

Frankie

---

### Post by frankster2000 on 2006-07-10
:confused: I'm still trying to figure this one one.  I even downloaded and compiled the bcm5700-source package and loaded the bcm5700 module with no luck.   If ANYONE can give me some advice it would be greatly appreciated.

Thanks

---

### Post by gekkonaut on 2006-07-19
Frankster,

I am having the EXACT same problem and it is very annoying!! (Dell D600 also).

I even tried copying the old tg3.c out of kernel 2.6.12 and recompiling it with 2.6.17 AND 2.6.15 but I still can't get a /dev/eth0!!! (I was able to compile 2.6.17 succesfully with the old driver in it, and I get the same behavior as the new driver, so who knows what is going on!)

And the worst part about it is that the new hardware abstraction layer in 6.06 doesn't seem to work with 2.6.12, so I have no sound or certain usb connectivities (ipod).

I am wondering if a reinstall of 6.06 will remedy this? ](*,) ](*,) 

I can't even blame it on the kernel now that I've used the newest kernel will the old working tg3.c. It might be something in the HAL but I have no idea. Maybe I can backport the old HAL and try that and see what else it breaks.

Let me know if you come up with anything.

James

---

### Post by czu on 2006-07-19
I've got a 6.06 box up and runing - kernel 2.6.15.23, AMD64, Trendnet TEW-421 wireless card
**dmesg|grep wireless** output:
> [   37.321443] acx: found ACX111-based wireless network card at 0000:00:0c.0, irq:193, phymem1:0xFAD00000, phymem2:0xFAC00000, mem1:0xffffc2000004c000, mem1_size:8192, mem2:0xffffc20001180000, mem2_size:131072
[   38.417406] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-23-amd64-generic
[   66.569355] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !

I updated to the version 2.6.15.26 of the Kernel, and evrytime I pickup this option from the new GRUB menu list, my netork doesn't work at all:
**dmesg|grep wireless** output:
> [   44.388804] acx: found ACX111-based wireless network card at 0000:00:0c.0, irq:185, phymem1:0xFAD00000, phymem2:0xFAC00000, mem1:0xffffc20000048000, mem1_size:8192, mem2:0xffffc20000100000, mem2_size:131072
[   45.461120] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-26-amd64-generic
[  116.606460] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !

Why does this happens?
TIA

---

### Post by gekkonaut on 2006-07-19
czu,

This thread is not about a wireless issue - we were having problems with the tg3 ethernet driver, not a wireless driver.

On another note, great news!!

I found a solution - 

I've been googling this for weeks but I finally found a post that was pertinent.

frankster -- I bet you have changed your motherboard recently (at least while ubuntu has been installed) - yes?

well this was my issue. my OLD onboard tg3 ethernet's MAC address was listed in /etc/iftab - aparently the old tg3 driver was not aware of this file, but the new tg3 driver (or the new HAL or something else) WAS aware of it.

SO, I had to simply replace the old MAC of my old motherboard's onboard ethernet card with the new MAC in /etc/iftab.

Either that or just clear the file out. When you run the new kernel you probably had a mysterious eth1, right? 

//frustrated this took so long to figure out.

---

### Post by tormod on 2007-02-26
Ran into the same upgrading from Breezy to Dapper... I thought first it was a driver version issue. Found this thread since I also had a tg3 card.

gekkonaut, thanks a lot for reporting the solution here!

---

### Post by Cipher63 on 2008-02-17
I found this at the Sooper Tux blog [http://soopertux.blogspot.com/2008/01/installing-broadcom-netlink-fast.html](http://soopertux.blogspot.com/2008/01/installing-broadcom-netlink-fast.html) after following up on entries from an Austrian UBUNTU user with what appears to be this same issue we are having: (I Hope this helps:))
Fire up your browser and navigate to Broadcom Ethernet NIC NetLink Driver Downloads page. Download the driver titled Linux (tg3).
Open a terminal, login as root using the su command, and navigate to the directory where you downloaded the driver archive linux-3.81c.zip (latest as of this post). 
Unzip the downloaded archive:
# unzip linux-3.81c.zip 
Navigate to the directory just unzipped:
# cd Server/Linux/Driver/.
Untar the arvhice tg3-3.81c.tar.gz:
# tar -xvzf tg3-3.81c.tar.gz
Navigate to the untarred directory:
# cd tg3-3.81c
Make the kernel module:
# make
The make process should output various binaries including tg3.ko which is the kernel module we are interested in. So, install the module:
# make install
Update kernel module dependencies:
# /sbin/depmod -a
Finally, reboot your machine.

---

### Post by clw89u on 2008-04-15
Recently, I installed Ubuntu 7.04 in my NoteBook (compaq nc4010) 

and my wired network card couldn't work correctly.

I felt very confused because I could find the wired network card

in hardware information (therefore, I knew my network card is 

Broadcom NetXtreme BCM5705).

The detail is as the following:

[http://www.pixnet.net/photo/clw89u/87006852](http://www.pixnet.net/photo/clw89u/87006852)

But, I couldn't find the wired card setting in my Network Manager.

The detail is as the following:

[http://www.pixnet.net/photo/clw89u/87006850](http://www.pixnet.net/photo/clw89u/87006850)

I had tried to patch the driver according to the article I found in the forum.

But, my network card still couldn't work correct.

The following is a screen shot of my ifconfig comand after patching:

[http://www.pixnet.net/photo/clw89u/87006849](http://www.pixnet.net/photo/clw89u/87006849)

As Result, my Network Manager still couldn't find my wired network card.

The detail is as the following:

[http://www.pixnet.net/photo/clw89u/87006850](http://www.pixnet.net/photo/clw89u/87006850)

Thanks !

---

