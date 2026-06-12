---
title: "wifi is not working"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by mahendrahpu on 2009-12-29
hi
i install ubuntu in hp pavilion leptop ,all is well but wireless is not working...........so please tell me what should i do
 i am new to it....

---

### Post by mahendrahpu on 2009-12-29
ifconfig details are

eth0      Link encap:Ethernet  HWaddr 00:26:22:9a:3f:50  
          inet addr:172.16.8.115  Bcast:172.16.9.255  Mask:255.255.254.0
          inet6 addr: fe80::226:22ff:fe9a:3f50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11765314 (11.7 MB)  TX bytes:2325499 (2.3 MB)
          Interrupt:30 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


and i install broadcom driver[ [http://www.broadcom.com/support/802.11/linux_sta.php]](http://www.broadcom.com/support/802.11/linux_sta.php])
for that but it is not working

so plz...........

---

### Post by focwiz on 2009-12-29
> **mahendrahpu said:**
> ifconfig details are

eth0      Link encap:Ethernet  HWaddr 00:26:22:9a:3f:50  
          inet addr:172.16.8.115  Bcast:172.16.9.255  Mask:255.255.254.0
          inet6 addr: fe80::226:22ff:fe9a:3f50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11765314 (11.7 MB)  TX bytes:2325499 (2.3 MB)
          Interrupt:30 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


and i install broadcom driver[ [http://www.broadcom.com/support/802.11/linux_sta.php]](http://www.broadcom.com/support/802.11/linux_sta.php])
for that but it is not working

so plz...........

Did you go to System->Administration->Hardware Drivers and activate the Broadcom STA driver?

---

### Post by bkratz on 2009-12-29
You might want to post the outputs of lspci -nn   (LSPCI in lowercase) and also   sudo lshw -C network


also is there some switch or key combination to turn on wireless?

---

### Post by mahendrahpu on 2009-12-29
broadcom b43 wireless driver install successfully but broadcom sda wireless driver installation give the following error.
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb) Could not resolve 'archive.ubuntu.com'


output of lspci -nn is


$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
04:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
04:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
04:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
04:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]

---

### Post by focwiz on 2009-12-29
> **mahendrahpu said:**
> broadcom b43 wireless driver install successfully but broadcom sda wireless driver installation give the following error.
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb) Could not resolve 'archive.ubuntu.com'


Yes...to activate STA driver, you have to be connected to the internet (I had to connect via regular wire connection).  After that, wireless worked perfectly.

---

### Post by FuManShu on 2009-12-30
bcmwl-kernel-source is also available on the live cd, which you can install directly from if you do not have internet access or don't want to wire up.

---

### Post by ppillard on 2009-12-30
I have the same machine with the same problem.  I am running Jaunty 9.04.  While trying to install the STA package, I get the following error message:

Error: Dependency is not satisfiable: dkms.

I thought DKMS was native to Jaunty.  Otherwise, I have downloaded DKMS, but am a dummy when it comes to installing it.  Any help out there?

---

### Post by FuManShu on 2009-12-30
So you have downloaded DKMS but not installed it?  You can use gdebi to install it by just opening the file and hitting install package (it will prompt for your credentials).  If that doesn't work, try:

sudo aptitude reinstall dkms

and see if that gets it going.  Then try the STA driver and load the bcmwl-kernel-source package and see how that goes from there.

---

