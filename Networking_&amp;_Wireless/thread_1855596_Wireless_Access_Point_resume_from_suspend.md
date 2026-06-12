---
title: "Wireless Access Point resume from suspend"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by jwcalla on 2011-10-06
Hi,

I finally have my USB dongle acting as a wireless access point which can successfully share the internet with clients.

I used the following rc.local to make this happen:

```
/sbin/ifconfig wlan0 inet 192.168.5.1 netmask 255.255.255.0
/sbin/iptables-restore < /etc/iptables.rules
/usr/local/bin/hostapd -B /etc/hostapd/hostapd.conf
service dhcp3-server start
```This works great on boot; and it's pretty evident that the order of execution for each of the statements is important.  But when resuming from suspend, my WAP doesn't work anymore.

After resuming, this is what I have:

the kernel module (driver) remains loaded
the hostapd program is still running
the dhcp3-server process is still running
the iptables rules are still in effect
the wlan0 interface is defined, but no IP address is assigned

I attempted to resolve the last point by adding a script to /etc/pm/sleep.d that assigns the IP address to the wlan0 interface.  And while this executes successfully, it seems pretty irrelevant because this assignment has to occur before hostapd is running.

So I'm asking for some advice on how people are reconfiguring their WAPs after resuming from suspend?

It seems that the crux of the problem here is that the hostapd program isn't a service, so it can't be "restarted".  Do I have to track down the PID, kill it, start it again and then restart dhcp3-server?  Or is there a better way?

I appreciate any help.

---

### Post by jwcalla on 2011-10-10
Despite everyone's rush to help me, I decided to just make a script in /etc/pm/sleep.d/ that kills hostapd on suspend and relaunches it on resume.  Not particularly elegant, but it works.

```

#!/bin/sh

case "$1" in
hibernate|suspend)
        /usr/bin/killall hostapd
        ;;
thaw|resume)
        /sbin/ifconfig wlan0 inet 192.168.5.1 netmask 255.255.255.0
        /usr/local/bin/hostapd -B /etc/hostapd/hostapd.conf
        ;;
esac

```

---

