---
title: "Wirless, with no GUI"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by danielgroves on 2009-06-04
Hi all,

I have installed Ubuntu Desktop (32-bit) on an old computer, then connected to my home network with the wireless card.  I then proceeded to turn off the GUI in order to create a "server-like" experience, and to save resources on the computer.  

Now I have the problem that I don't seem to be connected to the network anymore!  I have tried the following commands to try and find if I am connected to the network with no real luck.  

```

w3m google.co.uk
w3m: Can't load google.co.uk

```

```

w3m http://google.co.uk
w3m: Can't load http://google.co.uk

```

```

ping google.co.uk
ping: unknown host google.co.uk

```

```

ping http://google.co.uk
ping: unknown host http://google.co.uk

```

Can anybody help me out here?  Thanks! Dan.

---

### Post by Brandon Williams on 2009-06-04
For a server, you would typically want to install a static wireless config in /etc/network/interfaces. Here is a sanitized version of the necessary configuration from my own /etc/network/interfaces file:
```
auto wlan0
iface wlan0 inet static
        address 192.168.1.17
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        wpa-driver wext
        wpa-ssid MYWLANSSID
        wpa-proto RSN WPA
        wpa-pairwise CCMP TKIP
        wpa-group CCMP TKIP
        wpa-key-mgmt WPA-PSK
        wpa-psk MYWLANKEY
        dns-nameservers 192.168.1.1
```
Start with 'man interfaces', 'man ifup', 'man iwconfig', and 'man wireless' to get more information, and then ask more questions if you need more help to get this working.

---

### Post by t0mppa on 2009-06-04
[Here]("http://ubuntuforums.org/showthread.php?t=571188")'s a nice how-to for working without a GUI.

---

