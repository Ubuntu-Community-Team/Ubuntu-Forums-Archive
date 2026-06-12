---
title: "Question about RT200 and Aircrack-ng"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by dbzkid on 2010-04-19
Hello everyone, I'm new to the forums and was wondering if I could get some help with Aircrack-ng. I have tried this tool befor on a friends laptop but wanted to try it on my own desktop. I will list my wificard:
Manufacturer: AZIO
Model Number: AWD102N
When I go and do Airmon-ng I get: 
```
Interface	Chipset		Driver

ra0		Ralink 2560 PCI	rt2500 
```
If I do airmon-ng start ra0 I get:
```
Interface	Chipset		Driver

ra0		Ralink 2560 PCI	rt2500 (monitor mode enabled)
```

meaning monitor mode is possible, but when i try a test for injection I get:
```
#aireplay-ng -9 ra0
02:50:59  Trying broadcast probe requests...
02:51:00  No Answer...
02:51:00  Found 4 APs

02:51:00  Trying directed probe requests...
02:51:00  00:18:39:7F:B9:3E - channel: 6 - 'linksys'
02:51:06   0/30:   0%

02:51:06  00:0F:66:B2:9E:16 - channel: 6 - 'linksys'
02:51:12   0/30:   0%

02:51:12  00:12:17:46:8F:B8 - channel: 6 - 'linksys'
02:51:18   0/30:   0%

02:51:18  00:26:F2:64:E6:26 - channel: 6 - 'Johnson'
02:51:24   0/30:   0%

```
apperently This card doesnt support injecting... but what confuses me is this > Packet injection is now fully supported under Linux on PCI/CardBus RT2500 cards from > [http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=c4a36903831ab7b2c40874416f5f8ea6#compatibility](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=c4a36903831ab7b2c40874416f5f8ea6#compatibility)
has anyone ever seen this? I am just confused whether I am doing something wrong, Im running ubuntu 9.10 and the card was automatically discovered by ubuntu

---

