---
title: "No getting DHCP served. Avahi-daemon problem?"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2009-04-13
Hi all,

Wracking my brains here. Desktop box, was actually changing the graphics drivers around when suddenly the machine went offline. Seems unrelated but you never know. It internet connection literally just stopped working. The machine is wired to a router then to the modem etc. All is working fine on my two other machines, both of which connect to the same network. The router config can see the machine and has served an IP but Ubuntu is not picking it up. Also, when I shutdown or restart the machine, it has problems and gives some messages, one of which mentions something about not being able to close a port. They are connection related messages anyhow.

It is definitely a problem with the Ubuntu install. I have all machines dual-booting with Windows XP and when I boot into XP on the machine in question, it connects no problem. Just not in Ubuntu. Happy to send any info. This happened on my laptop awhile ago, or something similar, but I can't remember how I fixed.

When I type 'ifconfig' in a terminal, it finds everything: eth0, eth1; but also eth1:avahi which I don't think was there before. That is maybe overriding the regular port/connection? Bit hard to paste anything from that machine of course, because can't get online. Just ask and will give whatever info I can.

I have found a few things online but nothing has really pinned down the problem with a fix. From what I remember with my laptop, it turned out to be pretty simple ... 3 days later!

Any takers?


* Just to add to this ...

In the output from ifconfig, the 'lo' (loopback) section shows:

RX Packets: 661 errors
TX Packets: 661 errors

The eth0:avahi section is the only item with inet addr, bcast and mask, all the numbers relating to nothing to do with my setup (all numbers wrong). It also tells me:

Interrupt: 11

Again, the router can see and has/is serving this machine but machine seems to be attempting to pickup with the wrong device.

---

### Post by superprash2003 on 2009-04-13
post output of the following
1)ifconfig
2)sudo gedit /etc/network/interfaces ( post the contents of this file )

---

### Post by Hawk__0 on 2009-04-13
Could be your router.  unplug it and plug it back it.  That seems liek the least likely problem, but you never know.

If lo is getting errors I'd say your network card is toast, but you said you dual boot it with XP and it works?  I would try /etc/init.d/dhcpcd restart and see waht happens as well.

---

### Post by Iowan on 2009-04-13
Does that machine actually have eth0 and eth1? **ifconfig -a** or maybe **lshw -C network** should shed some light.

---

### Post by Bucky Ball on 2009-04-13
superprash2003, as explained I can't post anything from that machine but will try and provide what info I can.

Hawk0, router working perfectly, even serving an IP and the computer shows up as served with an IP in the router config. No problem there. The machine is telling me 'No persistant working leases'. In other words, it seems to be looking and not finding (possibly because eth0:avahi already has an IP, the completely wrong one and no idea where that came from).

Router works fine with the Windoze install on that same box also (and Ubuntu or XP on my 2 other machines) so rule out the router for a start.

Iowan, yes it does. Nothing plugged into eth1 though and was reasonably sure this machine was running eth0. I will get the broken box up shortly and post what I can ...

Thanks all for your responses. Hopefully we can get to the bottom of it because I haven't been having much luck on my own.

Bottom line, router served IP and not complaining (names the machine and shows correct IP for it in DHCP config section).
Computer seems to be assigning its own number on eth0:avahi and ignoring the IP the router is serving. IP out there, just not picking it up, whilst telling me eth0 and eth1 are up and ready for action.

The connection was up and fine as usual, in Synaptics I uninstalled the openchrome driver and installed the via one and this started happening. Thinking this is coincidental as these are graphics drivers, nothing to do with internet ... but you never know ...

---

### Post by Bucky Ball on 2009-04-13
Iowan, results of ifconfig -a show:

```
eth0
eth1
eth1:avahi
lo
```There are two physical ethernet ports on the machine, only one used. eth1:avahi I think is the problem as that looks like this:

```
eth1:avahi Link encap:Ethernet  HWaddr etc ...
inet addr: 169.254.5.138 Bcast: 169.254.255.255 Mask: 255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:11 Base address: etc ...
```all others are not assigned anything. IP actually served should be somewhere between 169.168.0.100 0 199, and is, the one being served as we speak is 169.168.0.101 for that machine. The mask should be 255.255.255.0

As for lshw -C network, there is a Realtek and Via ethernet (network 0 and 1). The via is on the MB and I have been using the Realtek. Let me know if you want specific info. Just posting the essentials as can't copy and paste from that machine, naturally.

---

### Post by Bucky Ball on 2009-04-13
Okay, here's what I did. Got a torch, crawled behind the machine and swapped the ethernet cable from the Realtek card to the Via ethernet port on the motherboard. ifconfig shows:

eth0
eth1
lo

... correct IP, gateway mask etc and online immediately. This doesn't get to the bottom of what happened and I haven't tried to swap back to see if this really fixed everything, but all up for now.

Maybe that realtek card is somehow faulty? Reasonably old. I will swap them back in awhile and let you know if the same thing happens.

Thanks to all. :)

---

### Post by Iowan on 2009-04-14
I'll have to go searching to find the name of the file where aliases are defined... dunno if you could manually edit it back the way it was.

EDIT: */etc/udev/rules.d/70-persistent-net.rules*

---

