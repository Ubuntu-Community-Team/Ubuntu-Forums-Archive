---
title: "Ubuntu Server Can't Connect to Wifi"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by Diracian on 2013-04-30
I just installed the Ubuntu 12.04 server edition, and everything went great. I wasn't able to configure the DHPS thing (or what ever it was, it was that thing that popped up that wanted me to configure my network). I don't have internet on it as a result, so the apt-get function doesn't work so I can't install anything. 

I have nothing installed on it right now other than what it came with (I did not check any of the boxes which had pre-installed software); so no editors like gedit. 

How do I get wifi working on my machine so that I can use apt-get install?

---

### Post by ahallubuntu on 2013-04-30
~

---

### Post by steeldriver on 2013-04-30
For a server, you can define the interface in your /etc/network/interfaces file - the details will depend on your interface name (wlan0, wlan1 or whatever) and whether you want to set up DHCP or static addressing - here is a simple template for a WPA-PSK connection on wlan0 with DHCP and the LAN router (192.168.1.1) providing name resolution:

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid *your-ssid*
    wpa-psk *your-passphrase*
dns-nameservers 192.168.1.1

```

---

