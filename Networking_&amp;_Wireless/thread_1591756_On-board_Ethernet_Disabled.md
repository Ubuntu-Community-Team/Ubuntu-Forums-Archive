---
title: "On-board Ethernet Disabled"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by sjhaffner on 2010-10-09
I have an on-board Ethernet controller that is disabled, and I can't find out how to enable it. How do I enable the on-board controller?

---

### Post by Iowan on 2010-10-09
Verify that it's enabled in the BIOS. What is the chipset?

---

### Post by scrooge_74 on 2010-10-09
> **Iowan said:**
> Verify that it's enabled in the BIOS. What is the chipset?

+1

A friend had same problem a few weeks ago (and he was running Win 7) was just a matter of going into the BIOS to fix it

---

### Post by sjhaffner on 2010-10-09
No, nothing in my bios changed because it used to work, and i haven't gone into my bios since then.  


This is what lshw said about the controller:


[INDENT]Ethernet interface
/0/100/7/0


product: RTL8111/8168B PCI Express Gigabit Ethernet controller [10EC:8168]
vendor: Realtek Semiconductor Co., Ltd. [10EC]
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 27:27:27:27:27:27
size: 10MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities:
    Power Management,
    Message Signalled Interrupts,
    PCI Express,
    MSI-X,
    Vital Product Data,
    bus mastering,
    PCI capabilities listing,
    extension ROM,
    ethernet,
    Physical interface,
    twisted pair,
    Media Independent Interface,
    10MB/s,
    10MB/s (full duplex),
    100MB/s,
    100MB/s (full duplex),
    1GB/s,
    1GB/s (full duplex),
    Auto-negotiation
configuration:
    autonegotiation: on
    broadcast: yes
    driver: r8169
    driverversion: 2.3LK-NAPI
    duplex: half
    latency: 0
    link: yes
    multicast: yes
    port: MII
    speed: 10MB/s
resources:
    irq: 41
    ioport: d800(size=256)
    memory: fdfff000-fdffffff
    memory: fdfe0000-fdfeffff
    memory: feaf0000-feafffff
this device has been disabled
[/INDENT]Thanks for any help!

---

### Post by bkratz on 2010-10-09
You might want to look at this bug report-esp. the last post

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)

---

### Post by sjhaffner on 2010-10-09
> **bkratz said:**
> You might want to look at this bug report-esp. the last post

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)


Umm, I don't know what I'm supposed to find there... 

I'm not very tech-savvy so I don't understand most of the stuff on there. 

thanks!

---

### Post by bkratz on 2010-10-09
Apparently a lot of people have had problems with this device, the last post says that 8 hours ago a fix was released. Don't know how long it will take to get in the updates though.

---

### Post by sjhaffner on 2010-10-10
> **bkratz said:**
> Apparently a lot of people have had problems with this device, the last post says that 8 hours ago a fix was released. Don't know how long it will take to get in the updates though.
Hmm, thanks! hopefully that will fix my problem!

---

### Post by dineshs on 2010-10-11
Have you seen this?  [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

---

### Post by sjhaffner on 2010-10-17
> **dineshs said:**
> Have you seen this?  [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

I just tried that but, sadly it didn't work. I'm thinking that it got fried because the address for that device is cf:cf:cf:cf:cf which i don't think is right.

Thanks for all the help though

---

### Post by sjhaffner on 2010-10-27
I had to reinstall because my hard drive crashed, and now my on-board Ethernet works! Thanks for all the suggestions!

---

