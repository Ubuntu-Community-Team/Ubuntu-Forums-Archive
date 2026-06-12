---
title: "where is the wlan0 auto connect configuration files?"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by shiftlong on 2011-03-28
Hi,i am new here.

when i use the terminal and type the words: ifconfig wlan0 down

it is surely shutdown now,but after a few seconds it works and connect to the net again.
i just want to ask where i can find and change the configuration file.:confused:

thanks for looking and answering it.

at last thanks for the ubuntu team make the desktop better and better.:D

ps:i use the ubuntu 10.04

---

### Post by vuncaro on 2011-03-29
Hi I use kubuntu 10.10, when i whant to stop my wireless i do this:
sudo rfkill block 0
sudo rfkill block 1

to bring up again
sudo rfkill unblock 0
sudo rfkill unblock 1
sudo ifconfig wlan0 up

I don't know if is this what you need

---

### Post by shiftlong on 2011-03-29
thanks for sharing~
it works and won't up again. thank you!

---

