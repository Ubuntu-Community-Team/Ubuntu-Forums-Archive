---
title: "Wireless N speeds?"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by AcidRain0 on 2009-09-01
Hi guys, I have a Wireless WiFi Link 5100 using iwlagn,iwlcore,mac80211 modules and i'm using gnome's network manager to connect to my network. I have wireless N and can use it on this laptop when i'm booted into windows (dual boot) and I can't seem to get the wireless N speeds while i'm in ubuntu. Does it not support N speeds or am I doing something wrong?

---

### Post by t0mppa on 2009-09-01
Some drivers don't automatically pick the quickest Bit Rate available when connecting, so check the following: after connecting to your network, open up a terminal and run **iwconfig** and check the Bit Rate setting, if it's lower than what you require, you can use **sudo iwconfig <interface_logical_name> rate xxxM** to update it to use higher rates.

---

### Post by AcidRain0 on 2009-09-02
> **maherjimmy said:**
> Hi Everyone..

I have a new IBM ThinkPad with an Intel Pro 2100 LAN card installed.  I use a  
Linksys Access Point and have sucessfully connected a desk top to  
the wireless network.  However, the laptop will not connect.  I tried using  
Windows to connect, but the network appears to be a conflict with the wireless card.  In the Network Connections  
It shows "Not Connected". The ipconfig shows Media disconnected.  IBM has  
replaced the card and the motherboard, but still no connectivity. I disabled  
the security on the access point but still no connectivity.  The error  
message says "waiting for IP configuration" when I try to connect. 

Anyone with any ideas?

why are you hijacking my thread?



anyways.. i tried that, the highest i can get up to is this "iwconfig wlan0 rate 60M", anything higher and it says 'Error for wireless request "Set Bit Rate" (8B20)'

help?

---

### Post by t0mppa on 2009-09-02
You cannot use it to pick arbitrary rates. Try running **sudo iwlist scanning** first and then see the bit rates your AP is providing and try changing into one of those. For instance, my AP (only 802.11a/b/g), gives the following rates (and trying to set anything between them will give the same error message as you had):

```
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
          9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
          48 Mb/s; 54 Mb/s
```

---

### Post by Elfy on 2009-09-02
> **AcidRain0 said:**
> why are you hijacking my thread?



anyways.. i tried that, the highest i can get up to is this "iwconfig wlan0 rate 60M", anything higher and it says 'Error for wireless request "Set Bit Rate" (8B20)'

help?

sneaky spam - post and come back later with spam in their sig :(

---

### Post by AcidRain0 on 2009-09-04
Hm.. this makes no sense. Do I have to do something to enable the N speeds?

On my N network it says this:
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s                              36 Mb/s; 48 Mb/s; 54 Mb/s



And you can see it's the higher freq. one so it should be fast
                    Frequency:5.805 GHz (Channel 161)

---

### Post by threetwoone on 2009-09-11
You should check on you routers configuration page (some say what speed you're connected at).  I was getting the same thing when I looked at the bit rates for my router, but when I looked at the router's page it said that I was getting over 100 Mb/s.  I'm also using iwlagn but with intel 4965 ag(n).  I'm not sure but your card may be newer than mine so if you are not connected at N speeds it might just be a matter of time.

What I think is happening is that some of the networking tools haven't been fully updated to incorporate wireless N and others are showing it in a strange way, for example network-manager only shows my connection as high as 60 Mb/s.  I guess what I'm trying to say is, wireless N support is still being worked on so things like this are to be expected.

---

### Post by zackiv31 on 2009-10-06
@threetwoone

I have the same wireless card and iwlist is only showing 54 max (network manager the same, although I swear I've seen 60 at some point).

Same machine, booted into windows 7 is showing 130... so is it as simple as you say that it is connecting at these higher speeds and the tools just aren't smart enough?

---

### Post by thecow on 2009-10-06
Ubuntu seems to have problems with N speed.  Seems like a problem that needs to be addressed, especially with the release of Windows 7 fairly soon.  Its been a problem for a long time now though

---

