---
title: "Wired network, 20mb connection but only 10mb downloadspeed"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by blackSP on 2010-06-03
Does anybody know what may be the problem here?

10.04 64 bit with the default network manager.
20mb ADSL connection
Asus pfql-e mobo with onboard atheros giabit lan
Wired with a super cat5 cable (about 8 meters)

In network information I see a maximum speed of 10 mb/s. but the card should switch from 10 to 100 to 1000 mb/s if I'm correct.

What can I do to get my 20 mb speed?

---

### Post by Ranko Kohime on 2010-06-03
When I got Internet set up at my apartment, the store I went to, to order service gave me a modem.  When they showed up to hook up the wires and test the system, they told me I was given the wrong modem, and that it would max out at 10Mbps because it was only designed to do that.  (It would not allow the computer to switch up to 100Mbps)

They swapped out the modem for a different one, and I ended up with about 27Mbps of real usable speed.

May want to check to see if your modem actually handles more than 10Mbps.

---

### Post by blackSP on 2010-06-03
Hi, thanks for the tip. I just checked again but the modem is a SpeedTouch 780 and supports both 10 and 100 mb/s, the network card on the mobo of my PC is a 10/100/1000 card and should also autoswitch. It looks like my internal network won't go over 10mb.

sudo ethtool -s eth0 speed 100 duplex full
doesn't change it to 100.


Settings for eth0:
   Supported ports: [ TP ]
   Supported link  modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
   Supports auto-negotiation: Yes
   Advertised  link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
   Advertised pause frame use: No
   Advertised  auto-negotiation: Yes
   Link partner advertised link modes:  Not  reported
   Link partner advertised pause frame use: No
   Link  partner advertised auto-negotiation: No
   Speed: 10Mb/s
   Duplex:  Full
   Port: Twisted Pair
   PHYAD: 0
   Transceiver:  internal
   Auto-negotiation: on
   MDI-X: Unknown
   Supports  Wake-on: pg
   Wake-on: d
   Current message level: 0x00000000 (0)
   Link  detected: yes

---

### Post by blackSP on 2010-06-04
Case closed, I solved it (on my own).

---

### Post by Ranko Kohime on 2010-06-05
> **blackSP said:**
> Case closed, I solved it (on my own).
What ended up being the problem?

---

### Post by Phrea on 2010-06-05
> **Ranko Kohime said:**
> What ended up being the problem?

This.
Posting your solution might help others.

---

### Post by scarf on 2010-06-23
> **Phrea said:**
> This.
Posting your solution might help others.Yes, please share.


edit: this worked for me:
> Try turning off the computer, unplugging from the wall, and pull the power connector on the motherboard. Modern ethernet cards use digital tuners and they retain gain settings between reboots. It's possible that your network card is scrambled and it needs to be reset.

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9290894&postcount=12](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9290894&postcount=12)

although, i did not take apart the case and unplug the power connector from the motherboard.  simply unplugging from the wall for about 30 seconds worked for me.

---

