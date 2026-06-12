---
title: "Wireless suddenly fails, networks still visible"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by ovis23 on 2011-05-19
I'm having a problem with my wireless, and after searching the forums for a couple of hours, I suspect it's time to speak up.

This morning, wireless was up and working fine on several networks. My laptop froze around noon, and I was forced to do a hard reboot. After restarting, the Network Manager will not connect to any wireless networks, which are visible. Wired connections work fine. I've tried multiple networks, and although I can see them, I cannot connect.

I've tried using Wicd, so it's not a NetworkManager problem, and I've tried connecting manually. If I try the routine in [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) and type:
```
sudo dhclient wlan0 -v
```I get the following:
```
Listening on LPF/wlan0/00:22:fb:51:ba:62
Sending on   LPF/wlan0/00:22:fb:51:ba:62
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```I've tried unloading and reloading the wireless drivers (iwlagn) and rebooting a couple of times.

Here are the details:
Ubuntu 11.04, 64-bit. Network adapter is an Intel 5100.

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"######"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```Network interfaces in /etc/network/interfaces only included
```

auto lo
iface lo inet loopback
```but I tried adding 

```

# Primary network interface
auto eth1
iface eth1 inet dhcp
```with no luck.

I reiterate - it worked fine before a forced reboot. Is there anything that may have been corrupted that I could reset?

Any ideas? This is mission-critical enough for me that I'm considering reinstalling Ubuntu from scratch if I can't get this fixed quickly.

---

### Post by ovis23 on 2011-05-21
I now have it narrowed down to only happening at the one router. Other people can connect fine, and inserting an 11.04 boot USB and trying to connect (which has worked in the past) doesn't achieve anything.

Given that I can use wireless elsewhere, is the router perhaps storing information about my computer that prevents connecting? Other routers on the same network do work for me, so it's not like I've been intentionally blocked.

I'd be really curious to know what's going on.

---

