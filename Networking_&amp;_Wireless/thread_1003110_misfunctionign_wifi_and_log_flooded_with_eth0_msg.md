---
title: "misfunctionign wifi and log flooded with eth0 msg"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by damatta on 2008-12-05
1) I'm on a wireless link (interface wlan0) and sometimes when i'm using transmission bt the connection is lost and after recovering i get lots of delayed packets in my tcpdump. Browsing the internet then is impossible. If i disable the network using the connection manager and enable again, it simply wont find any other wifi networks not even my own! 
notes: i'm on a laptop
        disabling avahi service seems to soothen this problem

2) every 10 seconds i get this in my log:

kernel: [ 1287.048025] eth0: auto-negotiating...

I can only imagine the meaning of that but its certainly nagging. I suspect disabling eth0 or something similar would help. How do you think i should proceed
Thanks

---

### Post by jmoorse on 2008-12-07
1. How far are you from your Access Point?  Are there any 2.4Ghz phones or microwaves in the way?

2. Instead of disabling you can just:

sudo ethtool -s eth0 speed 100 duplex full autoneg off

This manually sets the card to 100Full and disables autonegotiation

---

### Post by damatta on 2008-12-07
Hey thank you but the ethtool did not make it stop.
My wireless is perfectly functional when i'm using windows, i'm just 4m away from my AP. I tried reinstalling the driver rt73usb to no avail. It's really a strange problem, sometimes the network manager reconnects, sometimes the connection simply pauses and then i watch tcpdump getting lots of arp requests coming from me and suddenly lots of delayed packets. I'm starting to think this is not a driver related issue but some network config that hinders my internet.

---

### Post by jmoorse on 2008-12-07
I would imagine that if it works fine in Win it is a problem with your network driver/config on the Ubuntu box.  You may want to consult the Ubuntu wireless documentation for your specific wifi adapter.

---

### Post by damatta on 2008-12-11
Just in case someone seeking for help stumble onto this topic, this helped me: [http://mcmlxxii.co.uk/2008/10/22/rt73-ubuntu-intrepid-8-10/](http://mcmlxxii.co.uk/2008/10/22/rt73-ubuntu-intrepid-8-10/)

---

