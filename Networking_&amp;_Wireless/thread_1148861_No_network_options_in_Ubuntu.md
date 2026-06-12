---
title: "No network options in Ubuntu"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by kdragonracer on 2009-05-04
I installed Ubuntu 8.04 (Heron) on my laptop a few days ago, but it doesn't seem to be working correctly with the wireless or the wired networking hardware.  I'm dual-booting and Windows can still do everything fine, so I'm guessing it has something to do with the drivers.  Can anyone help me figure out what's going on?

Machine: Toshiba Satellite A105-S2716 with:
  Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller [11ab:4351] (rev 10)
  Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)

Running ifconfig gives me this:
```

eth1      Link encap:Ethernet  HWaddr 00:a0:d1:31:1a:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92100 (89.9 KB)  TX bytes:92100 (89.9 KB)
```iwconfig merely reports that I have no wireless extensions (that doesn't sound right...)
Here's some other results I've gotten from testing:
```
$ifconfig /etc/network/interfaces
/etc/network/in: error fetching interface information: Device not found

``````

$ ping -c 3 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.037 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.037 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.039 ms

--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.037/0.037/0.039/0.007 ms

``````

$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

```Yes, it ends right there, weird.
```
$ netcfg
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 10
       serial: 00:a0:d1:31:1a:3d
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:05:04.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=128 maxlatency=24 mingnt=3
```Help and advice would be very much appreciated!

---

### Post by Tilex on 2009-05-04
I don't want to sound dogmatic, but I would simply suggest you install the latest version of Ubuntun, namely Jaunty Jackalope 9.04 (which is 2 versions newer than 8.04).  

On a side note, I am surprised your Intel 2200 does not work 100% out of the box.

---

### Post by kdragonracer on 2009-05-04
That's the thing, as far as I can tell, there's no reason for the networking not to work out of the box, so I don't want to go through the trouble of burning another disc and installing over the old Ubuntu just to find out it still doesn't work.

Any other suggestions, or should I just upgrade and see if it works?

---

### Post by kdragonracer on 2009-05-05
I'll probably get raged at for double-posting, but I'm going to point out that after spending some more time looking for a solution, the only thing I've heard so far is that a lot of other people have encountered the same or similar problems with newer versions of Ubuntu and the same wireless card. So unless I can get a guarantee Jaunty will fix everything, I'm not going to spend 3 hours downloading it when I could just fix Hardy and let it upgrade itself.

I should point out that the Network Manager in the GUI doesn't even think I have a wireless connection, I believe; I'm also fairly certain both visible networking methods (modem and something else) were also grayed out and unavailable.

Help... please? Despite the business of this forum?

---

### Post by chili555 on 2009-05-05
> it doesn't seem to be working correctly with the wireless or the wired networking hardware.Your wired connection is working fine, except it doesn't appear to be connected.> link=noYour wireless is supposed to use a module named, appropriately enough, *ipw2200*. Please open a terminal and do:```
sudo modprobe ipw2200
```Now does your wireless appear in the Network Manager icon? Can you click it and connect?

I notice that your wired interface appears as eth1; ethernet interfaces are usually eth0. That's not really a fatal error, but we may find it's a hindrance we need to fix.

---

### Post by chili555 on 2009-05-05
> there's no reason for the networking not to work out of the boxThere are several reasons; some well understood and some not very well. Hence a robust bug tracking system.

Please check /lib/firmware/ or /lib/firmware/2.6.27-4-generic (or whatever your kernel version is) for ipw2200 firmware (ipw2200-bss.fw, etc.). 

Also, under System -> Administration -> Hardware Drivers, is there an option to enable the *ipw2200* module?

---

### Post by kdragonracer on 2009-05-09
Sorry for the delay in replying, chili555, and thanks for your help!

Running sudo modprobe ipw2200 didn't do anything right away; on reboot, I did have Wireless Networking (roaming) options set in, but no networks were detected automatically. However, right before the Ubuntu desktop popped up after login, what looked like an error message involving ipw2200 or something briefly appeared, but I missed seeing the actual text. Additionally, on a second reboot, the wireless options disappeared and haven't reappeared despite running the command again; I also haven't been able to see the error message again.

On running the Hardware Drivers tool, no proprietary drivers are shown for me to enable (might explain some sound problems too...)

I checked in the lib/firmware/ directory, and found three ipw2200 files (ipw2200-bss.fw, ipw2200-ibss.fw, and ipw2200-sniffer.fw). There were also files for ipw2100.

I've read elsewhere that some ieee-something is necessary for WAP authentication with my card, I think, and I did find ieee1394 modules in the modules/kernel/drivers/ directory. Not sure if that helps or not.

I've attached the screenshots of the options I had when the wireless options were available, in case someone needs to see them.

---

### Post by chili555 on 2009-05-09
First, let's see if we can track down the error. Please open a terminal and do:```
sudo cat /var/log/messages | grep ipw
```This will tell us if the kernel has any informational messages or errors concerning *ipw-whatever.*Kernel messages are logged for several days, but we just want the last two. Also, please do:```
dmesg | grep ipw
dmesg | grep eth1
```Thanks.

---

### Post by kdragonracer on 2009-05-10
All right, here's the requested output for the commands you gave me.

sudo cat /var/log/messages | grep ipw
```
May 10 11:24:47 karl-laptop kernel: [   22.419625] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May 10 11:24:47 karl-laptop kernel: [   23.717637] ipw2200: probe of 0000:05:04.0 failed with error -5

```

[There were two other messages I found interesting, as well...
May  3 14:49:28 karl-laptop kernel: [   24.314550] ipw2200: Radio Frequency Kill Switch is On:
May  3 14:49:28 karl-laptop kernel: [   24.398106] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)]

dmesg | grep ipw
```
[   21.186707] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   21.186712] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   22.419625] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.228120] ipw2200: Failed to send TX_POWER: Command timed out.
[   23.350159] ipw2200: Failed to send TX_POWER: Command timed out.
[   23.472118] ipw2200: Failed to send TX_POWER: Command timed out.
[   23.593983] ipw2200: Failed to send TX_POWER: Command timed out.
[   23.715756] ipw2200: Failed to send TX_POWER: Command timed out.
[   23.715762] ipw2200: Unable to initialize device after 5 attempts.
[   23.717559] ipw2200: failed to register network device
[   23.717637] ipw2200: probe of 0000:05:04.0 failed with error -5

