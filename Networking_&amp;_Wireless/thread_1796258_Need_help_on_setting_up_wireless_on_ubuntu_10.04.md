---
title: "Need help on setting up wireless on ubuntu 10.04"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by ImMatthew on 2011-07-03
Hello i need help on setting up wireless internet on ubuntu sever 10.04.

if anybody can help me or send me to a post were this has been explained already that would be great thanks :P.

---

### Post by Bucky Ball on 2011-07-03
Wecome. Firstly, have you plugged in an ethernet cable and gotten online that way? Do that and get updates then check System>Administration>Additional Drivers (or Hardware Drivers). Anything there? 

Secondly, if that doesn't get some action happening, open a terminal (Applications>Accessories>Terminal) and paste this in:

```
lshw -C network

```Post the results back here and that will tell us your wireless card and its current configuration. ;)

---

### Post by ImMatthew on 2011-07-03
Hello ive had this problem all day long ive googled non stop can anybody help i really want to get this to work.

The problem is im trying to get Wifi to work on ubuntu server 10.04 and i have a wep on it.

so dose anybody know a good solution to this?

---

### Post by mikewhatever on 2011-07-03
Here you go: [http://newbiedoc.berlios.de/wiki/How_to_set_up_a_wireless_network_card_using_drivers_from_Debian_packages](http://newbiedoc.berlios.de/wiki/How_to_set_up_a_wireless_network_card_using_drivers_from_Debian_packages)

Assuming the wireless driver is installed, start from the 2.3 section.

Here is another good one:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by Iowan on 2011-07-04
Threads merged.
From CoC:
> Do not cross post, or post the same thing in multiple locations.

---

### Post by Bucky Ball on 2011-07-04
> **ImMatthew said:**
> Hello ive had this problem all day long ive googled non stop can anybody help i really want to get this to work.

The problem is im trying to get Wifi to work on ubuntu server 10.04 and i have a wep on it.

so dose anybody know a good solution to this?

I posted 16 hours ago and asked you to identify your wireless card and post back. Post #2 which you seem to have missed ...

So if you could give the results of the command in that post we can maybe start to solve your problem ... ;)

---

