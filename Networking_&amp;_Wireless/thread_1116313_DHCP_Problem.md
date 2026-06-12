---
title: "DHCP Problem"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by gdselzer on 2009-04-04
One machine on my network with 8.10 loaded and a wired connection is not receiving an IP address via DHCP.  All other computers on the network, Windows and Ubuntu, are getting IPs without a problem.  The DHCP server is on a wireless router.

When I run:
```
> sudo dhclient3
```

I get:
> Listening on LPF/eth0/00:16:d3:a0:81:2f
Sending on   LPF/eth0/00:16:d3:a0:81:2f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 23
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I know that the ethernet is on the network.  I run wireshark and see other network traffic (ARP requests) coming through.  Additionally, if I setup a static address it works just fine.

Any help in troubleshooting this issue?

Thanks

---

### Post by superprash2003 on 2009-04-05
try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by gdselzer on 2009-04-05
Turning off IPV6 does not solve the problem.  I was able to troubleshoot it more but am completely at a loss as to what could be causing the problem.  Below is what I've found.  Keep in mind that this is not a new setup.  Every component has been in place for at least a couple months and working just fine until yesterday.

This computer, along with a couple others that are now having the same problem, are run through a switch which, in turn, is connected to the router.  When they are plugged into the switch, they are unable to get an IP address.  If I plug them directly into the router, they get an IP just fine.  

I figured it was a bad switch, so I grabbed another one I have lying around.  Same problem.  Bad ethernet cable from the switch to the router?  Changed it.  Same problem.  Bad router?  Changed it, same problem.

I'm going to start kicking things if I can't figure this out soon.  Help!  Please!

---

### Post by superprash2003 on 2009-04-06
ok ..this is really interesting.. does your switch have an UPLINK port? its usually this one port which is seperated from the rest of the ports.

---

### Post by sanemanmad on 2009-04-06
Sound's like a network issue... I wouldn't think Ubuntu could cause DHCP to become flaky on a entire network, let alone one it doesn't even have control over.

---

### Post by gdselzer on 2009-04-06
No uplink ports on the switches.  They are both fairly standard cheapy 8-port switches.  

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166007](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166007)

It does seem to be a networking issue, but I have no clue what the problem could be.  I've reduced the network to:

1 - Router/DHCP server
1 - Switch
1 - Computer

with no luck.

Thanks

---

### Post by sanemanmad on 2009-04-07
> **gdselzer said:**
> It does seem to be a networking issue, but I have no clue what the problem could be.  I've reduced the network to:

1 - Router/DHCP server
1 - Switch
1 - Computer

with no luck.

Thanks
I would reset your router to factory and set your PC to DHCP (bypass the switch) and connect directly using cat5. See if that works, should it work just go through the little setup wizard thingy in your router and enjoy... hopefully

---

### Post by gdselzer on 2009-04-07
Saneman, I have already tried this.  I went so far as trying a second router and second switch (please see #3 above).  If I plug directly into the router, everything works fine.  But for some reason, going through a switch is now screwing everything up.

---

### Post by coutts99 on 2009-04-07
Whats the output of ifconfig?

---

### Post by sanemanmad on 2009-04-08
can we see ```
dmesg
``` or ```
syslog
``` after running ```
dhclient
``` with the "Preferred setup" in place?

---

### Post by gdselzer on 2009-04-10
I went out of town for a couple days.  I get back and everything is working.

WTF?!

Maybe the network just need a little "space"

Thanks for all the help.

---

### Post by Iowan on 2009-04-10
Problems that solve themselves have a nasty habit of *un-solving* themselves... 
but good luck!!!

---

### Post by szarywilq on 2009-04-21
I have exacly same problem. Everything works for few months, ans suddenly yesterday problem mentioned above. I've tried everything...

On DHCP: NO DHCP OFFERS RECIEVED
on static - just do not work.

But there is something I have found out. I can't even ping router... On this pc I also have xp and on 2 other pc's also xp, and I tried ubuntu from live CD - all of these works fine.

---

### Post by gdselzer on 2009-04-21
Maybe your network card died?  Do you have a spare one around that you can install and test?

---

