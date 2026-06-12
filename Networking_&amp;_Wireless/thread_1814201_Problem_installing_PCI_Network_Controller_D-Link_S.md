---
title: "Problem installing PCI Network Controller D-Link System Inc AirPlus G DWL-G510"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by gxHL on 2011-07-29
I'm having trouble installing my DWL-G510. Found some old guides but the links aren't alive anymore and found this one but can't understand it. [https://help.ubuntu.com/community/WifiDocs/DWL-G510](https://help.ubuntu.com/community/WifiDocs/DWL-G510)

Have in mind that i have dual boot machine with windows 7 and ubuntu 10.04.My WLAN card works only in windows 7 and i don't have any internet connection within ubuntu.

More info:
```
ar@ar-d:~$ sudo lshw -C network
[sudo] password for ar: 
  *-network               
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wlan0
       version: 00
       serial: 00:26:5a:6d:29:3b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fcff8000-fcffffff
  *-network
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:23:54:62:ff:a0
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:28 memory:fce7c000-fce7cfff ioport:b880(size=8) memory:fce7f400-fce7f4ff memory:fce7f000-fce7f00f
```Any help appreciated.

---

### Post by varunendra on 2011-07-29
> **gxHL said:**
> I'm having trouble installing my DWL-G510. Found some old guides but the links aren't alive anymore and found this one but can't understand it. [https://help.ubuntu.com/community/WifiDocs/DWL-G510](https://help.ubuntu.com/community/WifiDocs/DWL-G510)
..
..
More info:
```
ar@ar-d:~$ sudo lshw -C network
[sudo] password for ar: 
  *-network               
       description: Wireless interface
       product: **RT2561/RT61** rev B 802.11g
       vendor: **RaLink**
       configuration: broadcast=yes **driver=rt61pci **..
..
..
```
Apparently, your adapter seems a common one and a suitable driver module has already been loaded for it. The loaded driver **rt61pci **used to have problems in the past but I think it has been fixed in newer kernels and is not a problem anymore.

So at this point, I don't think you need to install any other drivers. The link you referred points to a guide which is rather old (last edited 2008-07-24) and shouldn't be required with 10.04. Although it seems quite easy to follow if so required.

For now, please tell us the nature of problem you are having. Are you just having problem in connecting to a network, or can't see a network at all.

---

### Post by gxHL on 2011-07-29
Ubuntu isn't able to find the wireless network so i can't connect...
I can see the wireless networking button up in the screen but there are no networks to connect to.

---

### Post by varunendra on 2011-07-29
Please post outputs of:
```
ifconfig -a
```
```
iwconfig
```
```
rfkill list all
```

Besides, when you right-click on the NetworkManager applet in the panel, do you see "Enable Networking" as 'checked'?

---

### Post by gxHL on 2011-07-29
Yes it is checked.


```
ar@ar-d:~$ **ifconfig -a**

eth0      Link encap:Ethernet  HWaddr 00:23:54:62:ff:a0  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:28 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:84 errors:0 dropped:0 overruns:0 frame:0

          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:6408 (6.4 KB)  TX bytes:6408 (6.4 KB)



wlan0     Link encap:Ethernet  HWaddr 00:26:5a:6d:29:3b  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ar@ar-d:~$ **iwconfig**

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off


ar@ar-d:~$ **rfkill list all**

0: phy0: Wireless LAN

    Soft blocked: no

    Hard blocked: no

```

---

### Post by varunendra on 2011-07-29
Everything seems normal there. Please post the output of:
```
dmesg | grep wlan0
```

Can you temporarily connect via Ethernet? If it is a driver problem, maybe an update could fix it. Else we may need to manually fiddle with drivers (maybe including the ndiswrapper option) which I'm no good with. :(

And with this, I think I'll take my break for today.

---

### Post by gxHL on 2011-07-29
```
ar@ar-d:~$ dmesg | grep wlan0

[   10.620957] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Ethernet connection isn't possible at this time :(

go go rest... maybe the solution will come to you in your sleep xD

---

### Post by varunendra on 2011-07-30
> **gxHL said:**
> ```

go go rest... maybe the solution will come to you in your sleep xD
Hmm.. no dreams, no ideas, hence still no candy for you, but yeah I do still have hope :).

Some more research shows that rt61pci is perhaps still a troublesome driver as well as your card it is associated with. Ndiswrapper also doesn't seem a promising solution, so I think we should try it as a last option. Also, the output of iwconfig is not as normal as it seemed in the first glance, but seems more like a result rather than a hint to the problem.

So I'm still in search for a clue that I can understand. Please post outputs of:
[CODE]dmesg | grep rt
```
and
```
lsmod | grep rt
```

---

### Post by gxHL on 2011-07-30
I think my system isn't ment to use linux...

```
ar@ar-d:~$ dmesg | grep rt

[    0.000000] KERNEL supported cpus:

[    0.000000] Movable zone start PFN for each node

[    0.000000] Detected use of extended apic ids on hypertransport bus

[    0.000000] ACPI: PM-Timer IO Port: 0x508

[    0.000000] Allocating PCI resources starting at 78000000 (gap: 78000000:86c00000)

