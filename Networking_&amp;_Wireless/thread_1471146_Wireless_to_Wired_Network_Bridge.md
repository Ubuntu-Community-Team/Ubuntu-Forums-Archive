---
title: "Wireless to Wired Network Bridge"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by Cyc. on 2010-05-03
I am running ubuntu 9.10 on a dell xps m1530 laptop dual booting with windows 7. I am trying to achieve the following setup.

Wireless router <=========> Laptop <-----> Switch <-----> PS3

---- wired
==== wireless

Both laptop and ps3 have static ip addresses

The reason for this is I can connect to the internet on my ps3 through my laptop, and I can stream from my laptop to ps3 through wired connection. This works fine in windows 7 all I had to do was right click bridge connections. As I dual boot I don't want to have to make any changes to the settings on the ps3 as that would become very annoying.

My interfaces are:
eth0 - wired
wlan0 - wireless

I installed bridge-utils and created a bridge and added both eth0 and wlan0 to it. However I could not get it to work. I have also tried internet sharing through network manager and firestarter.

Can anyone provide more details instructions on creating a network bridge?

Thanks,
Cyc

---

### Post by Iowan on 2010-05-04
I found a couple of articles on bridging - hope one of them helps:
[https://help.ubuntu.com/community/Router]("https://help.ubuntu.com/community/Router")
[https://help.ubuntu.com/community/BridgingNetworkInterfaces]("https://help.ubuntu.com/community/BridgingNetworkInterfaces")
[http://www.linuxquestions.org/questions/debian-26/howto-bridge-wireless-and-wired-network-interfaces-369455/]("http://www.linuxquestions.org/questions/debian-26/howto-bridge-wireless-and-wired-network-interfaces-369455/")

---

### Post by Cyc. on 2010-05-04
Thanks, I've seen most of them before and tried with no luck. However the router one might work if I can do it the other way round. Will give it a try when I'm a little less busy with courseworks >:(

---

