---
title: "Configuring network:  /etc/network/interfaces"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by mjobrien on 2012-12-21
Hi everyone,

I was having problems getting network access (no internet) when connecting my 12.04 HP EliteBook 8540w to my router using an ethernet cable.  I was finally able to connect when I changed my /etc/network/interfaces file from

```

auto lo
iface lo inet loopback

``` 

to

```

auto eth0
iface eth0 inet static
      address 192.168.0.2
      netmask 255.255.255.0
      network 192.168.0.0
      broadcast 192.168.0.255
      gateway 192.168.0.1

```

This was a tip I found somewhere...perhaps on these forums?  Anyways, after going back to wireless, I could not access my router or my NAS (however, I did have internet access).  I could not ping them or anything.  I switched back to the original /etc/network/interfaces file, and was able to access everything again via wireless.  I figured then that having both versions in the same file would allow me to access both wireless and wired connections.  This was not true as I was unable to connect to the router via wireless (I did not try wired).  The original post that gave the tip on how to connect did not explain the different pieces, so I really don't know what I'm doing, and the other explanations I've seen through google have not been terribly enlightening.  What do the elements of this file mean, and how do I get both wireless and wired working?

Thanks so much for any assistance!

---

### Post by AlexDudko on 2012-12-21
First of all, do not remove default two lines
> auto lo
iface lo inet loopback
in /etc/network/interfaces unless there's a specific purpose.

Adding
> auto eth0
iface eth0 inet static
      address 192.168.0.2
      netmask 255.255.255.0
      network 192.168.0.0
      broadcast 192.168.0.255
      gateway 192.168.0.1

you tell the system to automatically enable eth0 interface and to configure it to use a static ip address

You can configure your wireless card to be automatically enabled adding
> auto wlan0
iface wlan0 inet dhcp
dhcp means that the system will be trying to connect to a router and receive ip address and nameserver from it.

Though it would be preferable to use NetworkManager...

---

### Post by mjobrien on 2012-12-21
Thanks for the response!

The reason I was not using the NetworkManager is because I could not get it to detect the eth0 connection.  I tried a few things, and using that interfaces file allowed me to get a connection, though I'm sure there is a better/easier way.  Anyways, continuing on this route, I attempted to use the following interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
      address 192.168.0.2
      netmask 255.255.255.0
      network 192.168.0.0
      broadcast 192.168.0.255
      gateway 192.168.0.1

auto wlan0
iface wlan0 inet dhcp

```

When I restarted Ubuntu, no network connection was made (via wireless).  I have since reverted to the original file, consisting of just the top two lines.  This allows me to access my wireless just fine, but I suspect it will once again fail when I connect to the wired ethernet (I'll verify this later tonight).  So, why does the above interfaces file fail?

Thanks!

---

### Post by Leonidas7 on 2012-12-21
To AlexDudko:

I have a problem: 12.10, ZTE831 as router. My win-vista have network, but I can not to have network in ubuntu. Cable is USB.

---

### Post by steeldriver on 2012-12-21
To bring up a wireless interface via /etc/network/interfaces you would need to add the target ssid and credentials I think, e.g. for WPA personal

```

auto wlan0 
iface wlan0 inet dhcp
    wpa-ssid *mynetworkname     *
    wpa-psk *mysecretpassphrase*

```Obviously you'd want to make sure the file has appropriate permissions to protect your passphrase

FYI there are sometimes issues running both old style networking and network-manager services on the same box

---

### Post by AlexDudko on 2012-12-22
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
There's enough information there on how to manually configure a wireless interface, but mind that you won't be able to easily switch between various wireless networks. To do that you'll have to manually edit  /etc/network/interfaces file and restart network.

---

