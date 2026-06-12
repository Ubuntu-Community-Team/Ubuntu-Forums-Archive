---
title: "Can't get IP with Intel 5300 AGN"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by bacota on 2010-02-01
I am using 64bit  ubuntu 9.10 on a Dell Vostro 1720 with an Intel 5300 AGN.  I cannot get an IP address from my router (Gigaset SE567 that works fine with everything else).

root@manager-laptop:~# ifup wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:21:6a:5f:6d:d6
Sending on   LPF/wlan0/00:21:6a:5f:6d:d6
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


After running out of other ideas, I installed a custom kernel 2.6.32.7 but it didn't help.
I would appreciate any advice.   Here is all the relevant information I can think of:

root@manager-laptop:~# iwconfig wlan0
wlan0     IEEE 802.11abgn  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
lshw -C network ..

      description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:5f:6d:d6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:fa000000-fa001fff

root@manager-laptop:~# lsmod | grep iwlagn
iwlagn                111816  0 
iwlcore               121178  1 iwlagn
mac80211              189985  2 iwlagn,iwlcore
cfg80211              140583  3 iwlagn,iwlcore,mac80211


From /var/log/messsages

Feb  1 09:23:53 manager-laptop kernel: [   11.359365] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Feb  1 09:23:53 manager-laptop kernel: [   11.359368] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Feb  1 09:23:53 manager-laptop kernel: [   11.359473] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Feb  1 09:23:53 manager-laptop kernel: [   11.359619] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Feb  1 09:23:53 manager-laptop kernel: [   11.399924] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Feb  1 09:24:42 manager-laptop kernel: [   60.019839] iwlagn 0000:0e:00.0: firmware: requesting iwlwifi-5000-2.ucode
Feb  1 09:24:42 manager-laptop kernel: [   60.041644] iwlagn 0000:0e:00.0: loaded firmware version 8.24.2.12

Thank you for any help,
Bruce

---

### Post by Tad2much on 2010-02-01
I am having the exact same behavior.  I have tried using wicd and network-manager.  This is when trying to connect to the network at work which is using PEAP and our old networking using LEAP.

---

### Post by bacota on 2010-02-02
Darn, I get all excited to see a reply hoping to get help, and all I got was a "me, too" :)

Well for what it's worth, I had a simlilar problem a couple years ago with an older Intel wireless controller on Centos.   I just kept watch on kernel.org and upgraded my kernel every time a new one was release.  It started working with issues, and with a later release all the issues went away.  So, I hope that happens again.

A laptop without wireless is really a desktop with a crummy display.

---

