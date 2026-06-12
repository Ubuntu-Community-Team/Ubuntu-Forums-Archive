---
title: "No wireless networks appear on Inspiron 6000"
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by jcblegen on 2009-01-13
I have just installed Ubuntu 8.4 on my Dell Inspiron 6000.  At first I couldn't get the wireless indicator to light.  After installing the latest updates, the indicator is now lit, but I still see no wireless networks when I click on the Network Manager icon. Can someone help?

---

### Post by mikewhatever on 2009-01-14
Look under System->Admin->Hardware Drivers for the wireless driver.

---

### Post by jcblegen on 2009-01-14
> **mikewhatever said:**
> Look under System->Admin->Hardware Drivers for the wireless driver.

OK: when I do that I see a Broadcom B43 wireless driver.  Now what?

---

### Post by superprash2003 on 2009-01-14
go to the terminal and type **iwlist scanning** and post output .. also post output of iwconfig

---

### Post by jcblegen on 2009-01-14
Here's the output:

john@john-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

---

### Post by styven on 2009-01-14
> **jcblegen said:**
> I have just installed Ubuntu 8.4 on my Dell Inspiron 6000.  At first I couldn't get the wireless indicator to light.  After installing the latest updates, the indicator is now lit, but I still see no wireless networks when I click on the Network Manager icon. Can someone help?
As I have just mentioned in another thread I too have this problem. I have installed the correct driver and have an indicator light showing that my wireless card is working.
In previous efforts with 8-10 i have manged to connect wirelessly if I turn of any security at the router. However when i activate security the password that i enter gets changed from the router password to to what i think is the hexadecimal (very long) key, hence i cannot connect.
That said even though my wireless card is clearly on, network manager is not showing any available networks as it does in 7-10.
If anyone has any thoughts I am all ears:)
Steve.

---

### Post by superprash2003 on 2009-01-15
hmm..strange.. output shows no wifi networks around.. are you sure you have wifi networks around?

---

### Post by jcblegen on 2009-01-15
> **superprash2003 said:**
> hmm..strange.. output shows no wifi networks around.. are you sure you have wifi networks around?

Yes -- in fact, the laptop is just a few feet away from the wireless router,  and the three Macs in the house all are using that network.

---

### Post by superprash2003 on 2009-01-18
have you enabled the broadcom driver in sys->admin->hardware drivers ?? post output of lshw -C network

---

### Post by jcblegen on 2009-01-18
> **superprash2003 said:**
> have you enabled the broadcom driver in sys->admin->hardware drivers ?? post output of lshw -C network

When I look at the driver in sys-> admin -> hardware drivers it appears to be enabled.  Here's the output of lshw -C network:

john@john-laptop:~$ sudo lshw -C network
[sudo] password for john: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:e4:3c:b2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=172.16.1.49 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:0b:b3:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes 

wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: aa:c7:11:11:a3:d1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
john@john-laptop:~$ 

Thanks for your patience with this!

---

### Post by stgoulash on 2009-05-28
Just wondering if anyone made some headway on this issue, I am also having the exact same problems, followed your trials at fixing it and am unsuccessful.

---

### Post by oniichan on 2009-05-28
Actually the driver does not appear to be activated. Install 'fwcutter' . Enter the command "sudo apt-get b43-fwcutter" in a terminal window. Then logout and log back on again. This should fix it. This is doc'dseveralplaces. Go to the Dell Support topic and search for BCM43xx and tons of help with explanations will pop up.
I also run a Dell Inspiron 6000 with a BCM4311 wireless modem. This should fix you right up.

---

