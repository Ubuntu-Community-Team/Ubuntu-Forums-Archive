---
title: "How do I disable WWAN and stop it draining battery?"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by sexyclient on 2009-10-30
It's nice that Ubuntu 9.10 has support for mobile broadband, but how the hell do I stop it from turning on whenever I load my computer?  It drains my battery until I put ubuntu to sleep then wake it up...

I don't use (and therefore haven't configured) mobile broadband, but on my laptop there's only one hardware switch to turn off wwan, wlan, and bluetooth.  Bluetooth is a lost cause and can only be "shut off" by logging into windows (...) but wwan can be disabled from linux -- but how??

(tidbits: I don't know what drivers I've got or my hardware info, but I'm un Ubuntu 9.10, sony vaio tz)

---

### Post by sexyclient on 2009-10-31
Anyone?

---

### Post by sexyclient on 2009-11-01
(Final bump...)

Anything will help, my battery depends on it :(

---

### Post by sliketymo on 2009-11-02
> **sexyclient said:**
> (Final bump...)

Anything will help, my battery depends on it :(

Try : System>Preferences>nNetwoek Connections.Click on the mobile broadband tab,and delete the connection.Might work.

---

### Post by sexyclient on 2009-11-03
Tried that, thanks, but there's no configurable options there.

---

### Post by sexyclient on 2009-11-05
Well then the problem is un-solvable in linux.  Goodnight.

---

### Post by mountain_goat on 2010-03-03
If you are still experiencing this problem, and if you haven't already done so, check that it is turned off in your BIOS. I have Dell D420 and it is all configurable for WiFi, Bluetooth and wlan.

---

### Post by zeus77 on 2011-08-17
The answer to this will depend heavily on your hardware.  As mountain_goat said, the BIOS may be one possibility.  If you have a Thinkpad, this command may work:
```
sudo sh -c 'echo 0 > /sys/devices/platform/thinkpad_acpi/wwan_enable'
```
Replace the 0 with a 1 to re-enable the WWAN.

cheers,
zeus77

---

### Post by billfeld on 2013-01-02
Thanx. That's what I was looking for. :-)
I put that into my Startup Applications so it disables Wwan on my Thinkpad on startup...

---

