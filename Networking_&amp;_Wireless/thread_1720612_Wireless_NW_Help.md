---
title: "Wireless NW Help"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by LNNewbie on 2011-04-03
Hi

I have just joined the forum in search of some help for my wireless network that I am trying to set up, I am having problems understanding what steps I need to take but have done the following on recommendation of help from linux forums but am not getting anywhere with what I have done.

PC: Laptop Dell latitude D610
Ubuntu Gnome 2.26.1

I currently have a wired connection to my laptop but am trying to set up wireless, I have put the antenna on the router and have a wireless network showing called NETGEAR, amongst others, which is my primary router name so i'm trying to connect to that but the actual wireless antenna is on the switching hub. For all intents and purposed assume I am a complete newbie with ubuntu and linux command line stuff, I know basics like pwd, ls and so on but need a good bit of help trying to do this.

When I click on this wlan network NETGEAR I get asked for the password, on the bottom of the switching hub is a code for WLAN and I put this in, it then asks for a password for a default keyring, which I do not know. How do I find this out?

But I am still not sure what I am supposed to be doing or looking for to resolve this connection problem, not only am I not a network expert I have no knowledge of linux either and would really appreciate some help and steps to follow to establish a connection.

> sudo iwlist eth1 scanWhich gives this:

```
Cell 04 - Address: 00:1F:33:01:63:20
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-68 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1216ms ago
```Thanks

LNNewbie

---

### Post by bkratz on 2011-04-03
> **LNNewbie said:**
> Hi

I have just joined the forum in search of some help for my wireless network that I am trying to set up, I am having problems understanding what steps I need to take but have done the following on recommendation of help from linux forums but am not getting anywhere with what I have done.

PC: Laptop Dell latitude D610
Ubuntu Gnome 2.26.1

I currently have a wired connection to my laptop but am trying to set up wireless, I have put the antenna on the router and have a wireless network showing called NETGEAR, amongst others, which is my primary router name so i'm trying to connect to that but the actual wireless antenna is on the switching hub. For all intents and purposed assume I am a complete newbie with ubuntu and linux command line stuff, I know basics like pwd, ls and so on but need a good bit of help trying to do this.

When I click on this wlan network NETGEAR I get asked for the password, on the bottom of the switching hub is a code for WLAN and I put this in, it then asks for a password for a default keyring, which I do not know. How do I find this out?

But I am still not sure what I am supposed to be doing or looking for to resolve this connection problem, not only am I not a network expert I have no knowledge of linux either and would really appreciate some help and steps to follow to establish a connection.

Which gives this:

```
Cell 04 - Address: 00:1F:33:01:63:20
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-68 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1216ms ago
```Thanks

LNNewbie

Welcome to the forums.  the keyring is asked for since you probably have it set not to require a password when logging in; it is for your protection but a quick googlubuntu.com search will show you a way around that too. For now though it should be just your normal password.  Anyway, do you have an icon for the connection at the top of the page?  If so and you right click on it you should be able to setup your connection there, just make sure you have a check mark in the wireless box, then edit the contents. here is a good starting point though.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

