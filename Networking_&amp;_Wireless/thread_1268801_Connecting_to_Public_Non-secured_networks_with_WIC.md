---
title: "Connecting to Public Non-secured networks with WICD/command line (tip)"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by gaussian on 2009-09-17
This is very short tutorial (might not be considered worthy of one), it is more of an observation that might be helpful for others.

Background: I have two laptops running running Ubuntu (currently Jaunty), one of them dual-booting to Mandriva. I have had in several occasions faced a situation where in a Hotel/Airport/Gym/CoffeeShop my Ubuntu using Wicd (I am not sure if NetworkManager has the same problems) cannot connect to provided non-secure network while my Mandriva using KNetworkManager can.* Only in one occasion I have met a network that Mandriva could not connect to. After extensive Googling I still could not found a solution.

After a pure lucky guess I have recently had  100% success rate in very small sample (3 different non-secured networks) connecting with Wicd or with command line.

**Symptom:** Wicd refuses to connect to a "not secured" network.

**Potential solution:** Choose Connection-Properties, click on "Use Encryption" and choose WEP (Hex[0-9/A-F]). As encryption key choose "0" (type in number zero). Click on connect, and hopefully you are connected soon.

**Command line alternative:** below is an easily modifiable script that connects to a network in a "Drury Inn Hotel" in Kansas City, MO.

```

#!/bin/bash
sudo ifconfig ra0 down
sudo dhclient -r 
sudo ifconfig ra0 up
sudo iwconfig ra0 essid "DruryHotels" key 0
sudo iwconfig ra0 mode Managed
sudo dhclient ra0

```

Note that "ra0" as well as "DruryHotels" will vary depending your situation.

I would be interested in feedback and also interested in potential applicability of this idea to NetworkManager users.


***Note:** I am using Wicd over NetworkManager because in Intrepid NetworkManager had early issues connecting to WEP2 networks (my work, much more important to me). Hardware involved here is Asus EEE 1000 and System 76 Darter (Daru2), but this given the nature of this fix this is irrelevant as far as I can tell.

---

