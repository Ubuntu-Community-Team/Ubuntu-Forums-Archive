---
title: "Desktop 'gives' Internet to a WM 6.1 device"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by tsoukase on 2009-06-20
Connecting a Windows Mobile v6.1 (WM) Mobile Device (device) with Windows-XP Activesync through USB, the device obtains internet access through desktop's connection, ei a "reverse tethering". There is no such guide for this to happen in Linux. I tried it because my HTC device has neither Wifi nor 3G.
[This]("http://ubuntuforums.org/showpost.php?p=7399890&postcount=55") and [this]("http://ubuntuforums.org/showpost.php?p=5451545&postcount=1") excellent posts explain only how the device gives internet to the Dekstop.

So:

1) the device's remote-NDIS card is set to:
Static IP: 164.254.2.1
Netmask: 255.255.0.0
Gateway: 164.254.2.2

2) when the device is connected in a USB-port, an rndis0 interface comes up in ifconfig 

3) in the desktop:
```
sudo dhclient3 rndis0
```
gives to it the IP: 164.254.2.2.

4) from the dekstop I can ping the device's address 164.254.2.1, but the device itself has no internet access.

How could the mobile "get internet" from the desktop? Any help would be appreciated.

---

### Post by theDaveTheRave on 2009-08-27
tsoukase

from what I can gather from what you are asking, and the information in your post.

1) you can ping your mobile from your pc
2) can't see the internet from you mobile.

I don't suppost you can open a "terminal" and determine what the phone thinks it's equivalent of < ifconfig >  is?

can you set the device to get a "dynamic" IP from your computer? if so you can then set up your desktop as a DHCP server, it will then give the phone an IP address, and tell it the default route to the internet.

From as I understand it you will then need to set up routing tables in your desktop to tell it to pass any requests from the IP addresses it gives out to the internet. This may work without the requirement for setting up the DHCP server - so maybe try it first.

Also the dhclient3 is reporting an IP of 164.254.2.2. whereas the device says it's IP is 164.254.2.1 - i think that may be where the root of the problem lies.

I don't know if this information helps at all? but maybe it will give you some ideas for a solution.

David

---

### Post by lasek101 on 2009-12-01
I was looking for similar solution. I could not manage to go out WM through rndis0 on linux box. It's seems that there is no default gateway on WM - only local network 169.254.2.0. But there is solution simillar to activesync. You have to install all SynCe packages as described on synce page. And after that you have to create partnership  between linux box and WM. Once partnership is created IE on WM can reach Internet.

---

