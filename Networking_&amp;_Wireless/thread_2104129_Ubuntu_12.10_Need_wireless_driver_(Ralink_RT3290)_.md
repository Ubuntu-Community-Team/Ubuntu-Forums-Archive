---
title: "Ubuntu 12.10: Need wireless driver (Ralink RT3290?) for HP Pavilion b002eo"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by Pepparroten on 2013-01-12
Hi all!

Need some help with my wireless drivers. Spent the last day installing Ubuntu 12.10 dualboot on a Hp pavillion 14-b002eo that came with preinstalled Windows8.

I finally got everything working, except for the wireless network. In W8 everything works fine. In Ubuntu, I can access via ethernet, but can't find any wireless connection. In fact, I wonder if the system even knows there is a wireless card...

Since many threads seem to have been solved with broadcom and sta-drivers I first tried them out but with no success. When I go to the software centre and the menu "additional drivers" it is blank and a text beneath the empty box says: "No proprietary drivers are in use". (It has always looked like this since the installation of U12.10 [now 3.5.0-21-generic x86_64])

In W8 it says my wireless card is a Ralink RT3290 802.11bgu.
Here is the result when I print some commands:

lspci:
01:00.0 Network controller: Ralink corp. Device 3290
01:00.1 Bluetooth: Ralink corp. Device 3298
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

lspci -nn | grep 3290:
01:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]

ifconfig:
eth0      Link encap:Ethernet  HWaddr 84:34:97:83:cc:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1368 (1.3 KB)  TX bytes:12588 (12.5 KB)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32672 (32.6 KB)  TX bytes:32672 (32.6 KB)

iwconfig:
eth0      no wireless extensions.
lo        no wireless extensions.

So. I really am lacking something, but don't know what or where to look. Can someone help me? Thanks.

---

### Post by Yellow Pasque on 2013-01-12
First, you need the firmware file (put it in /lib/firmware): [https://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=rt3290.bin;hb=HEAD](https://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=rt3290.bin;hb=HEAD)

Next, get a newer kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.2-raring/) (get the -headers and-image .debs that match your architecture)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

---

### Post by Pepparroten on 2013-01-12
Wonderful! Now it all works! Many thanks!

---

### Post by kaha6uc on 2013-01-18
If there was a thank you button here, I would press it tenfold! Thank you!

---

### Post by gruetar on 2013-02-26
Is your bluetooth also working? I have the wifi working but no bluetooth!

---

### Post by michaeljwjr on 2013-02-28
I tried this with kernel 3.8.1 and I still can't get it to work. I'm using 12.04 does this only work if I upgrade to 12.10? Or does this only work if I fresh install 12.10?

---

### Post by VSobota on 2013-03-15
> **Temüjin said:**
> First, you need the firmware file (put it in /lib/firmware): [https://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=rt3290.bin;hb=HEAD](https://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=blob_plain;f=rt3290.bin;hb=HEAD)

Next, get a newer kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.2-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7.2-raring/) (get the -headers and-image .debs that match your architecture)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

Hi, unluckily, I have the same problem (In Linux Mint 14 - basically Ubuntu 12.10) with the same Ralink, but the firmware repository doesn't exist anymore :( Could anybody please provide another link? Or would even newer kernel (newer than 3.7.2.) be a solution? :confused: Thanks in advance for your kind reply!

---

### Post by Yellow Pasque on 2013-03-15
Any kernel >= 3.7.x should work (get the -image and -headers .debs that correspond to your architecture as well as the -all .deb): [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
The firmware file is attached to this post.

Just for reference, here is the Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

---

### Post by Piddell on 2013-04-06
My HP Pavilion 15 with a RT3290 does not find the wifi. I upgraded the kernel as advised above,no joy so then to the latest 3.8, same problem.

I have just tried 13.04 beta in live mode and its much the same story - 
I get the message "device not ready (firmware missing)" from the little network icon at the top of the screen
[B]
from 13.04 LIVE[/B]
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
01:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 84:34:97:78:61:4b  
          inet addr:192.168.1.95  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8634:97ff:fe78:614b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4586324 (4.5 MB)  TX bytes:408715 (408.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76680 (76.6 KB)  TX bytes:76680 (76.6 KB)

ubuntu@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

ubuntu@ubuntu:~$ uname -r
3.8.0-16-generic

---

### Post by Piddell on 2013-04-06
Sorted, I followed this thread - [http://forum.novatech.co.uk/showthread.php?25562-How-to-get-the-RAlink-3290-wireless-working](http://forum.novatech.co.uk/showthread.php?25562-How-to-get-the-RAlink-3290-wireless-working) and I'm online with LIVE 13.04.
Phill

---

### Post by fipem on 2014-01-21
same problem here..., updated to lates kernell and copy paste the .bin file... nothing happens, still no wifi, please help

---

