---
title: "Losing network connectivity at random on Ubuntu Server 9.10"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by mellowd on 2010-01-24
It's certainly been a while since I've posted here. Hello all again.


I've been having strange problems with my server recently. At least twice a week I lose all connectivity to it. I have to switch it off and on again to get it working. It's a headless server with no keyboard or monitor attached. Switching it off certainly isn't graceful, which is why I want to try and fix the problem.

I'm running Server 9.10 32-bit. Moblock is running all the time and I have rtorrent running most of the time as well.

It happened again this morning, and I've got this in var/log/messages. There are tons of these entries:

```
Jan 24 08:31:58 simba kernel: [138718.000181] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jan 24 08:31:58 simba kernel: [138718.000850] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jan 24 08:32:16 simba kernel: [138736.000185] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jan 24 08:32:16 simba kernel: [138736.000855] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jan 24 08:32:32 simba kernel: [138752.000187] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jan 24 08:32:32 simba kernel: [138752.000862] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jan 24 08:32:48 simba kernel: [138768.000183] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jan 24 08:32:48 simba kernel: [138768.000278] via-rhine: Reset not complete yet. Trying harder.
Jan 24 08:32:48 simba kernel: [138768.000858] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jan 24 08:33:06 simba kernel: [138786.000181] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
```

This continued up until I hard shut the server and switched it on again.

The only other entry in var/log/messages is the very first line:

```
Jan 24 06:52:30 simba rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="516" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 24 06:52:42 simba kernel: [132762.000168] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
Jan 24 06:52:42 simba kernel: [132762.000275] via-rhine: Reset not complete yet. Trying harder.
Jan 24 06:52:42 simba kernel: [132762.000857] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Jan 24 06:53:00 simba kernel: [132780.000164] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
```

Anyone got any ideas? I've run 8.04, 8.10, 9.04 and 9.10 for ages with 0 problems. It's only been recently that this has been happening. I think it may have something to do with 9.10, or at least an application or driver of sorts.

---

### Post by mellowd on 2010-01-25
No-one got any ideas?

---

### Post by mellowd on 2010-02-02
bump

---

### Post by jre on 2010-02-03
To rule out any MoBlock related problems you should check /var/log/moblock.log. But I can't think of anything being blocked that explains those symptoms.

So I was curious and searched the web for 
```
"th0: Transmit timed out, status 0003, PHY status 786d, resetting..."
```

All reports also had the Via Rhine network card. So basically this card is not supported very well (or with other words Via doesn't support Linux very well!?!). Possible solutions therefore are within the kernel (and related hardware management) and the BIOS (because this decides which (non-)options the kernel has to manage the hardware).

Here is a bug report which also relates to Ubuntu 9.10:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454747](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454747)
Last post in that thread indicates this might be fixed in kernel 2.6.33


In some (other) cases the reason was that the machine erroneously thinks some network IRQ isn't needed any more and so switches it off. Don't ask me for details, I don't know that stuff. The solution then was to disable APIC in the BIOS, or to switch the BIOS to "fail-safe", or to change the boot line in grub to boot with APIC disabled. So this might be a helpful workaround.

I think it is possible that some recent software update just lead to this problematic hardware situation. Did the problems start with the last kernel update?

Of course, if you are unlucky your hardware is just broken.

Good luck!

---

### Post by mellowd on 2010-02-03
Thanks for the reply!

It could've started with an upgrade. I upgrade reguarly as it's just a home server. I'll have a look at the bios and see if changing the power settings change anything (though the problem is so sporadic to begin with)

I might just throw in a new nic and disable the onboard nic.

I'll let you know if anything changes

---

### Post by Zimmernuts on 2010-02-03
Hey Mellow.

I am having a similar problem.  I have no solutions, but maybe my observations can help someone figure out a solution.

I to have a Via Rhine onboard nic.  I have a new install of Ubuntu Server 9.10, so I have not upgraded into this problem.  I want this server to be a file server, so I have been transfering files to it.  It seems to loose connection faster when I'm transferring files (within 60 minutes but different each time).  If I am not transfering files, it will stay up for hours.

I also have been pinging the server when transfering files lately so I can see exactly when it goes down,  If I walk over to the keyboard attached to it and press any key on the keyboard, my pings will suddenly respond.  I would be interested to know if you plug in a keyboard, if yours comes back to life as well without a hard reboot.

Also I don't think it is a nic problem as in it going to sleep.  I have a switched plugged in right next to the server.  The link lights never change, so it almost seems like some kind of layer 3 networking problem?

I plan on trying witnout APIC when I get a chance or maybe trying an add in nic.  I will also check out my /var/log/messages.  When I ran tail on those before I did not see anything special, but maybe I need to look through the whole log.

---

### Post by dmizer on 2010-02-03
Please post the output of:
```
lshw -C network
```

---

### Post by Zimmernuts on 2010-02-04
I don't mean to hijack this thread.  I'm not looking to step on anyone's toes.  So I hope no one takes my posts the wrong way.  I'm just adding my input and hopefully it will help.

Also for reference the motherboard is an MSI KM2M (MS 6738) with a Via KM266 northbridge and VT8235 southbridge.

The output of the command is... 

 *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:76:e4:80:7d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=10.1.1.15 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:b800(size=256) memory:e0182000-e01820ff


I just disabled APIC in my BIOS and will be trying to transfer some files, I'll pass along the outcome.

---

### Post by mellowd on 2010-02-05
Feel free if your issue is the same as mine. It might help

---

