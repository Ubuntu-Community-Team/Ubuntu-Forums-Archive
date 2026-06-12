---
title: "Internet sharing over Bluetooth PAN?"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by viktorzk on 2009-12-10
Hello,

I am trying to connect a Nokia E51 phone to the Internet over a Bluetooth connection with my laptop. (I only need access to a localhost server.) I tried following this:
[https://core.forge.funambol.org/wiki/FunambolOverBluetooth](https://core.forge.funambol.org/wiki/FunambolOverBluetooth)

1. The tutorial is made for an old version of the BlueZ package. Things like pand seem to be no longer there (I am running Karmic), and I had to install bluez-compat, which is not supported and "will go away in the future". How can I do the same with the new BlueZ?

2. How to "start a DHCP server on pan0"? I tried with the gadmin-dhcpd GUI tool, but couldn't get the settings right. Please be very detailed here, I am a complete newbie to linux and networking in general.

3. The line 'echo "1" > /proc/sys/net/ipv4/ip_forward' gives permission denied even with sudo.

Of course, if anybody knows a better way of getting the job done, that would be great.

Thanks!

---

### Post by viktorzk on 2009-12-11
bump

---

### Post by beany1 on 2009-12-11
right click networking icon - uncheck enable networking - then i was able to run the command "echo "1" > /proc/sys/net/ipv4/ip_forward" - but as for the rest havnt got a clue sorry never tried bluetooth pan before - as  the new gnomebluetooth  is a fork for bluez i dont think many guides will work without alterations. hope this helps

---

### Post by beany1 on 2009-12-11
[http://blog.sumostyle.net/robg/?p=381]("http://blog.sumostyle.net/robg/?p=381")

looks alot easier that the guide your using, and he claims to have had success on karmic, but when i tried to install the bluez package it wanted to remove lots of things so i couldnt try!

---

### Post by robgarth on 2010-01-13
If you have already been using blueman, there are conflicts between bluez and blueman.

But I have scripted up the pand method, and it is the most reliable way I have found to tether.

---

