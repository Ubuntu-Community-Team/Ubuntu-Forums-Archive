---
title: "Lost wireless after dist-upgrade"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by graabein on 2006-07-03
I came home for summer vacation and updated to Dapper with Synaptic. After reboot I have no wireless connection. I've been looking at the wiki for wireless troubleshooting but I can't make it out. 

:oops: 

Here is what I think I know so far...

**$ sudo lshw -C network**
*- network
descripton: Wireless interface
product: ACX 111 54Mbps Wireless Interface
vendor: Texas Instruments
physical id: 10
bus info: pci@00:10.0
logical name: wlan0
version: 00
serial: 00:11:95:64:66:47
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
resources: iomemory:e8124000-e8125fff iomemory:e8100000-e811ffff irq:9

this is copied from my Ubuntu 6.06 box on my dads laptop... So the card is recognized and the driver is acx_pci, but when I do...

**$ lsmod | grep acx**
acx  101132 0
usbcore 130692 4 acx,usb_storage,uhci_hcd

it looks like I don't load the driver and...

**$ sudo modprobe acx_pci**
FATAL: Module acx_pci not found.

**$ sudo ifup wlan0**
ifup: interface wlan0 already configured

Running **iwconfig** gives me "no wireless connections" on lo and sit0, but wlan0 gives me IEEE 802.11b+/g+ etc... and **sudo iwlist wlan0 scan** returns two cells.

I'm not certain what I should do next. Is it a problem of loading a driver or is it something else? I have downloaded the ndiswrapper-utils deb from the dapper repositories but I have not installed anything yet. If the driver is okay then what should I do?

Please help! 8-[

---

### Post by Agent86 on 2006-07-03
[QUOTE=graabein] **sudo iwlist wlan0 scan** returns two cells.[/QUOTE]Is one of these cells your regular access point? Can you post the results of the scan? (mask out any sensitive info, of course). Also post the contents of your /etc/network/interfaces file.
> I'm not certain what I should do next. Is it a problem of loading a driver or is it something else? I have downloaded the ndiswrapper-utils deb from the dapper repositories but I have not installed anything yet. If the driver is okay then what should I do?

Please help! 8-[Don't do anything with ndiswrapper unless we can't get the acx driver going. I assume you are not using WPA, right?

---

### Post by blackjack6.21.91 on 2006-07-03
Do you have the network manager installed?  It is available in the repos and I would highly recommend it.  Makes wireless oh so much easier.  Support for your wireless card should not have been lost during an upgrade.

Peace,
blackjack

---

### Post by Agent86 on 2006-07-03
[QUOTE=graabein]**$ lsmod | grep acx**
acx  101132 0
usbcore 130692 4 acx,usb_storage,uhci_hcd

it looks like I don't load the driver and...

**$ sudo modprobe acx_pci**
FATAL: Module acx_pci not found.[[/QUOTE]The ACX driver in Dapper has been renamed from acx_pci to acx, so you are fine, the proper module is loaded. It might just need a firmware change, since some ACX based cards don't like the firmware that loads with Dapper. But let's see the scan results and the /etc/network/interfaces first.
Network Manager is probably not needed unless you roam between access points.

---

### Post by graabein on 2006-07-03
Okay thanks for the answers guys! I've got it working now. I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=206668") and edited */etc/modprobe.d/options* adding **options acx firmware_ver=1.2.1.34** to the bottom. 

After a reboot I had more cells in the scan and I selected our wireless with network-admin. I entered the wep-key and applied changes. I tried **iwconfig** and **ifconfig** and this time I had an IP address which I did not have before.

I followed the troubleshooting wiki again and stepped through the pinging till I got packets from [www.google.com](www.google.com) and voila! Internet!

\\:D/

---

### Post by shockme17 on 2006-07-07
awesome! i had the same exact problem-

you must have a trendnet card?

nice, i to have internet working on my newly up to date system. thanks!

---

### Post by graabein on 2006-07-12
I don't really know what card I have to tell you the truth. I bought it last year and I can't find the box it came in or the receit. I remember checking for GNU/Linux compatible cards before I bought it though. I think it's pretty well known but trendnet don't ring a bell. Sorry about that.

:-k

---

