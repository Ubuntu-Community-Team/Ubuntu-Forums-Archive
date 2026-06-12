---
title: "enable wireless from command line"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by jt_04 on 2009-04-11
Hello,

I desperately need a way to enable my wireless connection from a command line **WITHOUT the X server running**.  

I have tried to run nm-applet but it obviously requires a display manager.

surely someone has done this before?  please help

thanks in advance

---

### Post by davidgurvich on 2009-04-11
The graphical wireless tools have only recently (3 years) become usable.  Before that one configured a wireless card with some combination of iwpriv, iwconfig, ifconfig, dhclient, and wpa_supplicant.  All of these still work. Here's a simple way to configure a wireless interface called eth1 for a wep connection using dhcp with a combination of commands.```
ifconfig eth1 up
iwconfig eth1 essid "ESSID_NAME" key 1010101010
dhclient eth1
```That brings up the interface, set's the association with a wep encrypted access point called "ESSID_NAME" that uses a hexadecimal key of "1010101010" and assigns dhcp addresses to clients.  You get the dhcp address with dhclient.

---

### Post by jt_04 on 2009-04-13
thanks very much for the help david.  when i try those commands, it fails when getting the dhcp address and outputs this:

> wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:1f:37:91:a3
Sending on   LPF/wlan0/00:1f:1f:37:91:a3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

any ideas?

thanks,
jt

---

