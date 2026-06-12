---
title: "Broadcom problems"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Trevor Johnston on 2009-11-10
I have been looking for a solution to my problem but have found nothing equaling my same state. I have broadcom 4312 card and the restricted driver is installed /lib/firmware/b43 and /lib/firmware/b43legacy are both there. My system is up to date and all that stuff, but for some reason I don't have any wlan options, the two computers in the top right don't even appear so I can't tell it to connect to anything.... please help ^.^

---

### Post by t0mppa on 2009-11-10
Would help if you could provide a little more information about the issue. Namely the output of following commands from terminal would help:```
lshw -C network
dmesg | grep b43
sudo iwlist scanning
ps ax | grep nm-applet
```

---

### Post by Trevor Johnston on 2009-11-10
here ya go,
```

trevor@trevor-laptop:~$ sudo iwlist scanning 
[sudo] password for trevor: 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

```
```

trevor@trevor-laptop:~$ lshw -c network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: 82567LM Gigabit Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 03 
       serial: 00:21:70:d0:3c:57 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.7-7 latency=0 multicast=yes 
       resources: irq:30 memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32) 
  *-network 
       description: Network controller 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:17 memory:f1ffc000-f1ffffff 

```
```

trevor@trevor-laptop:~$ ps as | grep nm-applet
1752?       S   0:00 nm-applet --sm-disable
2350 pts/0  S+  0:00 grep --color=auto nm-applet

```
```

trevor@trevor-laptop:~$ dmesg | grep b43
[ 3.370375]b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3.370391]b43-pci-bridge 0000:0c:00.0: setting latency to 64
[ 8.244919]b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[ 8.292093]b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[ 8.292132]b43: probe of ssb0:0 failed with error -95
[ 297.620472]b43-pci-bridge 0000:0c:00.0: PCI INT A disabled
[ 298.353705]b43-pci-bridge 0000:0c:00.0: restoring config space at offset  0xf(was 0x100, writing 0x10a)
[ 298.353764]b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x4(was 0x4, writing 0xf1ffc004)
[ 298.353764]b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x3(was 0x0, writing 0x10)
[ 298.353792]b43-pci-bridge 0000:0c:00.0: restoring config space at offset 0x1(was 0x4, writing 0x100106)
[ 299.053639]b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

```

gah, lots of typing :D.

---

### Post by t0mppa on 2009-11-10
> **Trevor Johnston said:**
> gah, lots of typing :D. 

Sorry, just didn't which of the four would show the important details, each had a chance to, depending on what was wrong.

> **Trevor Johnston said:**
> [ 8.244919]b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[ 8.292093]b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)


The revision of the 4312 that you have isn't yet supported by the b43 drivers (all others are though). You'll have to use the Broadcom STA to get your card working.

It used to show up on System / Administration / Hardware Drivers back on Jaunty, but I'm not sure if it does anymore, as I don't have a box with a Broadcom wireless card at the moment. If it isn't there, you can just install *bcmwl-kernel-source*, that's the package that holds it in Karmic.

---

### Post by Trevor Johnston on 2009-11-10
Sta does show up on the hardware drivers list so I'll have to try that, is there anything else I should do once I hit activate?

---

### Post by t0mppa on 2009-11-10
Nope, that should be it. Just keep a connection active through your wired when you press activate, so that if it wants to download something there's no problems with that.

---

### Post by Trevor Johnston on 2009-11-10
Yay, I'm not sure why this was so difficult for me before but that was intensly simplistic and now it works like Ubuntu should work. YAY!!! ^.^ I can't conceal my appreciation for your help, so ya... THANKEE SAI <333 I will rear your children for you.... just kidding. But ya, thanks.

---

### Post by Trevor Johnston on 2009-11-10
By the way, these two replies are in fact from karmic koala ^.^

---

