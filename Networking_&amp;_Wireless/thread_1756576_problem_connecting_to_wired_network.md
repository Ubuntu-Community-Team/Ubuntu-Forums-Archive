---
title: "problem connecting to wired network"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by Dr.Joker on 2011-05-12
Hi guys,

I have a very strange and annoying problem. When I try to connect to the  Internet with a LAN cable, it doesn't work. I plug the cable in and  nothing happens. But here comes the twist: it was working perfectly  until yesterday! Without making any changes, yesterday I came to work,  plugged in the cable into my laptop, and nothing happens. I first  suspected there was something wrong with the cable, but I tried a  different cable from a different outlet and nothing happens, and when I  boot in to Windows it still connects automatically without any problems.  To make things even stranger, I reset the computer a few times, and  eventually it connected, but the next time I booted my system again no  wired Internet.  I can still connect to wireless, but this kind of thing  really bothers me, because I have no clue why this just suddenly  stopped working. When I run

```


sudo dhclient -v eth0


```it tries DHCPDISCOVER and finally the output it gives is


```

No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```But I don't understand why, and if I log in to windows I get an  IP address without any problems, and everything is smooth. Any help in  resolving this issue will be greatly appreciated.

---

### Post by josephmills on 2011-05-12
Hi there could we please get a little more info from you? please open your terminal and do a ```
sudo lshw -C network
``` and a ```
lspci -nn
``` thanks

---

### Post by Dr.Joker on 2011-05-13
Thanks for your reply. When I run

```

sudo lshw -C network

```

I get

```

  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 00:23:18:9d:ce:95
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:d4700000-d471ffff memory:d472a000-d472afff ioport:3020(size=32)


```

and when I run

```

lspci -nn

```

I get

```


00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b07] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
01:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 01)
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)


```

Also if I boot in recovery mode, and choose failsafeX, it connects to the network automatically right away.

---

### Post by Irony on 2011-05-13
See here; [http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9)

or here if you have a homehub2;

[http://ubuntuforums.org/showthread.php?t=1753698](http://ubuntuforums.org/showthread.php?t=1753698)

---

### Post by Dr.Joker on 2011-05-13
Hi irony,

thanks for your reply, but that doesn't solve my problem. It solved it once, I don't know if accidentally or not, and after that it went back to the same. I tried setting a static IP address but that didn't help either. I don't know what to do. When I log into recovery mode it works every time.

---

### Post by Irony on 2011-05-14
> **Dr.Joker said:**
> I tried setting a static IP address but that didn't help either.
Do you mean you set it as static but it went back to automatic, because that would mean you didn't save the settings - your readings indicate that you are on automatic.

What sort of router do you have?

---

