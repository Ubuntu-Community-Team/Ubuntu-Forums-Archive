---
title: "ipw2100 failing to start - Intel Pro/Wireless 2100 3B"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by iGoogle on 2012-05-03
Hi all,

I've scoured these boards for help on this, but so far, no luck. Hopefully someone has a solution.

I have done a fresh install of Ubuntu 10.04 Lucid Lynx on a laptop with the Intel Pro/Wireless 2100 3B mini pci card. I am using the 2.6.32.41-generic kernel.

I cannot get the wireless card to work.

lspci:
```
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0d:56:37:ca:69  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe37:ca69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14399 errors:15 dropped:7 overruns:0 frame:0
          TX packets:9515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18489040 (18.4 MB)  TX bytes:1177265 (1.1 MB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9928 (9.9 KB)  TX bytes:9928 (9.9 KB)
```

sudo lshw -C Network:
```
*-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:37:ca:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.104 latency=32 multicast=yes
       resources: irq:7 memory:faffe000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32 maxlatency=34 mingnt=2
       resources: memory:faffd000-faffdfff
```

dmesg | grep ipw2100:
```
 1036.513756] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[ 1036.513762] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[ 1036.516636] ipw2100 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 1036.517988] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[ 1036.518026] ipw2100 0000:02:02.0: firmware: requesting ipw2100-1.3.fw
[ 1036.540490] ipw2100: eth1: Error initializing Symbol
[ 1036.540499] ipw2100: eth1: Error loading microcode: -5
[ 1036.556121] ipw2100: eth1: Failed to power on the adapter.
[ 1036.556131] ipw2100: eth1: Failed to start the firmware.
[ 1036.556137] ipw2100Error calling register_netdev.
[ 1036.556497] ipw2100 0000:02:02.0: PCI INT A disabled
[ 1036.556520] ipw2100: probe of 0000:02:02.0 failed with error -5
```

From what I have read, I'm guessing that the firmware is failing to start up the wireless card.

The ipw2100 firmware files that came with this copy of Ubuntu are at /lib/firmware/, but I have also downloaded firmware from [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/) and unpacked to /lib/firmware/2.6.32.41-generic/

I then tried:

sudo rmmod ipw2100
sudo modprobe ipw2100

but no luck.

lsmod | grep ipw2100:
```
ipw2100                66395  0 
libipw                 39896  1 ipw2100
```

Hopefully someone can point me in the right direction on this.

Thanks.

---

### Post by chili555 on 2012-05-04
> firmware: requesting ipw2100-1.3.fwDo you have that exact firmware?```
ls /lib/firmware | grep ipw2100
```What is its md5sum?```
md5sum /lib/firmware/ipw2100-1.3.fw
md5sum /lib/firmware/2.6.32.41-generic/ipw2100-1.3.fw
```Mine is:```
dc1cece9f906f57a98f5a3859dba3e28  /lib/firmware/ipw2100-1.3.fw

```If yours is different, it may be corrupted or an earlier vesion.

If it's not correct, I can attach mine.

---

### Post by iGoogle on 2012-05-05
Thanks for helping chili.

Yes, I have that exact version firmware...

ls /lib/firwmare/ | grep ipw2100:
```
ipw2100-1.3.fw
ipw2100-1.3-i.fw
ipw2100-1.3-p.fw
```

And my md5sum's match, and also match yours...

md5sum /lib/firwmare/ipw2100-1.3.fw:
```
dc1cece9f906f57a98f5a3859dba3e28  /lib/firmware/ipw2100-1.3.fw
```

md5sum /lib/firwmare/2.6.32-41-generic/ipw2100-1.3.fw:
```
dc1cece9f906f57a98f5a3859dba3e28  /lib/firmware/2.6.32-41-generic/ipw2100-1.3.fw
```

Can you think of anything else worth checking? Thanks.

---

### Post by chili555 on 2012-05-05
> Can you think of anything else worth checking?I have googled this extensively and I see quite a few repetitions of the same message but no solutions. You could try linux-backports-modules or ndiswrapper, but googling reveals no instance of a fix that I could find.

You might download a copy of Ubuntu 12.04 and try the live CD and see if the dmesg is the same. You might, if you have not already, do a full update and see if a later linux-image has an updated driver.

I don't discount the possibility that the hardware is old and tired. If you decide to swap in another card, be sure you check on 'whitelists.' Of course, many good USB wireless devices are available for US$10-15.

---

### Post by iGoogle on 2012-05-05
Tried the Live CD with the latest Ubuntu, but same result.

No luck with linux-backports-modules either.

ndiswrapper and the Intel driver does bring the wireless card to life however.

