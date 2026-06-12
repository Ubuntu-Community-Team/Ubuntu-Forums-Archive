---
title: "sharing an internet connection through a wifi card"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by AVeryLongNickname on 2011-01-30
Hello!

Im living in a student-city where we get one internet-cable in the wall each, if we need more we are told to use a switch. But, since ive got some tech that depends on wifi, I was wondering if its possible to setup my ubuntu to work like a sort of wifi-switch?

basically, Im not allowed to set up anything that resembles a router..(so no dhcp) all i need is what a switch would do, only wireless:) and wpa/wep would be very nice :)

atm ive got my cabled network plugged into my onboard ethernet-port, and ive got a d-link DWA-556 (Atheros AR5008 I think) wifi card that i wanted to use to share my connection.

is this doable?

any help is much appreciated :D

---

### Post by Tweak42 on 2011-01-31
It sounds like the Wireless Ad-Hoc method may work for you detailed here:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

The Gateway method makes your computer essentially a router, so that would not suit your setup.  

Alternatively, some wireless routers can be configured to wireless access point (AP) mode.  This shuts off the router/firewall portion and allows all wired/wireless traffic through to the outbound ethernet port acting like a "switch".  You should still be able to use wep/wpa encryption in AP mode.

As to what models of wireless routers support AP mode, some may support it out of the box.  I do know that any routers that support ddwrt firmware can do it.  [http://www.dd-wrt.com/wiki/index.php/Wireless_Access_Point](http://www.dd-wrt.com/wiki/index.php/Wireless_Access_Point)

---

### Post by AVeryLongNickname on 2011-01-31
Thanks for the reply and the link :)

Now I'm able to set up an Adhoc-network, and I'm able to connect to it, but none of the other devices (laptop, iPhone, iPad) are able to connect to the internet, even though I'm connected to the Adhoc. Could it be a problem with the wifi-driver? Network Manager says im using the ath9k-driver.

But at least now I'm one step closer to my goal! ;) thanks :)

---

### Post by AlexQM on 2011-02-03
There is also way of bridging your wifi connection using a similar setup to this: [http://madwifi-project.org/wiki/UserDocs/WDSBridge](http://madwifi-project.org/wiki/UserDocs/WDSBridge)

I'm not having much setting it up myself though so if you get it working let me know how!!!

---

