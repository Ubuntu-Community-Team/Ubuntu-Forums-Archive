---
title: "Disabling Wireless Networking with Terminal Commands"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by Lorokien315 on 2011-03-10
So, I've been trying to figure this out for the last couple of days but I can't manage to find any help with exactly what I need to do.

I am trying to find a way to make a *.sh file that will do the following things:
Disable Wlan1/Wireless Networking all together
Change mac address
Reenable Wlan1/Wireless Networking

With this *.sh file I plan to be able to open a terminal, run "sudo sh *.sh", and have  it run the multiple commands quickly, cloning my mac address as quickly as possible.

*Note: if there is a way to clone my wireless mac address without having to disable wireless networking I would love to know how :D

Here is what I've gotten so far (contents of current *.sh file):

#!/bin/sh

ifconfig wlan1 hw ether ##:##:##:##:##:##
 
*currently I have to use the FN hotkey on my keyboard to disable wireless networking, then run the command "sudo sh *.sh", then reenable wireless networking through the same hotkey combination.

Here is what else I have tried (please don't laugh if I put irrelevant commands in here, I'm pretty much a noob, and I'm trying to learn :p)

contents of other *.sh file #2:

#!/bin/sh

ifconfig wlan1 down
ifconfig wlan1 hw ether ##:##:##:##:##:##
ifconfig wlan1 up

contents of other *.sh file #2:

#!/bin/sh

ifconfig wlan1 down
/etc/init.d/networking stop
ifconfig wlan1 hw ether ##:##:##:##:##:##
/etc/init.d/networking start
ifconfig wlan1 up

contents of other *.sh file #3

#!/bin/sh

ifconfig wlan1 down
/etc/init.d/networking stop
ifconfig wlan1 hw ether ##:##:##:##:##:##
/etc/init.d/networking restart
ifconfig wlan1 up

-------------------------------

I noticed that when I run the "/etc/init.d/networking stop" command in the terminal I get a message that states something along the lines of "ignoring unknown device wlan1=wlan1" hence the reason I always ran "wlan1 down" before hand.  However, when I run the "wlan1 down" command it seems to automatically restart the driver and restart the network card before i run "wlan1 up".

please, please help me, I'd really appreciate it :D

---

