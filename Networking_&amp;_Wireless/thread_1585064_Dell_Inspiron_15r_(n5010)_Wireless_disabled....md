---
title: "Dell Inspiron 15r (n5010) Wireless disabled...?"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by ZacharyD on 2010-09-30
Hey guys, i have to say that i'm not too familiar with Ubuntu... or Linux in general . I've installed it once, just to test it out but I didn't know how to use it so i just reinstalled windows. The other night, i was bored and decided i wanted to re-try Ubuntu and to my suprise, i found Wubi. I love ubuntu now and i made the decision to permanently switch over to ubuntu.

At first, my wireless wasn't working, but there was a quick fix. All i had to do was go to the Synaptic Package Manager, Reload, and search for "Broadcom." I installed the Broadcom STA Wireless driver and i was online within a couple of minutes. I then played around for a couple of hours before turning my laptop off. But, this morning, when i turned it back on...I coudlnt' connect. When i click the little connection icon in the top right, i see the message "Wireless is disabled".

There is a key on my computer that turns the wireless card on or off, and i have tried it. It doesn't work. I have reinstalled the broadcom driver and it doesn't work. I've rebooted...And it doesn't work. I don't know enough about linux to get a solution and every other solution i find on the internet doesn't work.

I have seen in other threads that you guys usually ask for a a couple of things from the user. ifconfig and the sudo lshw -C network so i have included them below. I also looked into the ubuntu help documentation and it told me to do the lspci command. It may help you guys. 

With any solution you give me, can you explain how it works so i can at least learn from it? ;)


ifconfig
```
eth0      Link encap:Ethernet  HWaddr a4:ba:db:d1:61:c2  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:fed1:61c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19214356 (19.2 MB)  TX bytes:2598410 (2.5 MB)
          Interrupt:32 Base address:0xc000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10072 (10.0 KB)  TX bytes:10072 (10.0 KB)

```sudo lshw -c network
```

zach@ubuntu:~$ sudo lshw -c network
[sudo] password for zach:
  *-network DISABLED      
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: eth1
       version: 01
       serial: 70:f1:a1:af:82:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fbc00000-fbc03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: a4:ba:db:d1:61:c2
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.68 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:32 ioport:e000(size=256) memory:d0b10000-d0b10fff(prefetchable) memory:d0b00000-d0b0ffff(prefetchable) memory:fb200000-fb21ffff(prefetchable)

```lspci -v | less
```

12:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
        Subsystem: Dell Device 0010
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fbc00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information <?>
        Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [13c] Virtual Channel <?>
        Capabilities: [160] Device Serial Number f1-70-af-ff-ff-a1-00-00
        Capabilities: [16c] Power Budgeting <?>
        Kernel driver in use: wl
        Kernel modules: wl

```Hopefully you guys can help me. I'm willing to give you guys whatever else you guys need.

Please advise,
Zach.

---

### Post by ZacharyD on 2010-09-30
Sorry for tripple post, but nobody knows a fix? :O

---

### Post by mbeltagy on 2010-10-03
I don't know if this will help, but I have come across a post showing that for some wireless cards that you need to first boot in windows and then reboot in linux for it work. 

See [http://ubuntuforums.org/showthread.php?t=894548](http://ubuntuforums.org/showthread.php?t=894548)

Try doing that and see it works.

---

### Post by mbeltagy on 2010-10-05
Here is another thing you could try... 
```

sudo ifconfig eth1 up

```
That should wakeup your wireless card. 
When you are done, share with us the output of 
```

sudo ifconfig 

```

---

### Post by chili555 on 2010-11-29
First of all, Network Manager is designed to disallow a wireless connection if you have wired, which you do:> eth0      Link encap:Ethernet  HWaddr a4:ba:db:d1:61:c2  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
Please detach the ethernet cable for a few minutes before you proceed.

Second, the module dell-laptop sometimes does not correctly translate key presses to useful activity. Let's unload it and see if we can get the wireless to come to life. Please do:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
iwconfig
```Is your wireless working now? If so, we can permanently block the module with:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by zanuxzan on 2011-04-19
Perhaps its worth noting that on my 15r (N5110) I have a Intel Wireless-N 1030 and it took some searching to find what was/is a rather simple solution.

See my post at [http://ubuntuforums.org/showpost.php?p=10694483&postcount=9](http://ubuntuforums.org/showpost.php?p=10694483&postcount=9)

---