[    0.000000] Booting paravirtualized kernel on bare hardware

[    0.000000] Enabling unmasked SIMD FPU exception support... done.

[    0.000000] virtual kernel memory layout:

[    0.004217] mce: CPU supports 5 MCE banks

[    0.035766] ftrace: converting mcount calls to 0f 1f 44 00 00

[    0.195516] ACPI: (supports S0 S1 S3 S4 S5)

[    0.224971] pci 0000:00:01.0: reg 10 io port: [0x900-0x9ff]

[    0.225014] pci 0000:00:01.1: reg 10 io port: [0xe00-0xe3f]

[    0.225026] pci 0000:00:01.1: reg 20 io port: [0x600-0x63f]

[    0.225031] pci 0000:00:01.1: reg 24 io port: [0x700-0x73f]

[    0.225052] pci 0000:00:01.1: PME# supported from D3hot D3cold

[    0.225277] pci 0000:00:02.0: supports D1 D2

[    0.225280] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.225339] pci 0000:00:02.1: supports D1 D2

[    0.225341] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold

[    0.225399] pci 0000:00:04.0: supports D1 D2

[    0.225401] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.225460] pci 0000:00:04.1: supports D1 D2

[    0.225463] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold

[    0.225504] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]

[    0.225575] pci 0000:00:07.0: PME# supported from D3hot D3cold

[    0.225642] pci 0000:00:09.0: reg 10 io port: [0xc480-0xc487]

[    0.225647] pci 0000:00:09.0: reg 14 io port: [0xc400-0xc403]

[    0.225651] pci 0000:00:09.0: reg 18 io port: [0xc080-0xc087]

[    0.225656] pci 0000:00:09.0: reg 1c io port: [0xc000-0xc003]

[    0.225660] pci 0000:00:09.0: reg 20 io port: [0xbc00-0xbc0f]

[    0.225712] pci 0000:00:0a.0: reg 14 io port: [0xb880-0xb887]

[    0.225744] pci 0000:00:0a.0: supports D1 D2

[    0.225746] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.225791] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.226045] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.226334] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.226623] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.226838] pci 0000:01:07.0: reg 10 io port: [0xdc00-0xdc1f]

[    0.226873] pci 0000:01:07.0: supports D1 D2

[    0.226905] pci 0000:00:08.0: bridge io port: [0xd000-0xdfff]

[    0.226949] pci 0000:02:00.0: reg 24 io port: [0xec00-0xec7f]

[    0.226983] pci 0000:00:0b.0: bridge io port: [0xe000-0xefff]

[    0.284619] system 00:06: ioport range 0x4d0-0x4d1 has been reserved

[    0.284622] system 00:06: ioport range 0x800-0x80f has been reserved

[    0.284625] system 00:06: ioport range 0x500-0x57f has been reserved

[    0.284628] system 00:06: ioport range 0x580-0x5ff has been reserved

[    0.284631] system 00:06: ioport range 0x800-0x87f could not be reserved

[    0.284635] system 00:06: ioport range 0x880-0x8ff has been reserved

[    0.284638] system 00:06: ioport range 0xd00-0xd7f has been reserved

[    0.284641] system 00:06: ioport range 0xd80-0xdff has been reserved

[    0.284669] system 00:0b: ioport range 0x230-0x23f has been reserved

[    0.284672] system 00:0b: ioport range 0x290-0x29f has been reserved

[    0.284675] system 00:0b: ioport range 0xa00-0xa0f has been reserved

[    0.284678] system 00:0b: ioport range 0xa10-0xa1f has been reserved

[    0.382727] pcieport 0000:00:10.0: irq 24 for MSI/MSI-X

[    0.382747] pcieport 0000:00:10.0: setting latency timer to 64

[    0.383141] pcieport 0000:00:12.0: irq 25 for MSI/MSI-X

[    0.383161] pcieport 0000:00:12.0: setting latency timer to 64

[    0.383544] pcieport 0000:00:13.0: irq 26 for MSI/MSI-X

[    0.383563] pcieport 0000:00:13.0: setting latency timer to 64

[    0.394367] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled

[    0.396445] input: Macintosh mouse button emulation as /devices/virtual/input/input2

[    0.398197] ehci_hcd 0000:00:02.1: debug port 1

[    0.398205] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported

[    0.435069] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00

[    0.435259] hub 1-0:1.0: 6 ports detected

[    0.435883] ehci_hcd 0000:00:04.1: debug port 1

[    0.435892] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported

[    0.444017] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00

[    0.444118] hub 2-0:1.0: 6 ports detected

[    0.502096] hub 3-0:1.0: 6 ports detected

[    0.558096] hub 4-0:1.0: 6 ports detected

[    0.558231] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp

[    0.558386] serio: i8042 KBD port at 0x60,0x64 irq 1

[    0.558579] rtc_cmos 00:08: RTC can wake from S4

[    0.558615] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0

[    0.558668] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs

[    0.560666] Using IPI No-Shortcut mode

[    0.561464] rtc_cmos 00:08: setting system clock to 2011-07-30 12:38:33 UTC (1312029513)

