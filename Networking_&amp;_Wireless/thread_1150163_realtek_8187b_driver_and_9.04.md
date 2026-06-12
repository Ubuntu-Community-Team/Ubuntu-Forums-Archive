---
title: "realtek 8187b driver and 9.04"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by feh on 2009-05-05
Hi folks.

I'm running mythbuntu 9.04, but I assume this would be the case for any variant...I'm having problems with a Trendnet 424UB wireless adapter.

It uses the realtek 8187 chipset. The driver (which is part of the 9.04 install - I didn't download anything) seems to be aware of the card. All iwconfig commands work; I can configure the adapter.

The problem is that when I run dhclient, I don't get an address. 

Is this a known problem? How do I troubleshoot the situation?

Thanks!

---

### Post by coffeeaddict22 on 2009-05-06
Hi,
Nice article [here]("http://www.linuxjournal.com/content/troubleshooting-network-problems") from a month ago that might help.

---

### Post by feh on 2009-05-06
> **coffeeaddict22 said:**
> Hi,
Nice article [here]("http://www.linuxjournal.com/content/troubleshooting-network-problems") from a month ago that might help.

Thanks for the link, but this isn't a general "the internet is down" type of problem. It's either a problem w/ the Realtek 8187b driver, or my dhcp client (or the kernel).

---

### Post by coffeeaddict22 on 2009-05-06
if it was the kernel/ driver, iwconfig would be down.  So it's likely your network connections.  what happens when you try to ping?  And what does ```
route -n
``` show?

---

### Post by feh on 2009-05-07
> **coffeeaddict22 said:**
> if it was the kernel/ driver, iwconfig would be down.  So it's likely your network connections.  what happens when you try to ping?  And what does ```
route -n
``` show?

I agree that the kernel/driver is probably ok, since I'm able to configure the interface.

I can't ping anything and the routing table is empty, because dhclient isn't able to get an IP address. I've got other machines on the same network (including another linux machine using the same adapter), so I don't believe it's the wifi router.

---

### Post by coffeeaddict22 on 2009-05-07
So what does iwconfig show?  And what do you get from ```
sudo iwlist scan
```

---

### Post by feh on 2009-05-07
> **coffeeaddict22 said:**
> So what does iwconfig show?  And what do you get from ```
sudo iwlist scan
```

I'm not at the machine now, so I'll have to summarize:

iwconfig shows my wlan0 interface as you would expect on a working system. I set the options manually, using iwconfig commands.

iwlist scan does show a network (with hidden ssid), which is my home network.

Everything looks good on the surface, but dhclient doesn't get an IP address.

---

### Post by coffeeaddict22 on 2009-05-07
Yeah, but what's the driver?  There's been a few issues with wireless drivers not getting picked up right; the clue is that wmaster0 is listed as a link, and it hijacks the working driver; wlan0 ends up with some other driver, often a leftover ndiwrapper or a dummy.

---

### Post by feh on 2009-05-08
> **coffeeaddict22 said:**
> Yeah, but what's the driver?  There's been a few issues with wireless drivers not getting picked up right; the clue is that wmaster0 is listed as a link, and it hijacks the working driver; wlan0 ends up with some other driver, often a leftover ndiwrapper or a dummy.

The wireless network is listed under wlan0 in the "iwlist scan" output. Does that answer your question? 

If not, how would I determine which driver is being used for each interface?

Thanks.

---

### Post by coffeeaddict22 on 2009-05-08
The only place the driver is easily accessible and reliably listed is in ```
lshw -C network
``` Nearly everywhere else you look uses the logical name to categorise the output, so you need to look in lshw to confirm which driver is linked to which logical name.  

Having said that, sometimes you've got to look through the output of ```
lsmod
```to make sure there isn't another driver interfering.  The latest upgrade in particular seems to have created some issues; I think part of the problem is ndiswrapper was needed for many cards in 8.04/ 8.10, and inserting ndiswrapper drivers was a bit of a workaround- so they remain installed when you upgrade, even if the new kernel senses your card and installs the correct driver.

---

### Post by feh on 2009-05-08
> **coffeeaddict22 said:**
> The only place the driver is easily accessible and reliably listed is in ```
lshw -C network
``` Nearly everywhere else you look uses the logical name to categorise the output, so you need to look in lshw to confirm which driver is linked to which logical name.  

Having said that, sometimes you've got to look through the output of ```
lsmod
```to make sure there isn't another driver interfering.  The latest upgrade in particular seems to have created some issues; I think part of the problem is ndiswrapper was needed for many cards in 8.04/ 8.10, and inserting ndiswrapper drivers was a bit of a workaround- so they remain installed when you upgrade, even if the new kernel senses your card and installs the correct driver.

lsmod doesn't show any ndiswrapper drivers.

It's very, very odd. "iwlist scan" finds the wireless network, and iwconfig shows a configured and apparently useful interface. But neither dhclient nor dhcpcd can get an address lease.

I installed kubuntu 9.04 to see if it behaved differently, and it doesn't. Same failure for both kubuntu and mythbuntu.

Here's the output of lshw -C network:

~# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:c0:a8:8c:96:2a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:d1:4b:ff:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c6:2f:61:03:d4:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Desolator64 on 2009-05-08
I'm having problems with this adapter too. Anybody know how to get 8187b working with Kismet/monitor mode?

---

### Post by coffeeaddict22 on 2009-05-08
So exactly _what_ is iwlist scan saying?  Your lshw shows the wlan0 doesn't have a driver- it should be listed in the configuration just like it is for the Ethernet connection, and its not.  So what's iwlist using to scan?

---

### Post by feh on 2009-05-10
I got it working. I had to do two things:

[LIST=1]
[*]shutdown NetworkManager, and prevent it from starting at boot
[*]specify the MAC address of the access point via the iwconfig command
[/LIST]

NetworkManager was messing with the interface (apparently) in the background, as I would see its configuration change through no action of my own. 

I don't know why I have to specify the MAC address of the AP...my SSID is not broadcasted; perhaps that has something to do with it?

Thanks for the help everybody.

---

### Post by coffeeaddict22 on 2009-05-10
network manager does do some messing around.  It might be worth typing into a terminal ```
nm-tool
```This shows you what network manager has had shown to it aw your network interfaces.  Another option is uninstalling it and using wicd; it works for some people but not for others.

---