```
dmesg | grep eth1
```
[   23.716099] udev: renamed network interface eth0 to eth1
[   55.730546] sky2 eth1: enabling interface
[   61.899004] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by chili555 on 2009-05-10
I wonder if the required firmware is present or getting loaded. Please do:```
locate ipw2200 | grep firmware
```

---

### Post by kdragonracer on 2009-05-11
> **chili555 said:**
> I wonder if the required firmware is present or getting loaded. Please do:```
locate ipw2200 | grep firmware
```
Didn't I check this by hand earlier? Anyway, here's what the terminal returned:
```
/lib/firmware/2.6.24-16-generic/ipw2200-bss.fw
/lib/firmware/2.6.24-16-generic/ipw2200-ibss.fw
/lib/firmware/2.6.24-16-generic/ipw2200-sniffer.fw
```

---

### Post by chili555 on 2009-05-11
> Didn't I check this by hand earlier?Awww, man! Sorry about that. See what happens when a dood gets in a hurry and old?

It's been a while since I worked with Hardy Heron (version 8.04), but I believe in System -> Administration -> Synaptic, there is a package, linux-backports-modules-hardy-generic, or similar, that has a newer ipw2200 module, and maybe firmware, included. I suggest you install it.

I believe your current ipw2200 is not loading correctly unless modprobed and is not correctly loading the firmware, even though it exists.

---

### Post by kdragonracer on 2009-05-12
The only packages I found that looked right were already installed:

linux-ubuntu-modules-2.6.24-16-generic (fw)
linux-image-2.6.24-16-generic (ipw2200.ko)

I can probably find a copy of the ipw2200 stuff online, although I'm not sure if I can compile it (gcc has yet to compile anything correctly)...

---

### Post by chili555 on 2009-05-12
Nothing with 'backports' in the name?

---

### Post by kdragonracer on 2009-05-14
Nothing with "backports" or "backport" comes up when I run a search for them under any of the search fields.

---

### Post by chili555 on 2009-05-14
Please run:```
uname -r
```Find your running kernel version. Match the package download here:

[http://packages.ubuntu.com/search?keywords=linux-backports&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=linux-backports&searchon=names&suite=hardy&section=all)

---

### Post by kdragonracer on 2009-05-14
All right, I ran uname -r and found that I'm running 2.6.24-16-generic, searched through the list of backports packages you pointed me to (thank you!), and downloaded the one for the x386+ architecture, since I have an Intel chip. So the package name is linux-backports-modules-2.6.24-16-generic_2.6.24-16.14_i386.deb and I'm not sure it's the right one, since the file listing didn't have any ipw2200 things that I saw. But I grabbed it anyway.

Rebooted into Ubuntu, transferred the file off the Win drive, and double-clicked to let Package Manager handle the installation. Installation completed, I rebooted, still no wireless. So I tried the modprobe again and rebooted, still nothing. Still no proprietary drivers or anything either. So... do I need to look for a package that has the ipw2200, or does that help you figure out what's happening?

---

