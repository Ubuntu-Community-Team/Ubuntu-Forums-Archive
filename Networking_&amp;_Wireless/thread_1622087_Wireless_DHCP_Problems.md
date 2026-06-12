---
title: "Wireless DHCP Problems"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by deadguy on 2010-11-15
Hello,

I've been trying to figure out a strange DHCP problem my girlfriend's having:  She can only get (or renew) a DHCP lease once;  Subsequent tries timeout.  I tried switching from network-manager (which uses dhclient) to wicd (dhcpcd), and noticed a key difference:  With wicd, restarting helps (again, works once, then another restart is required).  With network-manager, I haven't been able to get another lease, period.  

Exploring the dhcpcd case further, I found that suspend/hibernate do not correct the issue; a full restart is required.  Neither does `/etc/init.d/wicd restart` help.  I don't remember if I tried killing dhcpcd;  I'll have to test that.

The current workaround is to restart the computer after each disconnect.  It's pretty annoying, though, so I'd like to try to collect enough specifics to file accurate bug reports for each dhcpcd and dhclient.  Is anyone familiar with these projects?  Are these known issues?  Any ideas how to hone in a bit?  My gut tells me there's some state somewhere that needs to get flushed.  I read the manuals and deleted the lease files, but none of that seemed to help.

I'll post the card and router info soon.  I do know router's WEP protected.

---

### Post by uncaspi on 2010-11-15
I don't know if this works. dhclient renew or dhclient release
See man dhclient

---

### Post by LeMeun on 2010-11-15
I don't know which flavor of Ubuntu you are on but usually killing network manager and wicd using ps -ax and kill 1234 (1234 being the PID #). and configuring your /etc/network/interfaces file correctly:

auto wlan0 (replace wlan0 by your wireless interface)
iface wlan0 inet dhcp

Save (using nano CTRL+X)

followed by cd  /etc/init.d/
./networking stop 
./networking start

does the job

i think there is an easier way to do it but if forgot (./network restart?)

---

