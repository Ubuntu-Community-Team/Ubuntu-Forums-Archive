---
title: "ethernet dont work"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by siq on 2006-06-09
Hello, 
i installed ubuntu on a HP vectra xe310.
lspci shows that the integrated nic is a intel corp.82801 BA.
I can't find the right module(exact name), i tried several others (by modprobe or insmod) but when i try ifconfig eth0 up, i get the message:
SIOCSIFFLAGS: device or resource busy

---

### Post by ns2048 on 2006-06-09
Hello,

Could you post the output of 'lspci'

--ns2048

---

### Post by siq on 2006-06-12
Hello, 
thanks for your reply. Here's the lspci result:

0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
0000:01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

---

