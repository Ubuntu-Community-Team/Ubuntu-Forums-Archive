---
title: "sometimes (randomly?) there is no eth0 even with ifconfig -a"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by ruquay on 2011-01-05
**UPDATE: I have since discovered that this was a hardware problem. My ethernet will not show on the first boot of the day (or when not having booted "a long time").  It's so typical of me to never suspect hardware, this problem occurs in every Linux variant I've got installed an also Windows 7.**

After having upgraded to maverick (I suppose it may be unrelated, but I'm suspicious it had to do with the upgrade), I started noticing some funny behaviour with networking.  This is a desktop plugged into ethernet built into the motherboard, no other ethernet interfaces available.

What happens is that something along the lines of "half the time", there is no eth0.  Not even when I run ifconfig -a.  And also nothing when I run sudo lshw -C network.

I even ran sudo lshw | less and slowly scrolled through the output to make sure I wasn't missing anything.

Here is the output of sudo lshw -C network right now, when it is working.

```
  *-network               
       description: Ethernet interface
       product: 82578DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: e0:cb:4e:a1:2c:28
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=0.10-5 ip=192.168.2.106 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:48 memory:f9ec0000-f9edffff memory:f9efc000-f9efcfff ioport:dc00(size=32)

```

I have tried searching Google for "eth0 missing sometimes", etc., but have only run into solutions involving something like extra outdated entries in the udev rules, or something wrong in /etc/network/interfaces (when I edited that to be static, still nothing, only error that eth0 can't be accessed).  So, I don't know what to do other than reboot, log in, and see if eth0 is detected on the next go around.

Oh, and by the way, the problem annoyed me so much that I did a fresh install of maverick, wiping everything other than my /home/ which is mounted from a different drive.  Still no luck.

I would appreciate any help with this!

---

### Post by PatchesTheCaveman on 2011-01-05
Did you run updates on it?  There's a broken kernel update on Maverick that's causing problems with many devices.

Run ```
uname -r
``` to check.  If it responds with *2.6.35-24-generic* you have the faulty update.

If not, try updating your network card drivers.  Run ```
sudo apt-get update
sudo apt-get install linux-backports-modules-net-generic
``` to do that

---

### Post by ruquay on 2011-01-06
I do indeed have the faulty kernel update.  I will select the previous kernel when booting, and find out how to set it as the standard to be selected in grub.

Thanks so much for your help!

---

