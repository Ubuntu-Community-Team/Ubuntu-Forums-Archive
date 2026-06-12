---
title: "nd of my rope/sanity with wireless broadcom w/8.10"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by scearley on 2009-03-24
I have scoured he solutions here on the boards to get wireless working on this HP Pavilion zv6000.

I did a full, complete installation, so I do not have the broadcomm drivers to use from Windows via ndiswrapper.

but apparently everyone has success with the b43xx installation, which I tried. I did this via System > Administration > Hardware drivers, I did it via manual copy from a link in another thread here, and I tried it using package manager.  in each case, it resulted in the wifi button lighting but doing nothing else.

iwconfig results:
```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig results:
```
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:6b:db:8f  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe6b:db8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:881240 (881.2 KB)  TX bytes:148629 (148.6 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:ac:04:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-AC-04-DD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
I'm sure there are other results which might help but I can't think of useful commands right now after beating my head against this problem literally the entire night.

The ethernet connection works, and I'm using it now.  When I go to System > Preferences > Network Configuration, nothing shows up for wireless.

At this point what I really want to know is why it seems to be working for every other person (it seems) who installed 8.10 on a Pavilion zv6000 but not ME.  My frustration is so enormous with this, at this point I don't know if installing ubuntu was the right thing.

I have been running Kubuntu on my JVC subnotebook and my desktop for about a year now...this is my girlfriend's computer.

---

### Post by jpalmisa on 2009-03-24
have you seen these?

[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

I know they are for older versions, but maybe something in there might help. I tried to attach the drivers to this response, but the forum wouldn't let me... if you still need the win drivers for ndiswrapper then send me email through this forum...

---

### Post by scearley on 2009-03-24
Thanks.
Link 2 is just instructions on how to install the b43 stuff, which I already have installed.
Looking towards the end of the first link, a number of people using computers similar to this one state it doesn't work using those parameters, and no additional help comes from there.  I may try it later if I can't find some other method.

Though this brings up a different question:  Are the broadcom windows drivers different between 32 and 64 bit systems?  The computer I am using is a 64 bit.

---

### Post by scearley on 2009-03-24
I ended up using [this thread]("http://ubuntuforums.org/showthread.php?t=870086") to try to work with ndiswrapper and after going through all of the steps, including building ndiswrapper, it [did not work]("http://ubuntuforums.org/showpost.php?p=6947879&postcount=271").

It seems I have absolutely no recourse here.  No?

output of lshw -C network:
```
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:6b:db:8f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.2 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:ac:04:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 0e:7c:3f:0b:89:0e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I added b43-pci-bridge to the blacklist and it's still listed.

---

### Post by Ayuthia on 2009-03-25
Can you post the results of:
```
sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg|grep ndiswrapper
```
This will remove the possible wireless modules and then load ndiswrapper.  The last part will check and see if any error messages pop up.  If I recall correctly, the 4306 rev 03 driver that is suggested from that site only worked with the 32-bit and not 64.  It is possible that the drivers in steps 2a and 2b might work.

---

### Post by scearley on 2009-03-25
> **Ayuthia said:**
> Can you post the results of:
```
sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg|grep ndiswrapper
```
This will remove the possible wireless modules and then load ndiswrapper.  The last part will check and see if any error messages pop up.  If I recall correctly, the 4306 rev 03 driver that is suggested from that site only worked with the 32-bit and not 64.  It is possible that the drivers in steps 2a and 2b might work.

```
[   27.869191] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   27.965044] usbcore: registered new interface driver ndiswrapper
[  217.826866] usbcore: deregistering interface driver ndiswrapper
[  228.311913] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  228.911348] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  228.911361] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwl5'
[  228.914074] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwl5; check system log for messages from 'loadndisdriver'
[  228.914185] usbcore: registered new interface driver ndiswrapper

```

I'm no sure where to find the systemlog otherwise I'd post the relevant section as well.  based on the 5th line of the results I posted above, it looks like the issue is the driver, which you astutely already anticipated.

I know I'm reading into your reply, but since bcmwl5 is not working, I'm going to go ahead and try steps 2a and b.  Thank you!

ADDITIONAL
I went through step 2a (and then 3), which did not work, then went through the listed method of [installing a new driver]("http://ubuntuforums.org/showpost.php?p=3767216&postcount=273") and then went through 2b (and 3).

Neither worked - wireless is not even functional now (the LED is no longer lit, as it was previously), lshw -C network displays that the wireless is still using the b43-pci-bridge driver and module=ssb.

Does this mean a 64-bit OS is not possible?  I don't want to go through everything with removing the 64-bit an reinstalling the 32-bit if it means the wifi still won't work.

---

