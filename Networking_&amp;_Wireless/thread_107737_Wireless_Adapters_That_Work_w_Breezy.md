---
title: "Wireless Adapters That Work w/ Breezy?"
date: 2005-12-23
forum: Networking &amp; Wireless
---

### Post by BitTorrentBuddha on 2005-12-23
Does anybody know any internal wireless adapters that will work with minimal effort with breezy?

---

### Post by fordfan753 on 2005-12-23
Usually intel w2200 (spell check)

---

### Post by BitTorrentBuddha on 2005-12-23
PCI, sorry forgot to mention that lol

---

### Post by Lambert on 2005-12-23
Fordfan meant any minipci card based on the ipw2200 chipset.

Here is a list of minipc cards and their general support in linux. 

[http://linux-wless.passys.nl/query_hostif.php?hostif=mini-PCI&zoek=hostif](http://linux-wless.passys.nl/query_hostif.php?hostif=mini-PCI&zoek=hostif)

You can cross this with this list

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards#head-58b882a4bf3f313aa4d1a37829bcb143958f8011](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards#head-58b882a4bf3f313aa4d1a37829bcb143958f8011)

And there is little telling what will happen. It's possible you'll get a card with a little newer chipset with some minor changes that make it incompatable with drivers in breezy.

I personally reccommend anything with atheros chipset but there are success stories with intel 2200 based cards and others.

---

### Post by WildTangent on 2005-12-23
My MSI card (based on Ralink 2500 chipset) worked out of the box. I think any Ralink based card will work, but don't quote me.

-Wild

---

### Post by BitTorrentBuddha on 2005-12-24
Thanks very much for the wiki, that was a big help :)

---

### Post by cloudy2 on 2005-12-25
[QUOTE=WildTangent]My MSI card (based on Ralink 2500 chipset) worked out of the box. I think any Ralink based card will work, but don't quote me.

-Wild[/QUOTE]
Mine did, but it did not STAY working. Even though it worked at first and works perfectly in Windows, it only works sporadically in Ubuntu. It is an older card -rt2400. Rest of info is in my last thread....

---

### Post by tktreload on 2005-12-25
also chipsets that are produced by atheros especially the 5212 chips work with the standard linux-restricted-modules.

---

### Post by BitTorrentBuddha on 2006-01-13
Ok, i got a TrendNet that, according to the wiki, should just work, it's not just working, and I feel really dumb asking, but do I need to install the driver and if I do how can I go about that?

---

### Post by Lambert on 2006-01-13
Post the output of this command

sudo lshw -C network

and 

iwconfig

---

### Post by BitTorrentBuddha on 2006-01-13
I think there may be something wrong with my sudo, when I enter the command and enter my password into the prompt no output comes back nor does it come when I repeat the command, the same is true for the GUIs in the administration options, the visual prompt comes up, I enter my password and then nothing happens, [on neither am I again prompted for a password when I try repeating the action]

EDIT: I'm using the trendnet TEW-443PI

---

### Post by BitTorrentBuddha on 2006-01-14
OK, A fresh install got it functioning properly, now my only problem is that I can't get it to connect, I'm not sure what I put for IP, Subnet, or Gateway under the connection, is it the same that I can find in windows by using the ipconfig command?

---

### Post by Lambert on 2006-01-14
[quote=BitTorrentBuddha]OK, A fresh install got it functioning properly, now my only problem is that I can't get it to connect, I'm not sure what I put for IP, Subnet, or Gateway under the connection, is it the same that I can find in windows by using the ipconfig command?[/quote]

You're probably using dhcp on your router to assign addresses. Change configuration from static to dhcp.

If you are using static, the ip needs to be different then your winxp box as each interface needs a unique ip address.

so if winxp was 192.168.1.2 you can assign ubuntu to 192.168.1.3
subnet mask will be the same
gateway will be the same which is your router's ip address

---

### Post by BitTorrentBuddha on 2006-01-14
Please help, I don't know what to put for my IP, subnet, or gateway :confused:

---

### Post by BitTorrentBuddha on 2006-01-14
Enabled DHCP and had it all assigned, fixed the problem, much thanks :)

---

