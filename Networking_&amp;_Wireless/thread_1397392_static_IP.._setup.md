---
title: "static IP.. setup"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by rflores2323 on 2010-02-03
hey I am having problems forwarding my port on my ubuntu 9.10 box.  can someone please see below my settings and advise what needs to be done. 

my connection settings
[IMG]http://www.ubuntu-pics.de/bild/40851/screenshot_007_CLQ7hB.jpg[/IMG]

what am I suppose to change here on the connection screen to? 

[IMG]http://www.ubuntu-pics.de/bild/40852/screenshot_008_1iOxD5.jpg[/IMG]

my router settings-  am I suppose to change this to set static IP? what static ip do i choose?  does this Ip go to the connection screen in ubuntu? 
[IMG]http://www.ubuntu-pics.de/bild/40853/screenshot_010_7p4p11.jpg[/IMG]
[IMG]http://www.ubuntu-pics.de/bild/40854/screenshot_011_8xzawn.jpg[/IMG]

my port forward settings- which do not work in either transmission or xbmc.
[IMG]http://www.ubuntu-pics.de/bild/40855/screenshot_012_FLz42T.jpg[/IMG]

can someone pleasae help on this.  also i need the connection to connect automatically when booted.

sorry but I dont know what to change and dont want to screw my settings all up.  help  :grin: 
thanks for the help/

---

### Post by Iowan on 2010-02-03
You will probably need to leave the router set to DHCP (dynamic) address - unless your ISP assigned you a static address. That means that you'll probably need services such as [no-ip.com]("http://www.no-ip.com/") or [dyndns.com]("http://www.dyndns.com/"). 
You can probably set up your DHCP server (router?) to issue a static lease based on MAC address and leave the box set for DHCP. Whether you set up static IP address or a static lease, the address will need to be in the same subnet - but outside the DHCP range. The other information can be copied.

---

