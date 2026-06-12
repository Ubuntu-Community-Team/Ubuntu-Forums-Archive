---
title: "How do I connect to wireless network with automatic login"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by SESteve on 2011-03-01
I've set up Ubuntu 10.10 on a 64-bit AMD X4 machine. I want to run it as a headless machine on a wireless network. I got an ASUS PCE-N13 installed and working (mostly. It doesn't see my 802.11n network, only the 802.11g but I can live with that). Under Login Screen I have it set to automatically log in as me. But when it does, I get a dialog saying "Enter password to unlock your login keyring". The network connection doesn't get made until after I type in my password. Obviously that won't work if the machine is headless. How can I get the wireless connection made without any intervention?

---

### Post by chili555 on 2011-03-01
> Obviously that won't work if the machine is headless. How can I get the wireless connection made without any intervention?You can remove Network Manager entirely; it's designed for netbooks, etc. that travel down to the coffee shop, library, dorm, etc., and does very fine for that. However, it's an unsuitable tool in your setting:```
sudo apt-get remove --purge network-manag*
```The wildcard * will remove every installed package with *network-manag* anywhere in its name.

Then set up /etc/network/interfaces with your details. Here is an example for WPA2-PSK:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid mylilrouter
wpa-psk mysecretkey

#auto eth0
iface eth0 inet dhcp
```If you are running headless, you probably want a static IP address so you can administer it by ssh:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wpa-ssid mylilrouter
wpa-psk mysecretkey

#auto eth0
iface eth0 inet dhcp

```Be sure to pick an IP address outside the range used by the router's DHCP server. Reboot and you should be all set. Post back if you need further details.

---

### Post by SESteve on 2011-03-02
Thanks a lot for the detailed instructions. I will work on that this weekend.

The SSID of my network has spaces. Will it work to enclose the name in single quotes in /etc/network/interfaces?

---

### Post by chili555 on 2011-03-02
> Will it work to enclose the name in single quotes in /etc/network/interfaces?It sure will:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wpa-ssid[COLOR="Red"] "my router"[/COLOR]
wpa-psk mysecretkey

#auto eth0
iface eth0 inet dhcp
```

---

### Post by SESteve on 2011-03-04
Thanks. I just had to change my gateway to 192.168.1.1 and it all works perfectly.

---

