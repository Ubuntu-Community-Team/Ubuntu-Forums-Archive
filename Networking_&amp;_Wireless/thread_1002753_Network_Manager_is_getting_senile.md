---
title: "Network Manager is getting senile"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by pwaldo on 2008-12-05
Hi all,

I'm running Ubuntu Intepid on a Dell Laptop.  When I first installed it, I had all of my networking working fine.  I had an OpenVPN connection to my internal network running over WiFi, as well as my AT&T Wireless Network card was working flawlessly.

As time passed (and maybe as updates were applied), Network Manager has been going senile.  Now when I try to get the VPN working, it tells me "No VPN configuration options" in syslog and won't connect.  

Also, when I plug in my AT&T Wireless card, syslog tells me it has loaded the driver (hso.ko) and "ifconfig hso0" shows an unconfigured interface.  NetworkManager is supposed to take over at this point when I tell it to connect.  Even though I have the Mobile Broadband connection defined, I get no option to use the card, so cannot get the hso0 interface up.

I'm going crazy, here.  Any help would be hugely appreciated!  Thanks in advance.

Paul

---

### Post by pwaldo on 2008-12-05
OK, this really starting to get crazy.  My laptop has a key combo that enables or disables the WiFi and Bluetooth.  If I turn it on, I start getting all kinds of error messages in syslog, then something (NetworkManager I'll bet) starts grabbing all the memory it can.  The system ends up becoming unusable due to the high amount of swapping.

I'm wondering if nuking all of my NetworkManger configuration and starting fresh will resolve the problems.  Any idea of how to start afresh?  Thanks!

---

