---
title: "&quot;Connect&quot; button not available for wireless authentication"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by dishbert on 2009-12-03
I'm trying to connect to my wireless network from 9.04 booted from a USB drive using the "persistent" option.  

Ubuntu finds the correct network, but the "Wireless Network Authentication Required" dialog box has the "Connect" button greyed out when I'm logged as as Live User.  

I created a new user with Administrator privileges, but when I log on to this user the network notification icon doesn't even show up.  I rebooted and my new user is still available, so I know I'm not just using an install version of 9.04.

What am I missing here?

---

### Post by dishbert on 2009-12-06
So I installed Mint 8 on my USB stick, and I have the same problem.  I've tried iwconfig, still no joy.

There is no sense installing a new version of Linux on my laptop if I can't connect, that's one of the reasons I always try it out with a live CD (and now, better yet, a USB install) first.

Any suggestions would be appreciated.

---

### Post by uncaspi on 2009-12-06
Try to remove all lines except auto lo and iface lo inet loopback in /etc/network/interfaces and then reboot.

---

### Post by dishbert on 2009-12-07
Thanks for the reply uncaspi, my existing default file was exactly as you describe:

auto lo
iface lo inet loopback

I had changed it to specifically point to wlan0, but have since changed it back with no success either way.

I've tried this from another post:

sudo iwconfig wlan0 essid MyNetworkName
sudo iwconfig wlan0 key xxxxxxxxxx
sudo ifconfig wlan0 up
sudo dhclient3 wlan0

But I just get:

DHDCPODISCOVER on wlan0 to 255.255.255.255 port 67 interval 3

repeated 6 times with varying intervals, then:

No DHCPOFFERS received.
No working leases in persistent database - sleeping 

Stumped again!

---

### Post by dishbert on 2009-12-07
I checked the permissions for "root" using the "Users and Groups" dialogue and it was missing check marks for everything, including "Establish Network Connections"  I checked all the boxes and rebooted, but no luck.  I also added a new user to the Admin group and gave it all the permissions but again no luck.

I haven't given up yet, but I'm getting close.

---

### Post by gerbman on 2010-08-14
> **dishbert said:**
> I checked the permissions for "root" using the "Users and Groups" dialogue and it was missing check marks for everything, including "Establish Network Connections"  I checked all the boxes and rebooted, but no luck.  I also added a new user to the Admin group and gave it all the permissions but again no luck.

I haven't given up yet, but I'm getting close.

Did you find a solution to this problem?

---

