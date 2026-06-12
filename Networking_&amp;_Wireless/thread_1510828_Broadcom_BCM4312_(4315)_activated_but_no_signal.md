---
title: "Broadcom BCM4312 (4315) activated but no signal"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by ofir_k on 2010-06-16
Hello,

I recently bought a Lenovo laptop which comes with a wireless card called Broadcom BCM4312 but in dmesg it says "bcm4315 hybrid wireless controller".

Jockey says the driver is installed, activated and in use. However I don't get any signal (I even moved the laptop to the same room the wireless router is).

I run iwevent and nothing appeared.

I run Kubuntu 10.04, fresh install from a USB stick, latest updates. I replaced knetworkmanager with the network-manager-gnome. network-manager-gnome works fine and I can connect to wired connection with no problem.

network-manager-gnome says that the wireless is disconnected.

What can be done to make the wireless work?

Thanks,
Ofir

---

### Post by ofir_k on 2010-06-17
I searched the internet and it seems that the driver called STA from jockey (Hardware Drivers) is the one for Broadcom BCM4312 (4315).

So, I reinstalled it and rebooted and nothing!

After more reading I encountered some post which says to load the defaults in the BIOS and that should fix the wireless problems.

So I did it, and the wireless come back to life!!!


My home wifi is secured with WPA auth. Immediately after connecting to it, the wireless connection drops. It doesn't happen on my other laptop (kubuntu 10.04 with network manager).

Why the wireless connection keeps dropping? Is there a way for debugging the connection?

Thanks,
Ofir

---

### Post by kahnoie on 2010-06-17
I have the same problem. I have currently installed STA driver from the restricted drivers and rebooted. I still cant get it to work
Here is my output:
uname -a
Linux amit-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

lspci -nn | grep BCM
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
____________________________________________________________________________________________
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 0c:60:76:44:a6:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl2 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:d9000000-d9003fff

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:9e:49:7c:24  
          inet addr:10.8.1.158  Bcast:10.8.255.255  Mask:255.255.0.0
          inet6 addr: fe80::226:9eff:fe49:7c24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:719538 (719.5 KB)  TX bytes:58147 (58.1 KB)
          Interrupt:31 

eth1      Link encap:Ethernet  HWaddr 0c:60:76:44:a6:4a  
          inet6 addr: fe80::e60:76ff:fe44:a64a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ofir_k on 2010-06-17
kahnoie, have you tried to load defaults in the BIOS?

I will summarize the steps I did to get the driver work:
[LIST=1]
[*]Install the driver through "Hardware Drivers"
[*]Reboot and enter the BIOS
[*]Load defaults in the BIOS using "Load defaults"
[/LIST]
After these steps I can see networks and connect to them, **but the connection drops frequently!**

---

### Post by ofir_k on 2010-06-22
Finally, I got it working.

I will list the steps needed for getting this driver to work:
[LIST=1]
[*]Install Ubuntu
[*]Activate the **B43 driver** from "Hardware Drivers"
[*]Follow the instructions found here: [http://ohioloco.ubuntuforums.org/showpost.php?p=7950101&postcount=1](http://ohioloco.ubuntuforums.org/showpost.php?p=7950101&postcount=1)
[*]**_On reboot, enter the BIOS and load defaults_**
[*]Done!
[/LIST]

Now I have boot issues, where Kubuntu sometimes just will hang on boot... anyway, this is for another thread.

This is marked as SOLVED!

---

