---
title: "eth0/dhcp lost and mysteriously back"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by photoriot on 2009-03-18
I power-cycled my router (Linksys WRT54G) and found I lost net connectivity on my kubuntu 8.04 box (I believe 8.04 - not sure how to check version w/ kubuntu). The box had been rebooted a couple of times since the last upgrade. Looking in /var/log/messages after un/replugging the net cable I noticed these msgs w/in the same second:

eth0: link up, 10 Mbps, half-duplex, lpa 0x0000
ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
eth0: link down

After a while with no ip showing on eth0 in ifconfig, an eth0:avahi entry appeared after the eth0 one:

eth0:avahi ...
       inet addr:169.254.3.1 ...

I looked at /etc/network/interfaces and saw
---
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
---

So I uncommented the commented line and ran 'sudo ifup -a' and also tried a reboot. It seemed there was no dhcp offer on eth0, and the eth0:avahi entry came up right away instead of after a while.

Then I let the machine sit overnight, replugged the net cable to test it on another machine, then looked at ifconfig: now the eth0:avahi entry was gone, and eth0 showed an ipv6 ip, tho there was no connectivity. I ran ifup -a one more time, and this time it picked up dhcp ok and connectivity is restored (still w/ the ipv6 addr alongside the 192.168.1.105 that the router handed out). What happened? I'm worried that I lost use of my machine for a few days and don't know why or why connectivity is back. The router supported a wired conn to a Windows box and a few wireless connections ok throughout.

Any enlightenment would be appreciated.

---

### Post by photoriot on 2009-03-18
One possibility for what cleared the problem is plugging the net cable into my Windows box to test the cable - maybe Windows reset the protocol on the port.

---

