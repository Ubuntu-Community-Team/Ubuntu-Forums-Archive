---
title: "Share Internet Connection (Ubuntu Server)"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by mikemhz on 2012-11-18
I have Ubuntu Server on an old laptop.
It connects to my router via wifi.

**/etc/network/interfaces **
```
auto eth1
iface eth1 inet dhcp
    wpa-ssid <ESSID>
    wpa-psk <password>
```

It has an Ethernet port (eth0) to which I've connected a Windows 8 box with no internet. I want the internet on the Windows box.

This is easy using Ubuntu or Windows GUI. But how do I achieve this by command line? I've worked on this for three days with no results.

---

### Post by ahallubuntu on 2012-11-18
Try this:

[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

---

