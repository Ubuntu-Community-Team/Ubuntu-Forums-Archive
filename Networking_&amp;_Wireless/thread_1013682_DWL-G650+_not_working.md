---
title: "DWL-G650+ not working"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by lapp on 2008-12-17
I've been doing a lot of reading and a whole lot of experimenting in trying to get a DWL-G650+ (rev b) PCMCIA card working on an Asus laptop running an install of Intrepid 8.10.

It seems the that ACX111 compatibility changes with every revision of Ubuntu so im not sure whether to keep troubleshooting it using guides written for previous revisions, as i can't find anything regarding my wifi adapter for Intrepid.

When i plug the card into the laptop, it is detected by Ubuntu but i can't do anything with it.

IWCONFIG shows the card as being Wlan0 with the nickname "acx v0.3.36"

When i attempt to connect to my wireless network i get an error;

```

iwconfig wlan0 essid "Home Sweet Home"
Error for wireless request "Set ESSID" (8B1A)
      SET failed on device wlan0  ;  Operation not permitted.
```


I can only assume the Intrepid ACX111 driver is still a little fubar with the DWL-G650+



Has anyone had any success with this card and Intrepid?

---

### Post by angelmartinezn on 2008-12-17
Have you got installed 'linux-restricted-modules' ?

I think you will also need 'madwifi' packages...

can you show us what 'dmesg' shows when you put in the card?

I have this card working, but in an old laptop with ubuntu 7.04

---

### Post by lapp on 2008-12-17
linux-restricted-modules is for Atheros based cards isn't it? This card is ACX111.

Still can't get it to work properly :/

---

### Post by Joe2Shoe on 2008-12-17
I have that same card, running Intrepid Ibex v8.10
No problems here.
Here's my configuration info.
Hope this helps.

This is an Atheros chipset based card!!

Wireless Card info



D-Link DWL-G650 AirPlus ExtremeG PCMCIA Card
 (rev. B)


WLAN connection information



Interface: 802.11 WiFi (ath0)

Hardware Address: 00:xx:xx:xx:xx:xx (changed here for security reasons)

Driver: ath_pci

Speed: 54 Mb/s

Security: WPA/WPA2



IP Address: 192.168.11.3

Broadcast Address: 192.168.11.255

Subnet Mask: 255.255.255.0

Primary DNS: 192.168.11.1

---



HOW TO EDIT CONFIGURATIONS OF WIFI CARD:



In the top-right of the screen, right-click the "Network Manager" icon (the signal strength bar).

Left-click on "Edit Connections".



Click the "Wireless" tab

Click your network's name, then click "Edit".



Connect automatically: is Checked

System setting: is not Checked



Under the "Wireless" tab

SSID: name of network

Mode: Infrastructure

BSSID: blank

MAC address: blank

MTU: automatic



Under the "Wireless Security" tab

Security: WPA & WPA2 Personal (or whatever type of encryption you used on your wireless router).

Password: xxxx



Under the "IPv4 Settings" tab

Method: Automatic (DHCP) or Automatic (DHCP Address only)



Save/Exit.

Try connecting again.



Addresses section

Address: 192.168.11.3

Netmask: 24

Gateway: 0.0.0.0

DNS Servers: 192.168.11.1

Search Domains: blank

---

---

### Post by Joe2Shoe on 2008-12-17
Pardon my oversight on my earlier post as your card does use the ACX111 chipset.

Here's a direct Ubuntu link on configuring your specific card.

[https://help.ubuntu.com/community/WifiDocs/Device/DWL-G650%2B](https://help.ubuntu.com/community/WifiDocs/Device/DWL-G650%2B)

---

### Post by Condillac on 2009-04-26
Hello,

it works but it needs wicd (and linux-restrited-modules) instead of Network-Manager.

---

### Post by Ryuhayabusa on 2009-05-05
has anybody managed to get the 5212 chipset working in WPA enterprise PEAP TKIP MSCHAPV2 ?

---

