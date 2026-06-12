---
title: "Have to ifdown/ifup at boot for wireless to connect, 13.04 Server"
date: 2013-07-14
forum: Networking &amp; Wireless
---

### Post by Jorsher on 2013-07-14
Initially, after installing Ubuntu 13.04, it seemed to connect automatically after a reboot.  Now, it seems like I have to manually ifdown/ifup for it to connect.  The chipset is RT2800 and the router is a Linksys E4200.  I'm using wireless, with DHCP set on the server, and an IP address reserved for the server's MAC on the AP.

The only thing I've done since the fresh installation is:

I checked/installed all updates.

I installed the SSH server.  For some reason, even though I'm certain I chose SSH Server configuration when installing Ubuntu -- it had to be installed manually.

I installed/set up NGINX.

I set up an iptables rule to deny SSH access after a few incorrect password attempts.

Now, when I reboot the server, I have to physically go to it and ifdown/ifup for it to connect.

---

### Post by praseodym on 2013-07-14
Open the file:
```

sudo nano /etc/rc.local
```
and add the lines
```

ifdown wlan0
ifup wlan0
```
_before_ "exit 0". Save with CTRL+X

---

### Post by openlaptop on 2014-06-29
This is a dirty way to fix this.

Better try first to add this line:
***auto wlan0***

In the /etc/network/interfaces file, complete example:
> auto wlan0
allow-hotplug wlan0
iface wlan0 inet manual
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
iface default inet static
address 192.168.0.5
netmask 255.255.255.0
network 192.168.0.0


Wlan0 should now be brought up automatically during boot up.

---

