---
title: "Gigabit?!?! NetXtreme BCM5751 Gigabit"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by z80 on 2010-08-21
Ok so I have been using ubuntu regularly for about a year now and i have once again decided to tackle my Ethernet issue.  it makes me want to c4 my computer.  I have a NetXtreme BCM5751 Gigabit Ethernet PCI Express, and that is in a dell demension 8400.  This in turn is connected to a gigabit ethernet router with four other gigabit devices connected.  For some reason even with the proper driver the ethernet controller thingy wont select 1000MB/s and i cant seem to do it manually... here is the only real command i have tried and had fail:

sudo ethtool -s eth0 speed 1000 duplex full autoneg off

and it returns:

Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg

im completely lost and frustrated because i have found a graphical interface to control every other setting i want on my system but nothing for Ethernet, and the terminal just irritates me because it dosnt really tell me what i need to change to get it right...  
any help would be appreciated...
:cry:](*,)


ooooh by the way i am running   Ubuntu 10.04 LTS - the Lucid Lynx

---

