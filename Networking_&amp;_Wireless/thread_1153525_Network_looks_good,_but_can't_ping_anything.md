---
title: "Network looks good, but can't ping anything"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by inphinity on 2009-05-08
On a fairly fresh install of Jaunty, everything was going normally until I rebooted to add a HDD.  Before the reboot, I installed a few basic packages, including uTorrent on Wine, G15stats/daemon and PeerGuardian.  When the system came back up, I had zero internet connectivity.  (I've since removed the HDD, but that hasn't made a difference.)

Currently, these are my symptoms:

[LIST]
[*]Cannot ping localhost, 127.0.0.1, or 192.168.0.118 (this machine), no other machines can ping this one (all pings are just lost)
[*]ifconfig looks normal, two interfaces listed (eth0 and lo)
[*]Unplugging and replugging the cable, Ubuntu recognizes the event and says it's connected
[*]sudo dhclient3 seems to return an IP (this machine has a reserved IP on the router)
[LIST]
[*]DHCPACK of 192.168.0.118 from 192.168.0.1
[*]bound to 192.168.0.118 -- renewal in 905652007 seconds
[/LIST]
[/LIST]
I'm at my wits end -- I've searched high and low for the cause of this, and while I'm still relatively new to Ubuntu, I can't fathom what could be causing this.

Any help is greatly appreciated!

](*,)

---

### Post by superprash2003 on 2009-05-09
post output of **sudo iptables -L** . have you installed firestarter or anything similar..try also **sudo /etc/init.d/networking restart**

---

### Post by dandnsmith on 2009-05-09
Whatever else caused the problem, it will not have been the HDD (unless through some disturbed cables/connections).
A common problem is to load new software, the impact isn't present until it has had a chance to settle in and the system has been rebooted - I'd be looking at that new stuff as a possible cause.

Apart from that, I'd go with the iptables suggestions, as firewalls are the most common way of rendering network connections useless.

---

### Post by inphinity on 2009-05-09
> **dandnsmith said:**
> Whatever else caused the problem, it will not have been the HDD (unless through some disturbed cables/connections).

Yah, I was 99% sure the HDD wasn't related, but mentioned it just on the off-chance.

> **superprash2003 said:**
> 
post output of **sudo iptables -L** .

```

Chain INPUT (policy ACCEPT)
target   prot  opt  source     destination
QUEUE   all    --    anywhere        anywhere

Chain FORWARD (policy ACCEPT)
target   prot  opt  source     destination

Chain OUTPUT (policy ACCEPT)
target   prot  opt  source     destination
QUEUE   all    --    anywhere        anywhere

```> **superprash2003 said:**
> 
try also **sudo /etc/init.d/networking restart**An interesting result:
```

 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0
                                                                              [ OK ]

```

---

### Post by superprash2003 on 2009-05-09
post output of the /etc/network/interfaces file

---

