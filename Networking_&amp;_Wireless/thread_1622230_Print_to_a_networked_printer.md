---
title: "Print to a networked printer"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by revtds on 2010-11-15
I have a network that connects my office and home together.  The home system has a cable 10Meg service, and from this router (192.168.2.1) a cable goes to the office router (192.168.1.1). Attached to each router are an HP Laserjet 4100 on 2.1(home) and a Phaser 860 on 1.1.(office)

From my office computer I can access both printers using TCP/IP.  From home, I cannot find or access the Phaser which is on the second router. No problem using the HP from the home computer.

Both printers are directly connected to the routers.

I assume this is something simple, but I can't find it, so any help would be greatly appreciated.

The reason for two routers is the office and home are 150 year old brick buildings, and even though they are very close, actually connected, wireless is unable to penetrate with much efficiency to the office, hence the second router giving wireless access in the office as well.

---

### Post by revtds on 2010-11-28
bump

---

### Post by cybergnome on 2010-11-28
I'm assuming that you don't need to have two networks, though in effect, that's what you've created.  If the router in the office is to serve simply as an access point, then it should have an IP in the subnet range of the home router.  DHCP should be turned off in the access point, allowing the home router to do all the routing for all network devices.

---

### Post by revtds on 2010-12-04
I have turned DHCP off in the office router, left everything connected as it was, but when I do that, none of my wired connections through that router in the office work anymore.  I cannot find the Phaser printer, my wired connection to my office PC no longer works, the other office PC no longer makes a connection, etc.

Are there other settings I need to change so the the Belkin is only an access point?  It does not show up in the DHCP Client table on the home router. Nothing new does.  It still only shows the stuff in the house, so I have no address to find the office computer again.

It sounded like all I needed to do was turn DHCP off on the office computer, and everythign would sort itself out. What am I missing.  I only know enough about this to think I can set something simple like this, and then find out I am stupid about it.

Any help I can get to put this system up and running again would be greatly appreciated.

---

### Post by revtds on 2010-12-22
I finally turned my Belkin router into an access point, re-booted everything and I now have access to all of the printers. Turning DHCP off I guess is what enabled that but not until everything was rebooted did it start working.

Thanks for your help.

---

