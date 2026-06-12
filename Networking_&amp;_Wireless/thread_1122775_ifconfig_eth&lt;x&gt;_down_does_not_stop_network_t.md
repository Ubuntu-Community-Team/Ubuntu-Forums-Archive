---
title: "ifconfig eth&lt;x&gt; down does not stop network traffic on eth&lt;x&gt;?"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Schorschi on 2009-04-11
Ok, not being 100% familar with how linux networking works as yet, in reference to bonds, bridging, etc., but still this has me puzzled.  I have a server, runnng 9.0.4 beta (latest updates applied).  I have two NICs, eth0 and eth1, assigned two different IPs respectively, we plan to do virtualization on this box, and want shape traffic by using different VLANs, hence the different IPs for now and different NICs.

If I disable eth0, both IPs are still pingable.
#ifconfig eth0 down

And ethtool reports link state as good.  This implies that internal routing in taking place, which is what we do not want.  So I check route, no cross route exists.  So I unload the driver for eth0, it just so happens that eth0 and eth1 are different model/make of NICs, as I said this a test setup so not what we would do for critical use outside of our lab.

#rmmod e1000e

And link state is down, and IP for eth0 is of course not responding.  This does not appear to be good behavior, if eth0 is taken down by # ifconfig eth0 down, it should stop all traffic.  At least the way I understand it, and the way I recall Solaris behaving.

We have no bridging in place, no bonding is active.  Although we do have bridge utils and ifenslave installed, just not enabled.  The only interfaces defined in /etc/network/interfaces are eth0 and eth1.

This appears to be a bug?  Or is it the expected behavior?

---

### Post by FrankT-Qc on 2009-04-11
Two things that I would check : 

1- Did ifconfig really bring the thing down (is it reported as down) if not, try this instead : ```
ip link set down eth0
```

2- Do you have an "autoconfig" application that could bring it back up when used ?

3- The IP addresses that you assigned to your devices, could they be also assigned somewhere else (tun, bridge, tap, whatever...)

---

### Post by Schorschi on 2009-04-13
Definitely have not setup any type of autoconfig, just a simple install of OS.  No other use of IPs, everything is on simple VLAN and range being used is static range, no DHCP or such.  I have not tried your first suggestion, but wil do so.  I think I understand the logic, that ifconfig is scripted sequence so it may not be functioning as expected?

---

### Post by Schorschi on 2009-04-13
Definitely have not setup any type of autoconfig, just a simple install of OS.  No other use of IPs, everything is on simple VLAN and range being used is static range, no DHCP or such.  I have not tried your first suggestion, but wil do so.  I think I understand the logic, that ifconfig is scripted sequence so it may not be functioning as expected?  The link state still show detected but the interface is not response as expected.

---

