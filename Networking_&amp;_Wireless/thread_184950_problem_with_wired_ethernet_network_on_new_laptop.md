---
title: "problem with wired ethernet network on new laptop"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by eckmann on 2006-05-30
Hi all,
  I just installed Ubunto 5.10 AMD 64 bit on an Acer Aspire 5004WLMi Notebook dual boot with Windows XP Home.  I understand that the onboard wireless would not work out of the box, but I read somewhere that the wired networking should work.  I plugged in a working network cable into the ethernet port and during installation of Ubuntu, it could not configure it for DHCP.  (Note: this network cable definitely works with other machines using DHCP (and even this machine when I boot into Windows.))

I ended up having to choose the option to configure the network later.  Then when the installation finished and the machine was booted into Ubuntu, I tried to get the wired networking working.  Here's what I did:
I followed some of the suggestions in:
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

and to turn off ipv6 I did this:

sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a

When I do:
sudo mii-tool eth0
I get:
eth0: no autonegotiation 100baseTx-HD, link ok

When I do:
ifconfig eth0
I get:
eth0      Link encap:Ethernet  HWaddr 00:16:36:2A:B2:25
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:3 Base address:0x1800

When I do:
lspci | grep Eth
I get:
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)

When I do:
lsmod | grep mii
I get:
mii                     6144  1 sis900

I tried:
sudo ifconfig eth0 up
and this changed nothing.

Any help you can provide would be appreciated.

Thanks.

Mike

---

### Post by eckmann on 2006-05-31
At this point, please ignore question above.  I tried many things last night and this morning and could never get it to work.  I also tried to get the wireless to work (using 64bit drivers and ndiswrapper) without luck.  (... and I'm not a newbie -- I've installed many different versions (mostly Redhat) of linux over the last 8 years on many machines, but never on a laptop.)

Anyway, I decided to install the x86 version of Ubuntu 5.10 and wipe out the AMD64bit version.  I'm doing that now and it detected my wired network fine.

Thanks for reading.

Mike

---

