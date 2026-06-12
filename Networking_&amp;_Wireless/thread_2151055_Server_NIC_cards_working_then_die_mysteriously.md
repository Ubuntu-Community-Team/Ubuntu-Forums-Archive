---
title: "Server NIC cards working then die mysteriously"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by hawaiiman on 2013-06-03
Ubuntu server at my school. Clients running XP. Onboard Realtek LAN (gigabit) eth0 and added Realtek gigabit card for eth1. Everything worked fine for 6-7 months, the eth0 stopped transmitting packets. Added another NIC eth3, and edited /etc/networks to read eth3 where eth0 had been. eth3 works fine, but at some point (server sat idle for quite a while) eth1 stopped transmitting also. I can bypass the server and DHCP etc. from our modem/router, but we lose some functionality. Is it possible for a virus in a client machine to attack the NIC in a Ubuntu machine? all the NICS run the same Realtek driver, BTW, and the machine is on a UPS

---

### Post by VinDSL on 2013-06-03
Without knowing more about your server...

I do a lot of testing (of new releases) and can tell you that I've run across periods where I suffered spontaneous NIC disconnects.

Usually this was due to Network Manager (NM) upgrades.  The immediate cure was always -- remove NM and install WiCD.

* You cannot run two network managers at the same time. ;)

That's on the software side of things.  On the hardware side...

Recent kernel upgrades started playing havoc on my ancient iron.  Newer kernels didn't care for my pseudo, southbridge-driven, Lan chipset.

The long-term fix, was to install a NIC that was supported. in my case, I installed a Netgear PCI Ethernet card with a real DEC "Tulip" chipset, e.g. none of this cheapskate, pseudo device nonsense.

Haven't had a problem ever since -- knock on wood.

Anyway, hope that gives you some ideas...

Good luck!

---

### Post by hawaiiman on 2013-06-03
@VinDSL, thanks, but this machine has been doing fine for 6-7 months. The NICS work fine receiving packets, and the newly installed NIC which is same brand and same driver also works fine.

---

### Post by hawaiiman on 2013-06-06
VinDSL...Hey, I think you hit it on the NM upgrade. Cards work fine in another machine. I rexall how many painful weeks it took me to get this thing to fly. A lot of had to do with conflicts with NM. Everything is backed up once a week, but at this point I'm feeling very cautious about how to proceed. Starting over....ugghhh. It would be easy if there were other nic cards available here in the wild of N.E. Thailand, but there aren't. Wicd? Not familiar. Having nightmares of starting a snowball of conflicts with my dhcp or elsewhere.

---

### Post by VinDSL on 2013-06-06
> **hawaiiman said:**
> VinDSL...Hey, I think you hit it on the NM upgrade. Cards work fine in another machine. I rexall how many painful weeks it took me to get this thing to fly. A lot of had to do with conflicts with NM. Everything is backed up once a week, but at this point I'm feeling very cautious about how to proceed. Starting over....ugghhh. It would be easy if there were other nic cards available here in the wild of N.E. Thailand, but there aren't. Wicd? Not familiar. Having nightmares of starting a snowball of conflicts with my dhcp or elsewhere.
Good. Sounds like you're headed down the right path.

We're fortunate to have a place called "Goodwill Industries" AKA "Willy's" here in the USA.  They resell things that ppl would otherwise throw away -- unwanted items, left over from "yard sales" -- things that are donated to them through charity.  I haven't bought a new router, switch, keyboard, NIC, et cetera in years.  I pick used ones at Willy's for pennies on the wholesale dollar.  LoL!  :D

Good used NICS, with real chipsets, can usually be had for $4.00-$5.00 USD.  No kidding.

[WiCD]("https://launchpad.net/wicd") has been a drop-in NM replacement for me, on desktop/mobile machines.  Never tried it on a server, but...

The only reason I run NM is because I'm supposed to be testing Ubu dev releases.  Doesn't do anybody (except myself) any good, if I'm using something that isn't included in the official release, you know?

Switching over to WiCD is easy.  I just download the most recent WiCD, in advance.  Remove NM.  Install WiCD. And, reboot.

To switch back to NM, I just do the opposite.

In the past, when there were conflicts with NM, I would switch back n' forth every day (after doing daily upgrades) to see if NM had started working yet.

It's been a relatively painless process.  WiCD works every time.  NM is a crap shoot.

Anyway, I don't want to talk you into something you're not comfortable doing.  Just trying to give you some ideas, based on personal experience(s).  ;)

---

