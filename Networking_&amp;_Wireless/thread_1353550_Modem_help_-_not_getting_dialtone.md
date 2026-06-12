---
title: "Modem help - not getting dialtone?"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by poltr1 on 2009-12-12
I have a Compaq Presario M2000 with a built-in modem and wireless cards.  When I installed karmic on it, it identified them and automatically loaded the drivers.  The wireless driver works fine, but I'd like for the modem to work as well.

I ran scanModem and the modem was identified as an "ATI Technologies Inc SB400 AC'97 Modem Controller".  I edited /etc/wvdial.conf accordingly and when I ran wvdial, I got the messages "--> Cannot get information for serial port." and "no dialtone".  It's finding and initializing the modem, however.  I'm getting the same messages when I use gnome-ppp.

(The phone line is plugged in when I do this.)

Having modem access would be nice to have, as it would be one less reason for me to stick with Windows.

---

### Post by gordintoronto on 2009-12-13
That sounds like a Winmodem.  You might find some useful information on this site:
[http://www.linmodems.org/](http://www.linmodems.org/) 

Is the same hardware used for sound on your computer?

---

### Post by poltr1 on 2009-12-14
I'm not sure, Gord.  Everything's inside the laptop and I haven't been brave enough to go under the hood on this one.  

It wouldn't surprise me if the built-in modem it was a winmodem.  XP was the original OS on the system.

---

