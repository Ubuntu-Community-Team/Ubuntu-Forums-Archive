---
title: "Cannot connect to LAN via Cat-5"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by StepNjump on 2012-01-15
Hi guys,

Normally I connect to the LAN using my wifi connection on my netbook. Having said that, I don't remember the last time I used my eth0 connection. Now I just found out tonight that the wired connection is not working.

I thought it might be a hardware problem.. Fortunately it isn't that because it works just fine using the live USB.

I tried to do a dhclient eth0 to no avail.
eth0 is showing in my ifconfig -a

I tried a ifconfig eth0 up
I get Interrupt: 46

Any ideas why my LAN is no longer coming up?

I'm set up DHCP enabled on my router.
pinging the router: Destination host unreachable.

I didn't fool around in any configuration files whatsoever... Could they get corrupted like that for no reason?


Thanks in advance,


Pete, Stepnjump

---

### Post by Iowan on 2012-01-15
Which version are you using?
Please post results of **sudo lshw -C network**
(from a terminal)

---

### Post by StepNjump on 2012-01-30
Iowan, sorry for the delay.
I was reviewing my tickets here today and found out this hadn't been updated yet.

Thanks for your reply however, everything works great now.. Didn't do anything!
Might have been a hardware connection issue.. who knows.

Thanks

SNJ

---

