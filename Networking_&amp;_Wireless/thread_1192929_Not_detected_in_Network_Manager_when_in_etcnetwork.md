---
title: "Not detected in Network Manager when in /etc/network/interfaces"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by wowiesy on 2009-06-20
Hi,

After installing Ubuntu Desktop 9.04 on an Acer 4736z I was able to get wifi working. However, I somehow changed /etc/network/interfaces to have an entry like this:

```
 
auto wlan0
iface wlan0 inet dhcp

```

After rebooting, the Network Manager applet couldn't detect any wifi access points.  However lspci, ifconfig & iwconfig indicated that the wifi was working.  When I did a manual scan (iwlist) it showed the available access points.  So I had to manually set the essid in order to connect.  

Only when I commented out the wlan0 entries in /etc/network/interfaces was NetworkManager again able to automatically detect wifi access points...  

I got it to work yes, but I'm just wondering why it is behaving like this.

---

### Post by kerry_s on 2009-06-20
/etc/network/interfaces overrides network-manager now.

---

### Post by DGortze380 on 2009-06-20
> **wowiesy said:**
> Hi,

After installing Ubuntu Desktop 9.04 on an Acer 4736z I was able to get wifi working. However, I somehow changed /etc/network/interfaces to have an entry like this:

```
 
auto wlan0
iface wlan0 inet dhcp

```

After rebooting, the Network Manager applet couldn't detect any wifi access points.  However lspci, ifconfig & iwconfig indicated that the wifi was working.  When I did a manual scan (iwlist) it showed the available access points.  So I had to manually set the essid in order to connect.  

Only when I commented out the wlan0 entries in /etc/network/interfaces was NetworkManager again able to automatically detect wifi access points...  

I got it to work yes, but I'm just wondering why it is behaving like this.

There is a conflict in 9.04 between Network Manager and the interfaces file.

Use one or the other.

---

### Post by wowiesy on 2009-06-20
Where does NetworkManager read its settings? Where does it save them?

---

### Post by nandemonai on 2009-06-20
> **wowiesy said:**
> Where does NetworkManager read its settings? Where does it save them?

/etc/NetworkManager/

As stated above, from Jaunty onwards you'll need to use one or the other (Network Manager or /etc/network/interfaces file).

---

### Post by Iowan on 2009-06-22
[**gconf**]("http://ubuntuforums.org/showthread.php?t=1190043&highlight=gconf") is another "place" network settings get saved.

---

