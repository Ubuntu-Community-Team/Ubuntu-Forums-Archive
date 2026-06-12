---
title: "Client on LAN can't be pinged by other clients"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by skullmunky on 2009-08-30
I have two computers, a desktop and a laptop, both running Kubuntu 9.04 64 bit, both connecting over wifi.  

Computer A: The Desktop has a RaLink RT2561/RT61 PCI card
Computer B: The Laptop is a MacBook Pro (5,1)
The Router is a WRT54G.    

both computers can connect to the internet without problems.  The difficulty is in trying to use (A) as a print and file server - I can get that working for a little while, but after a little while (A) disappears and (B) can't connect to it anymore.  At first I tried different configurations with Avahi, CUPS, my ftp server, and using static or dynamic addresses;  connecting from (B) using zeroconf, or connecting from (B) using the explicit IP address of (A).  All methods stop working after a little while, and I've now discovered that (B) also cannot Ping (A), so naturally nothing else will work.  

A is 10.0.0.105
B is 10.0.0.104
Router is 10.0.0.1

I can ping B from A, but can't ping A from B.  I can get to Router from both, and to the internet from both.   I have not done any firewall configuration.

I can connect to A for a little while, but then it stops.  If I go back to A and do some network activity there, like some web browsing, I can now connect to A from B.  Then after a while it stops working again.  Is there a setting on the RaLink driver that makes it go to sleep when it's inactive?

---

### Post by uylug on 2009-08-30
Are you using default installations? I know for a fact you can configure it to ignore ping requests.

---

### Post by Iowan on 2009-08-31
> **skullmunky said:**
>   Is there a setting on the RaLink driver that makes it go to sleep when it's inactive?Dunno about the driver, but BIOS and Power Management might be worth checking.

---

### Post by natrixnatrix89 on 2010-03-07
I have the same problem too.
Maybe it can be solved in iwconfig (power):
```
power  Used to manipulate power management scheme parameters and mode.
              To  set  the  period between wake ups, enter period `value'.  To
              set the timeout  before  going  back  to  sleep,  enter  timeout
              `value'.  To set the generic level of power saving, enter saving
              `value'.  You can  also  add  the  min  and  max  modifiers.  By
              default,  those  values are in seconds, append the suffix m or u
              to specify values in milliseconds  or  microseconds.  Sometimes,
              those values are without units (number of beacon periods, dwell,
              percentage or similar).
              off and on disable and reenable power management.  Finally,  you
              may  set the power management mode to all (receive all packets),
              unicast (receive unicast packets  only,  discard  multicast  and
              broadcast)  and multicast (receive multicast and broadcast only,
              discard unicast packets).
              Examples :
                   iwconfig eth0 power period 2
                   iwconfig eth0 power 500m unicast
                   iwconfig eth0 power timeout 300u all
                   iwconfig eth0 power saving 3
                   iwconfig eth0 power off
                   iwconfig eth0 power min period 2 power max period 4

```

But what's the difference between "off" and "all"?

---