[    0.771080] udev: starting version 151

[    0.911375] hub 1-1:1.0: 4 ports detected

[    0.926165] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode

[    0.927445] ata1: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76100 irq 27

[    0.927449] ata2: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76180 irq 27

[    0.927452] ata3: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76200 irq 27

[    0.927455] ata4: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76280 irq 27

[    0.927458] ata5: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76300 irq 27

[    0.927462] ata6: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76380 irq 27

[    1.410308] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    1.411681] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    1.428035] ata8: port disabled. ignoring.

[    1.667548] USB Mass Storage support registered.

[    8.984706] udev: starting version 151

[    9.300319] Linux agpgart interface v0.103

[    9.306718] parport_pc 00:05: reported by Plug and Play ACPI

[    9.306768] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]

[    9.332877]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)

[    9.388567] ppdev: user-space parallel port driver

[    9.408374] lp0: using parport0 (interrupt-driven).

[    9.442691] rt61pci 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 16 (level, low) -> IRQ 16

[    9.554317] [drm] nouveau 0000:02:00.0: TMDS table revision 2.0 not currently supported

[    9.607420] Registered led device: rt61pci-phy0::radio

[    9.607436] Registered led device: rt61pci-phy0::assoc

[    9.777816] [drm] nouveau 0000:02:00.0: 512 MiB GART (aperture)

[   10.175761] rt61pci 0000:01:06.0: firmware: requesting rt2561.bin

ar@ar-d:~$ lsmod | grep rt

rt61pci                18920  0 

crc_itu_t               1371  1 rt61pci

rt2x00pci               5995  1 rt61pci

rt2x00lib              27573  2 rt61pci,rt2x00pci

led_class               2864  1 rt2x00lib

mac80211              205402  2 rt2x00pci,rt2x00lib

parport_pc             25962  1 

agpgart                31724  2 ttm,drm

cfg80211              126144  2 rt2x00lib,mac80211

eeprom_93cx6            1333  1 rt61pci

parport                32635  3 ppdev,parport_pc,lp

```

---

### Post by varunendra on 2011-07-30
Nothing rings a bell so far. I doubt the quality of signal. So what is the strength of the signal when it is connected in win7?

Try this as a wild shot (actually I don't know at this point what am I doing):
```
sudo ifconfig wlan0 down
```
then wait about 10 sec., then-
```
sudo ifconfig wlan0 up
```

If this doesn't help picking up a network, then-
```
sudo /etc/init.d/networking restart
```

There are a few more things we can try, but I need some time to recollect them. Hopefully I'll get some time this Sunday.

By the way, what was the problem with the ndiswrapper tutorial you mentioned in your first post. It seemed quite easy to me. We may try that if I don't come up with something meaningful tomorrow.

---

### Post by gxHL on 2011-07-30
> **varunendra said:**
> Nothing rings a bell so far. I doubt the quality of signal. So what is the strength of the signal when it is connected in win7?
The smallest signal quality is 36Mbps but at 70% its 48-54mbps.


> **varunendra said:**
> Try this as a wild shot (actually I don't know at this point what am I doing):
```
sudo ifconfig wlan0 down
```then wait about 10 sec., then-
```
sudo ifconfig wlan0 up
```If this doesn't help picking up a network, then-
```
sudo /etc/init.d/networking restart
``` 

Tried that one myself but i will give it a try again. ill edit the results here.

> **varunendra said:**
> By the way, what was the problem with the ndiswrapper tutorial you mentioned in your first post. It seemed quite easy to me. We may try that if I don't come up with something meaningful tomorrow.

Well actually i didn't understand it...although in win7 i got more experience my knowledge of linux and linux commands are very very VERY small ...

---

### Post by gxHL on 2011-07-30
Moved my computer a bit....(A LOOOT...) and now it works... fair connection but i guess i can live with that.
Can't thank you enough for the support and i'm so sorry for the inconvenience... :(

---

### Post by varunendra on 2011-07-31
> **gxHL said:**
> Moved my computer a bit....(A LOOOT...) and now it works... fair connection but i guess i can live with that.
Can't thank you enough for the support and i'm so sorry for the inconvenience... :(
It's alright with me, no inconvenience at all! It's experience that counts. Besides, if you had to move your computer 'a lot' just to get a 'fair' quality connection, whereas win7 was getting upto 70% signal strength at the earlier location, then it can't be considered as satisfactory. With this kind of poor performance by the driver, I doubt the stability of the connection. But having found no perfect solution for this card so far, all I can suggest now is to keep looking for a better replacement for this driver/version.

In case you experience further problems with it, you should consider trying drivers from ralink's own site: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) or else trying the ndiswrapper method (using win98 drivers). Also, if you now have internet connection on it, try updating the system and see if there's any better driver suggested under 'System > Administration > Hardware Drivers'.

---

### Post by gxHL on 2011-07-31
The strength of the signal is about 60 %  but its pretty much the same as in win... i don't really need more than that.
I run the Hardware Drivers but the only thing that came up was Nvidia Graphic Accelerator. which i installed... :P 
Anyhow thank you again for everything go get some rest now ^^

---

