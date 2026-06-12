---
title: "Dell B130 - Broadcom Wireless"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by Jerim on 2006-06-05
I just tried posting this but I don't think it went through. I have spent over a week trying to find the solution to no avail.

My problem is that Ubuntu automatically loaded my wireless card as eth1. I don't know if that is an issue or not. I can activate the eth1 card and setup the ssid, but device never appears in the gateway list. I can't use it. If I do dmesg, this is what I get:

4294782.850000] SoftMAC: Authentication response received from 00:11:50:8d:e9:6e but no queue item exists.
[4294871.850000] SoftMAC: Authentication response received from 00:16:6f:16:f6:5b but no queue item exists.
[4294871.858000] SoftMAC: Authentication response received from 00:11:50:8d:e9:6e but no queue item exists.
[4294871.874000] SoftMAC: Authentication response received from 00:11:50:8d:e9:6e but no queue item exists.
[4294871.876000] SoftMAC: Authentication response received from 00:11:50:8d:e9:6e but no queue item exists.
[4294871.892000] SoftMAC: Authentication response received from 00:11:50:8d:e9:6e but no queue item exists.
[4294871.908000] SoftMAC: Authentication response received from 00:11:50:8d:e9:6e but no queue item exists.
[4294871.909000] SoftMAC: Authentication response received from 00:11:50:8d:e9:6e but no queue item exists.
[4294871.924000] SoftMAC: Authentication response received from 00:11:50:8d:e9:6e but no queue item exists.
[4294871.926000] SoftMAC: Authentication response received from 00:11:50:8d:e9:6e but no queue item exists.
[4294881.115000] ADDRCONF(NETDEV_UP): eth1: link is not ready

I have tried to use the ndiswrapper method to get the card installed. However, it will load the driver, but the device never shows up in the networking panel. If I do lspci this is what I get:

0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Also, networkmanager-gnome isn't working. At bootup it tells me some the components are missing. I have tried reinstalling with the same results.

Any help is greatly appreicated. I am not sure if I need to remove eth1 first and if so, how. I am willing to provide any information that is needed.

---

### Post by Jerim on 2006-06-06
Here is what my /etc/network/interfaces looks like:

auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid Office

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by Jerim on 2006-06-06
I get this error on bootup everytime:

*The NetworkManager applet could not find some required resources. It cannot continue. *

I have tried remoging networkmanager and networkmanager-gnome and reinstalled them. Same error.

---

### Post by Jerim on 2006-06-06
Here is what iwconfig shows me:
[I]
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Yount"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
[/I]

I believe the wirelss card may be working. The light on the laptop for wireless is lit up. I just can't seem to set my gateway device to be eth1. It doesn't show up in the list. I also can't seem to get the wireless utilities to work.

---

### Post by Jerim on 2006-06-07
Okay, I saw wifi-radar mentioned elsewhere. I tried it and was suprised to see that it actually finds the local wireless connections. So we know Ubuntu is communicating with the wireless card, how else would wifi-radar know what the local wireless networks are named?

Something I find odd though is that when I try to connect to a wireless network using wifi-radar, it will connect, but I get no IP address. I have tried using static and assigning and IP address from the proper range. Yet it still doesn't get an IP address. 

Another think I am noticing, is that when I connect to a wireless connection, it disables the wireless card in the network management panel. The card is working, because the light is on and I am connected to something. But it just shows not active in the network panel.

---

### Post by MarkSheely on 2006-06-07
I'm having the same problem, using wifi radar - it connects, but acquires no ip address.  I'm stumped for now, but will keep working on it and let you know what I come up with.

Btw, we are using the same laptop.  I had my wifi working several hours ago at a different location at my university.  Not sure why it would suddenly stop working when changing locations -

--Mark

---

### Post by Jerim on 2006-06-08
One trick that worked for me a while back, on a different laptop, with a different  distro of Linux, was to set the mac address of my wireless card in my wireless router. It seemed to really help if the router knew what piece of hardware it is looking for.

I haven't tried that yet, but will try it the first oppurtunity I can.

---

### Post by MarkSheely on 2006-06-08
Alright, I got my wireless working -  try the instructions here if you haven't already:

[http://ubuntuforums.org/showpost.php?p=1085392&postcount=55](http://ubuntuforums.org/showpost.php?p=1085392&postcount=55)

I did a clean install and followed the instructions in the post above.  Now my wireless is working without a hitch,

(I also starting using Wifi-radar, which helped a great deal).  

Let me know if you have already done this or if it doesn't work, and we'll try something else.  

Good luck,
Mark

---

### Post by shousonhill on 2006-08-30
Hey guys, I had all of these problems w/ no success.

I am using wifi-radar and I tried changing the channel and mode just for shits and giggles.  I tried Channel 1 instead of Auto.  What do you know, it works for the moment.  Hopefully it will continue to.

---

