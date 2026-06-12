---
title: "Wired network breaks when idle"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by Steven_B on 2010-02-26
I'm having a problem where the wired network wired network (eth0) disconnects when the connection is idle for a while (usually tens of minutes).  It works fine every time I boot up, but eventually it dies, and I can't ping the machine, or ping anything from the machine.  
ifconfig shows that it still has an IP address.  Running ifdown/ifup causes it to work again.  I intend for this machine to be a server, so I can't afford to go restart it when I need network access.

sudo lshw -class network gives me this:
```
 *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0c:76:13:48:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=10.52.30.179 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:ec002000-ec002fff ioport:d000(size=8)

```

I'm running Ubuntu server, so there's no NetworkManager.  I've tried this on two different network connections with different cables, so I don't think it's a problem with one specific router or cable.

Thanks in advance for your help.

---

### Post by Iowan on 2010-02-27
You've checked the power management and BIOS settings?

---

### Post by pjf.weeks on 2010-02-28
I'm having the exact same problem. Works fine while active, then once idle, connection properties switch back and forth from "Status: Sending" to "Status: Idle". No receiving any packets.

```
*-network
        description: Ethernet interface
        product: nVidia Corporation
        vendor: nVidia Corporation
        physical id: a
        bus info: pci@0000:00:0a.0
        logical name: eth0
        version: a2
        serial: 00:21:85:63:96:e8
        size: 100MB/s
        capacity: 1GB/s
        width: 32 bits
        clock: 66MHz
        capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10 bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=142.2.159.165 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
*-network DISABLED
        description: Ethernet interface
        physical id: 1
        logical name: vboxnet0
        serial: 0a:00:27:00:00:00
        capabilities: ethernet physical
        configuration: broadcast=yes multicast=yes
```

---

### Post by Steven_B on 2010-02-28
> **Iowan said:**
> You've checked the power management and BIOS settings?
I didn't see anything relevant to the network card and power management in the BIOS.  I tried adding the boot parameter apic=off in Grub, but that didn't seem to have fixed anything.  Is there somewhere else I should look for power management settings?  It's a desktop running without a GUI, so I didn't think there was much power management involved.

It's possible the hardware is just flaky, but the problem can always be fixed by restarting the computer or running "sudo ifdown eth0; sudo ifup eth0", which makes me think it's an Ubuntu bug.

---

### Post by Steven_B on 2010-03-24
Just an update:
I tried using Ubuntu desktop; same results.  I also tried a 2-year-old Knoppix CD, and it seemed to have the same problem.
I'm using Fedora now, and it seems to be working.  My best guess it that this is a Debian bug.

---

