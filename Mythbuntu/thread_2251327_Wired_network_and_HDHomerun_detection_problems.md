---
title: "Wired network and HDHomerun detection problems"
date: 2014-11-03
forum: Mythbuntu
---

### Post by joe145 on 2014-11-03
I have wifi and wired networks on my mythbuntu box. The box is both fronttend and backend.

The machine sees the world via the wifi connection. The eth0 interface is my wired network, but the only item on that wire is the hdhomreun device. There is no router, and no internet.

But, hdhomerun_config discover returns 'No device found'.

This same setup works just fine when the machine is booted into Windows: the HDHomerun is detected and OTA signals are found and tuned to, and TV programs are recorded.

What can I do to make it work in Mythbuntu? (I'm on 14.04)

Thanks!

---

### Post by TheFu on 2014-11-03
HDHR (at least the versions I have) default to an odd network unless you setup DHCP reservations in the router.  Since you don't have a router ... er ...   you'll need to ensure the eth0 subnet is the same as what the HDHR uses.  Normally I document stuff like this, so I don't have to relearn it later - sorry - for me, it was just easier to setup DHCP reservations for any difficult-to-manage network devices on my internal LAN.  While it won't help you ... [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) should help lurkers with the same issue.

I think the HDHR is on a 169.x.x.x subnet (but don't quote me).

---

### Post by mathog on 2014-11-03
> **joe145 said:**
> I have wifi and wired networks on my mythbuntu box. The box is both fronttend and backend.

The machine sees the world via the wifi connection. The eth0 interface is my wired network, but the only item on that wire is the hdhomreun device. There is no router, and no internet.

But, hdhomerun_config discover returns 'No device found'.

What does ifconfig show?  For all we know eth0 doesn't have any kind of an address.

Out of the box ubuntu is going to expect a dhcpd server running on that wired network, and that it will be able to figure out eth0's network address from that.   Since there is no such thing you are going to have to set it up some other way.  It might fall back to something like avahi - not sure, I never use that.   If I had to guess it would be that Windows used some sort of zeroconf implementation like avahi to discover and talk to the hdhomerun, and that Ubuntu is either not running one, or the configuration is not right.

If it were my machine I would start by manually setting an address and mask for eth0.  Check the hdhomerun documentation to see what subnet/addresses it will use if it cannot find a dhcp server, and use something compatible.  Here is an example 

sudo ifconfig eth0 192.168.2.5 netmask 255.255.255.0 broadcast 192.168.2.1

192.168 is probably correct, but the hdhomerun might use 0 or 1 instead of 2 for the expected subnet.  Be sure eth0's address is not the same as the default hdhomerun.  You could have a problem if your home wifi network happens to use 192.168.0.xxx and the hdhomerun also wants to use that.

Anyway, for a first pass, try the sudo line above, then run "hdhomerun_config discover" and see if the device turns up.

---

### Post by TheFu on 2014-11-03
The default HDHR IP is on that same network that MS uses if no DHCP server is found and no static IP is manually configured. Think it is a 169.x.x.x.  If you boot Window and run **ipconfig /all** and look for the wired NIC that will be the subnet you need for Ubuntu.

169.254/16 ---- according to [http://www.ietf.org/rfc/rfc3927.txt](http://www.ietf.org/rfc/rfc3927.txt)

---

### Post by dannyboy79 on 2014-11-03
are you using a regular ethernet cable or a cross-over cable? im guessing you're having a problem because the utility maybe can't determine the subnet you're on. maybe this thread will help? [https://www.silicondust.com/forum2/viewtopic.php?f=21&t=17966](https://www.silicondust.com/forum2/viewtopic.php?f=21&t=17966)

---

