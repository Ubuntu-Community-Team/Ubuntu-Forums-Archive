---
title: "Weak wireless internet signal"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by camronh08 on 2009-11-02
I recently got a new computer and after putting it together and installing Ubuntu, I am experiencing very weak internet connection signals. Every few seconds it skips from 88% to 50% to even 30% and it is very annoying because I will lose connection on games I'm playing online.

The computer is in the exact same place as my old computer that had excellent signal from my router which is only about 15 feet away, through one wall. This is the first computer I've managed myself, but after searching for hours on different problems, I finally thought I would ask the community.

I'm using an Asus PCI-G31 Wireless Adapter, running Ubuntu 9.04.

Any suggestions or tips to fix/improve the connection?
Also, if any other system infortmation is relevant, please ask and I will post it. I'm a beginner at this.

---

### Post by SteveDee on 2009-11-02
> **camronh08 said:**
> I recently got a new computer and after putting it together and installing Ubuntu, I am experiencing very weak internet connection signals. Every few seconds it skips from 88% to 50% to even 30% and it is very annoying because I will lose connection on games I'm playing online.

The computer is in the exact same place as my old computer that had excellent signal from my router which is only about 15 feet away, through one wall. This is the first computer I've managed myself, but after searching for hours on different problems, I finally thought I would ask the community.

I'm using an Asus PCI-G31 Wireless Adapter, running Ubuntu 9.04.

Any suggestions or tips to fix/improve the connection?
Also, if any other system infortmation is relevant, please ask and I will post it. I'm a beginner at this.

You may be suffering interference from other WiFi systems. You could simply try changing channels to see if it improves (e.g. if you are using channel 12, try switching to a low channel like 1).

If you can install the latest version of WiFi Radar, this will show the channels used by all wifi within range. Try to ensure you are at least 3 channels from the strongest signals.

Notes on Wifi Radar:-
WiFi Radar version 2 onwards will show channels used for each Access Point within range.
The Jaunty Rep only includes V1.9.
So download V2.x from here: [http://wifi-radar.berlios.de/pub/](http://wifi-radar.berlios.de/pub/)
Extract from tar.
In terminal navigate to new directory & run "make"
Now run:-
gksu path/wifi-radar or create a launcher.

You may need to create /etc/wifi-radar/wifi-radar.conf so it can save conf settings.

---

