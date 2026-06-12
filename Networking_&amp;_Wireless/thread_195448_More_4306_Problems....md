---
title: "More 4306 Problems..."
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by oberon on 2006-06-12
I have sorted through all of the posts on this forum (I think) about using the 43xx drivers for my 4306 wireless NIC.  I was able to extract the firmware from the wl_apsta.o driver with no errors.  Here is some output:

```
rbeale@saphira:~$ sudo dmesg | grep 43xx
[4294692.333000] bcm43xx driver
rbeale@saphira:~$
```
```
rbeale@saphira:~$ sudo lspci | grep Broad
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)rbeale@saphira:~$
```
```
rbeale@saphira:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:1f:7c:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=172.16.10.101 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:185
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:53:a8:a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-23-k7 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e0104000-e0105fff irq:217
rbeale@saphira:~$
```

I have tried setting the IP to static and dhcp, WEP inabled and disabled, set rate tp 11M and 54M.  After many reboots I think my problem is in theout put from the last command.  It shows the device as disabled.  I am not sure what else I can do to enable to device asside from the button on the front of the laptop (there is no Fn key combo on my laptop, just the button).  I know the wireless card works and that the button works.  It worked under Windows, but I can't test it in that anymore since I removed it.  No sense in having somthing that I haven't used in four months.  Oh yea, I am using a Compaq R3000 (incase that helps at all) and am using the 2.6.15-23-k7 kernel.

Thanks in advance for anyhelp!

---

### Post by oberon on 2006-06-13
Bump! :)

---

### Post by bobterri on 2006-06-13
I have the same wireless NIC in a Dell Inspiron 5360.  I used ndiswrapper.  It's working great!

---

### Post by oberon on 2006-06-14
Any other recomendations; aside from using ndiswrapper?  I would like to get it working with the bcm43xx driver if I can, but will use ndiswrapper as a last resort.

---

### Post by jhr79 on 2006-06-14
[QUOTE=oberon]Any other recomendations; aside from using ndiswrapper?  I would like to get it working with the bcm43xx driver if I can, but will use ndiswrapper as a last resort.[/QUOTE]

I'm having HP laptop with the same chip. Bcm43xx driver is working great after I added "noapic" boot parameter. Without it I couldn't get it to work even by using ndiswrapper.

BTW: I suppose you have followed the instructions in the wiki...


Jani

---

### Post by oberon on 2006-06-14
Thanks I will try setting that and see if it helps! :D   Yes; I did go through the wiki.

---

### Post by oberon on 2006-06-16
Okay, I tried that and it doen't show as disabled any more, but that is all that changed.  It still does not seem to actually function.  There are about 6 wireless networks that I can see on my wife's laptop, but "iwlist eth1 scan" shows no results.  iwconfig still show AP as invalid no matter what I do.  Any one one have any other Ideas?  It worked fine in flight 4, but after the final release I did a fresh install and is has not worked since then.  Well, it looks like I may be forced to use ndiswrapper again. :-(

---

### Post by jhr79 on 2006-06-16
[QUOTE=oberon]Okay, I tried that and it doen't show as disabled any more, but that is all that changed.  It still does not seem to actually function.  There are about 6 wireless networks that I can see on my wife's laptop, but "iwlist eth1 scan" shows no results.  iwconfig still show AP as invalid no matter what I do.  Any one one have any other Ideas?  It worked fine in flight 4, but after the final release I did a fresh install and is has not worked since then.  Well, it looks like I may be forced to use ndiswrapper again. :-([/QUOTE]

Ok, if I remember right, I had to execute following commands before using *iwlist*.

```

ifdown eth1
ifup eth1

```

After that it showed networks with *iwlist*.

---

### Post by jawrat on 2006-06-16
Try rebooting your router.  Then try a static IP.  if that works, then try dhclient ethX.  

That worked for me.  (but i'm using the bcm43xx driver)

---

### Post by oberon on 2006-06-20
So last night I was fed up and was going to load ndiswrapper, but decided to try and get it working one last time.  I removed the firmware files, commented out the config for eth1 in /etc/network/interfaces and started again.  I turned on SSID broadcast, turned off WEP and set it the b only.  I unpacked the firmware with no errors, iwlist saw it, but could not scan through the device, but for some reason this time when I tried to bring it up (ifup) network manager saw a wireless device so I tried to enable it.  Nothing happened.  I exited NM and then proceeded to configure the device manually.  After bringing the interface down and back up with just the basic config uncommented I was able to scan.  Needless to say it works now.  I have no idea why, I did everything the exact same way I did before with the same driver file for the firmware.  Anyway, thanks for the responses and help.

-oberon

-edit- Oh, yea it works fine at 54M with WEP enabled! :-)

---

