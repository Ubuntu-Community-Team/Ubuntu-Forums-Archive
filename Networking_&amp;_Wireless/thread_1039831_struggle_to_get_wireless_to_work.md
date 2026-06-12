---
title: "struggle to get wireless to work"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by said76 on 2009-01-14
Hi,

I was wondering if i could get some help with issue of getting the wireless connection to work. There is a wireless Access Point to which i was trying to connect my Fujitsu laptop that runs on Ubuntu 8.04.1. It has a built-in Atheros AR5001X wireless adapter. 

I have also installed madwifi.tools from running synaptic package manager.

The message i received when running 'iwconfig' is

lo      no wireless extensions
eth0    no wireless extensions
wifi0   no wireless extensions
ath0    IEEE 802.11g ESSID:"" Nickname:""
        mode:Managed Frequency:2.437 GHz Access Point:Not-        associated Bit Rate:0 kb/s ......

From the info above, i assume i should be picking ath0 for the wireless connection to establish. However, i do not know how to go about that (sorry, i'm still learning my way around).

I have tried to get into the Network under System-Administration-Network. When the Network Settings pop-up box comes up, there is a wireless connection option under Connection list. I clicked on it and selected properties. I defined Network Name, Password type and chose "Automatic configuration (DHCP)" as configuration for connection settings. Hence, i can not see what else is there that stops it from getting connected.

Any helps would be greatly appreciated.

Thank you in advance

---

### Post by utnubuuser on 2009-01-15
are your wireless networks listed if you click the network icon?  Do you have the drivers enabled in System>>Administration>>Hardware Drivers?

---

### Post by cdtech on 2009-01-15
What do you get with:
```
iwlist ath0 scan
```
And can you bring the ath0 up using:
```
ifconfig ath0 up
```

---

### Post by said76 on 2009-01-15
Thank you for your reply.

> **utnubuuser said:**
> are your wireless networks listed if you click the network icon?  Do you have the drivers enabled in System>>Administration>>Hardware Drivers?

Yes, i can see the 2 drivers in the list and they are 
1. Atheros Hardware Access Layer (HAL)
2. Support for Atheros 802.11 wireless LAN cards

They are ticked with status "in use" at this moment.

Thank you in advance

---

### Post by said76 on 2009-01-15
Thank you for your reply.

> **cdtech said:**
> What do you get with:
```
iwlist ath0 scan
```

i got to see a list of all the wireless available and one of them is mine.

And can you bring the ath0 up using:
```
ifconfig ath0 up
```

No, failed to run this. got the following message

SIOCSIFFLAGS: permission denied

Please advise what to do to get permission granted.

Thank you in advance

---

### Post by cdtech on 2009-01-15
Sorry, you'll have to use the "sudo" command in front.
```
sudo iwlist ath0 scan
```
and the same with the other as well............

---

### Post by said76 on 2009-01-15
Thank you CDtech.

it solved the permission thing with sudo typed in the front. Then, what should i do next?

By the way, i think i should let you know that my Access Point is set to use WPA security encryption. Not sure if this may be one of the reasons why it refuses to connect, though.

I have just upgraded from 8.04 to 8.10 in a bid that the 8.10 would smooth things out for me in terms of wireless connection but it turned out to be the same :(

Is there any packages that need installing?

Thank you in advance

---

