---
title: "Broadcom 4312/Ubuntu Linux 9.10 64-bit/Lenovo G530 446 35U"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by walkera994 on 2009-11-08
I have a Lenovo G530 4446 35U, using a Broadcom 4312 PCI Card. I'm running Ubuntu Linux 64-bit. I can see wireless networks, but I'm unable to connect to them. Any help is appreciated.

---

### Post by swudee on 2009-11-14
I have a Compaq CQ45 222tx with Broadcom 4312 chipset which worked fine under 32 bit Jaunty, works ok with 64 bit with unencrypted wireless, but while I can get it to connect to WPA2/PSK I could not connect to the net, or ping the router for that matter. I went for a walk, just booted it up and it connected.

I had set it up by left clicking on the wireless signal icon on the top tool bar, selecting VPN Connections, Configure VPN, selecting the Wireless tab, and add.
**Wireless**
Put the SSID name in, mode is set to infrastructure, MTU is set to automatic.
BSSID and MAC address are empty
[B]
Wireless Security[/B]

Security is set to WPA & WPA2 Personal
Password is of course what is set in the Wireless router:)

**IPv4 Settings** 

Set to Automatic (DHCP)
[B]
IPv6 Settings[/B]

Method is set to Ignore

The wireless router is set to:

 WPA2-PSK for wireless security

TKIP+AES for data encryption

Password characters are ASCII for what it is worth.

Why it didn't work this afternoon I don't know,  had done some cold reboots:confused:

Maybe someone will find this useful?

---

### Post by nigamp on 2009-11-14
i ve Broadcom 4312 wireless card.....n after dloading the drivers...cudnt install it properly ....
after the make command completes succesfuly.....the
# modprobe lib80211
# insmod wl.ko
are the nxt ones ..they wont complete....

ne help ?

---

### Post by walkera994 on 2009-11-14
I solved it....somewhat. I downgraded to Ubuntu 9.04. It works perfectly fine on it. Just not on 9.10.

---