Still don't know why it doesn't work with the included firmware, but ndiswrapper will have to do!

Thanks for your help.

---

### Post by jrz on 2012-07-19
I'm having the same problem on an IBM ThinkPad R40 with ipw2100 connecting and dropping intermittantly. Googling finds complaints, but no solutions, as far back as 2005 although I didn't have a problem until several months ago, and sometimes it works for weeks without a problem and then all of a sudden it drops connection dozens of times a day. Rebooting doesn't appear to help.
After a reboot dmesg always shows the same output and I can usually click the CONNECT button on wicd and get a connection for an undetermined amount of time before it disconnects.

ADDRCONF (NETDEV_UP): eth1: link is not ready
ADDRCONF (NETDEV_UP): eth1: link is not ready
ADDRCONF (NETDEV_UP): eth0: link is not ready
ADDRCONF (NETDEV_UP): eth1: link is not ready
ADDRCONF (NETDEV_CHANGE): eth1: link becomes ready
eth1: no IPv6 routers present
ipw2100: Fatal interrupt, Scheduling firmware restart.
ipw2100: Fatal interrupt, Scheduling firmware restart.
ipw2100: Fatal interrupt, Scheduling firmware restart.
ipw2100: Fatal interrupt, Scheduling firmware restart.
ipw2100: Fatal interrupt, Scheduling firmware restart.
ADDRCONF (NETDEV_UP): eth0: link is not ready
eth1: no IPv6 routers present

Since this seems to have been a problem for at least 7 years now, is it likely to get any attention, or just remain something we have to live with?

---

### Post by chili555 on 2012-07-19
> Since this seems to have been a problem for at least 7 years now, is it likely to get any attention, or just remain something we have to live with?Having worked on wireless drivers at this forum for many years, my strong belief is that it's a relatively rare and not readily reproducible problem. It may be caused by heat or age of your device. If it were me, I'd get a newer device on the R40's whitelist and get rid of the IPW 2100. There are also many US$10-15 USB devices available.

---

### Post by jrz on 2012-07-21
As it appears there is little interest in fixing this problem, I do have a work around which in my case is better than having no wireless connection at all. It only works if your ipw2100 will connect but not remain connected for any great length of time. I use Wicd rather than Network manager, and have also installed wicd-cli. I keep a terminal open  running the command:

while true; do wicd-cli --wireless -n 0 -c; sleep 150; done

While it may not be an elegant solution, it does provide me with a usable wireless Internet connection.

I only wish it were possible where I live to run to a store and purchase a piece of compatible hardware whenever something didn't work. If my hardware was the problem, I think it would also fail running Windows XP, which it does, but then I don't have access to all the programs I work with, plus my WinXP is difficult to use as all the menus are in a foreign language.

If anyone knows of where this problem is getting any attention, please post it here and I will move my attention to that location. I'm of the opinion that it may be something to do with the kernel and older mother boards (non-APIC) using shared IRQ's, although I've played around with IRQ's in BIOS to no avail.

As a note:  I was unable to get Network Manager to recognize the wireless at all, and only Wicd seemed to recognize it. That was found to be the situation in earlier distributions of Ubuntu also, causing me to replace Network Manager with Wicd each time I did a fresh install.

---

### Post by kuffu on 2012-09-25
> **iGoogle said:**
> Hi all,

The ipw2100 firmware files that came with this copy of Ubuntu are at /lib/firmware/, but I have also downloaded firmware from [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/) and unpacked to /lib/firmware/2.6.32.41-generic/

I then tried:

sudo rmmod ipw2100
sudo modprobe ipw2100

but no luck.

lsmod | grep ipw2100:
```
ipw2100                66395  0 
libipw                 39896  1 ipw2100
```Hopefully someone can point me in the right direction on this.

Thanks.
hi
i had the same issue on a ibm thinkpad x40, upgrade from ubuntu 11.10 (i think) to last release
wireless stopped working, trying to get ip address, dropped connexion, and so on
wireless adapter intel 2100, all as in the previous post

the only extra action (after copying files to /lib/firmware/3.2.0-23.generic) was to replace the files  in /lib/firmware with those downloaded above.

i suspect the upgrade added a new set of ipw2100 drivers on /lib/firmware which were not good.

my laptop is maybe 7-8 old, but always worked so i do not believe in hw failure.

so shorter story
1/ download from link in the quote
2/ delete all ipw2100 from /lib/firmware (or better backup somewhere)
3/ unpack the files to /lib/firmware and maybe need to do the same on /lib/firmware/3.2.....
   verison i have now for ipw2100 is from 2004 september

4/ modprobe ipw2100

hope it helps.
regards
kuffu

---

