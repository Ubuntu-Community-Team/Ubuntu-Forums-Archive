---
title: "Wireless card undetected after upgrade to 9.10"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by jono_nz on 2010-01-25
Hi! As an introduction to the problem I'm having: For a long time, I've been on 9.04 and my wireless worked quite happily. Then when I upgraded to 9.10, to my despair I found that my laptop no longer detects my wireless driver! Before I go on, I should also say I'm rather inexperienced with Ubuntu in general, despite having used it for quite some time.

Anyway, onto the informational part:
I'm using a Compaq Presario CQ40. 
According to lspci, my wireless network card details are as follows:
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```lsusb shows the following: 
```
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
```I'm not sure if ifconfig here is relevant, but since I'm already following the template for posting these, I'll include it here anyway: 
```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:af:75:15  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:feaf:7515/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4801 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4379567 (4.3 MB)  TX bytes:1004240 (1.0 MB)
          Interrupt:31 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```Now this part is what throws me off: Unfortunately I never checked this when my wireless was working. But common sense tells me that the iwconfig output should not be the case:
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


```As for the module name, I'd include that but I have absolutely no clue if it's there. I'll the entire output of lsmod if needed later on, since it's a bit spammy.

"sudo lshw -C network" gives me the following, and I think it's where I'm having problems:
```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:99700000-99703fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:af:75:15
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:31 ioport:3000(size=256) memory:93410000-93410fff(prefetchable) memory:93400000-9340ffff(prefetchable) memory:93420000-9343ffff(prefetchable)

```If I'm not as inept as I think, the first part is the relevant part. I've gone through the ubuntu forums for the last few days trying to fix this, and I've had limited progress. Initially, it was my Broadcom STA Wireless Driver that was deactivated, and I couldn't reactivate it through System>Administration>Hardware Drivers, citing some kind of error and directing me to a log. I reinstalled bcwm-kernel-source after that, and fortunately now my Broadcom STA Wireless driver is activated. Unfortunately, however, it's "not currently in use". 

I'm not really sure what other information I need to add to this other than the fact that I've been losing hairs over it. With 9.04, I was able to enable/disable my wireless and wired network connections separately when I right clicked on the network icon on the taskbar. But right now, I can only disable the wired connection. 

Please help! I'm getting a headache using my laptop next on my bed instead of having it on a table. D:

Thanks in advance, though. :)

---

### Post by jono_nz on 2010-01-26
Hm, apparently unclaimed means I have no drivers for it. But I've got my Broadcom STA driver installed and activated, but not in use. Not sure how to fix this. :\

Edit: I think the problem may also be related to my wireless kill switch on the keyboard. It usually deactivates/reactivates the wireless card properly, but since my 9.10 install it only enables/disables bluetooth.

---

### Post by bkratz on 2010-01-26
> **jono_nz said:**
> Hm, apparently unclaimed means I have no drivers for it. But I've got my Broadcom STA driver installed and activated, but not in use. Not sure how to fix this. :\

Edit: I think the problem may also be related to my wireless kill switch on the keyboard. It usually deactivates/reactivates the wireless card properly, but since my 9.10 install it only enables/disables bluetooth.

I don't see the STA driver associated with the listings above. Look at this thread and see if it helps.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by jono_nz on 2010-01-26
Hi! Thanks for replying and thanks for the thread. Unfortunately it wasn't of any help :(

However, I'm curious if the wireless toggle button on the keyboard is set to off, is the wireless card is actually detected at all? Because what may be the case here is that whenever I hit the toggle, only the bluetooth turns on/off (and that's working, at least) but the wifi remains off. I'm not sure how to reconfigure that. Prior to upgrading to 9.10, the toggle *did* correctly toggle the wifi, not bluetooth. (In fact, I didn't even realize my laptop had bluetooth till now!)

---

### Post by bkratz on 2010-01-26
> **jono_nz said:**
> Hi! Thanks for replying and thanks for the thread. Unfortunately it wasn't of any help :(

However, I'm curious if the wireless toggle button on the keyboard is set to off, is the wireless card is actually detected at all? Because what may be the case here is that whenever I hit the toggle, only the bluetooth turns on/off (and that's working, at least) but the wifi remains off. I'm not sure how to reconfigure that. Prior to upgrading to 9.10, the toggle *did* correctly toggle the wifi, not bluetooth. (In fact, I didn't even realize my laptop had bluetooth till now!)

I've seen this in some thread before, it may take awhile but I will find it.  It seems like multiple pressing was required--a certain number of times for bluetooth, a different for wireless and again for a combination. Anyway, you might want to check the bios and check the setup there too.

---

### Post by jono_nz on 2010-01-26
Well, from the post in the [link]("http://ubuntuforums.org/showpost.php?p=8661743&postcount=16"), I think I can safely say that my problem here is really to do with my wireless toggle. Unfortunately for me, the bios on my machine (Compaq Presario CQ40, for reference' sake) is extremely limited and I couldn't disable the toggle and force that the wlan be activated. 

I've tried looking for some applications that let you enable/disable wifi and bluetooth so your laptop works in flightmode, but the only one I've come across (KDE Airplane Mode) doesn't look like it works with my laptop.

I've also seen that you can use scripts to disable/enable bluetooth, is there perhaps a way to do this for wifi? I can't really think of how else to force my wifi to turn on, other than perhaps grabbing a usb wifi stick and grabbing other drivers for that.

---

### Post by jono_nz on 2010-01-26
Dang. Well, I just booted into my Vista partition from years ago, and found that my wifi toggle was doing the same thing there, too. Which was weird, because until I installed 9.10, it never did that on either operating systems. Anyway, the only difference here is that with Vista I was able to go to Device Managers and enable my Broadcom wifi from there, enabling me to detect wireless networks. Surely there must be a linux equivalent?

This is especially frustrating when considering the fact that all I need to do is somehow enable my wifi card on Ubuntu, but have no idea how else to do it. :\

---

### Post by jono_nz on 2010-01-27
Bump! Would really appreciate some help with this. It feels like there's an easy solution, since I just need a workaround for the wifi toggle, which only activates and deactivates bluetooth. Surely there's a way to activate wifi through Ubuntu!

---

### Post by texaswriter on 2010-01-27
please delete

---

### Post by jono_nz on 2010-01-27
Well now, I guess I was way off in my understanding of the problem. I disabled the Broadcom STA Drivers, and downloaded b43-cutter and installed the drivers from there. And viola! I have wireless \o/

...I can't believe it took me 3 days to figure this out.

---

