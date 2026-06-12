---
title: "How to avoid 169.254.0.0 address assignment after network down"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by mbaitoff on 2010-07-14
I'm connected to the network, to 24-port switch, using the DHCP address assignment. When the network administrator rebooted the switch, I've lost the network connectivity ("media disconnected"). While the switch was booting, my machine auto-configured the network adapter to belong to 169.254.0.0 network. When the network connectivity resumed, I continued to belong to 169.254.0.0 network. To resume my networking, I had to take the network adapter down and up again.

This is a nuisance when I'm present in the office, but when I'm out, I cannot connect to my office machine.

How can I setup the networking to try obtain the DHCP address infinitely, avoiding self-assignment to 169.254.0.0 network?

---

### Post by Iowan on 2010-07-14
I haven't tried adjusting any of the timout/retry options, but */etc/dhcp3/dhclient.conf* is the file to check for DHCP options. **man dhclient** should provide *some* help...

---

### Post by doogy2004 on 2010-07-14
[http://linux.die.net/man/5/dhclient.conf](http://linux.die.net/man/5/dhclient.conf)

> The retry statement 

retry time;

The retry statement determines the time that must pass after the client has determined that there is no DHCP server present before it tries again to contact a DHCP server. By default, this is five minutes. 

looks like this may be a starting point.

---

### Post by mbaitoff on 2010-07-14
It seems that when the interface falls back to 169.254.0.0, it no longer cares about the DHCP settings, and stops trying to contact any DHCP server.

Network down event happened after the end of the working day last time, and the office machine has been unreachable until morning, when I came to the office and restarted the interface. Obviously, the whole night is much longer than default five minutes.

Moreover, what to do if the interface was configured as "static" IP address, and never contacts the DHCP?

---

### Post by doogy2004 on 2010-07-15
you could write a script to ping something or check the ip, if the ping doesn't work or the ip is wrong you could have the script take down the interface and bring it back up.

---

### Post by capscrew on 2010-07-15
> **mbaitoff said:**
> It seems that when the interface falls back to 169.254.0.0, it no longer cares about the DHCP settings, and stops trying to contact any DHCP server.

Network down event happened after the end of the working day last time, and the office machine has been unreachable until morning, when I came to the office and restarted the interface. Obviously, the whole night is much longer than default five minutes.

Moreover, what to do if the interface was configured as "static" IP address, and never contacts the DHCP?

Just disable Avahi if you don't want it to try and configure the interface.  I believe the avahi-autoipd daemon is what controls this.  See these man pages```
avahi-autoipd(8)
autoipd.action(8)
dhclient(8)
```

The Avahi auto-pid is also [**_documented here_**]("http://avahi.org/wiki/AvahiAutoipd").

> Moreover, what to do if the interface was configured as "static" IP address, and never contacts the DHCP?

If you have the host configured with a static IP address, Avahi will never come into play.  It needs to see the request for DHCP go unanswered before it auto-configures.

---

### Post by mbaitoff on 2010-07-18
> **doogy2004 said:**
> you could write a script to ping something or check the ip, if the ping doesn't work or the ip is wrong you could have the script take down the interface and bring it back up.

this is not robust. if "something" goes down, the script would trigger, ruining all the active connections.

---

### Post by mbaitoff on 2010-07-18
> Just disable Avahi if you don't want it to try and configure the interface. I believe the avahi-autoipd daemon is what controls this. See these man pages

I have already disabled Avahi before by putting "use-ipv4=no, use-ipv6=no" in avahi-daemon.conf, and there's no any running process containing "avahi" in it's name.
Seems that it activates during the network down, or there's something else playing it's role.

---

