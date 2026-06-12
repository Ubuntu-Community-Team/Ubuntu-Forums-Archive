---
title: "No network, no internet on Ubuntu 12.04"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by firekage on 2012-06-22
Hello.

I would ask again for your help. I was curious about Ubuntu 12.04 so i installed it. After installation i entered gui, desktop, wanted to install some software but...i couldn't because there is no internet, no network.

In network menager i see 2 network cards:

-Realtek
-Sundance

All of them works fine under Ubuntu 11.10 but on 12.04 wired connection after log in is "lost" - i see this message near icon that symbolizes network in Ubuntu.

Can You help me? I tried to do something that is written on internet/web like adding static ip addres, so i

-edited /etc/Network/Network.conf and changed to true menaging
-edited /etc/network/interfaces and added 

auto eth0
iface eth0 inet static
address      xxx.xxx.xxx 
netmask    xxx.xxx.xxx
network xxx.xxx.xxx
broadcast xxx.xxx.xxx
gateway   xxx.xxx.xxx

But after reboot i didn't have network again. In network settings choosed from dash when typeing i saw that there is "no cable plugged" when in fact it is not true. In network connections on panel/ubuntu bar (near clock) i see 2 lan card (realtek and sundance listed and greyed out) and even if i add something here there is no internet, no connection.

I did some outputs and here are them:

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 90:e6:ba:c7:52:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 48:5b:39:bf:0b:55  
          inet6 addr: fe80::4a5b:39ff:febf:b55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4133 (4.1 KB)
          Interrupt:21 Base address:0xe880 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33648 (33.6 KB)  TX bytes:33648 (33.6 KB)

```

---

### Post by firekage on 2012-06-22
lsmod:

```

Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
snd_hda_codec_via      46138  1 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ati_agp                13242  0 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
k10temp                12990  0 
snd_ctxfi              86200  2 
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_timer              28931  2 snd_seq,snd_pcm
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_seq_device,snd_ctxfi,snd_pcm,snd_timer
sp5100_tco             13495  0 
soundcore              14635  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_piix4              13093  0 
parport_pc             32114  1 
asus_atk0110           17742  0 
mac_hid                13077  0 
nouveau               712294  3 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  2 cx88xx,nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  56321  0 
sata_sil24             17794  1 
pata_atiixp            12999  1 

```

---

### Post by firekage on 2012-06-22
lshw:

```

deusex
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 4027MiB
     *-cpu
          product: AMD Phenom(tm) II X4 955 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: cpu@0
          version: 15.4.3
          size: 3200MHz
          capacity: 3200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:b000(size=4096) memory:f4000000-f7dfffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: GT200 [GeForce GTX 260]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:18 memory:f6000000-f6ffffff memory:d0000000-dfffffff memory:f4000000-f5ffffff ioport:bc00(size=128) memory:f7d80000-f7dfffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port D)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:c000(size=4096) memory:f7e00000-f7efffff
           *-storage
                description: RAID bus controller
                product: Silicon Image, Inc.
                vendor: Silicon Image, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list rom
                configuration: driver=sata_sil24 latency=0
                resources: irq:19 memory:f7effc00-f7effc7f memory:f7ef8000-f7efbfff ioport:cc00(size=128) memory:f7e00000-f7e7ffff
        *-pci:2
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port F)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:f7f00000-f7ffffff ioport:f2f00000(size=1048576)
          ** *-network**
                description: Ethernet interface
                product: **RTL8111/8168B PCI Express Gigabit Ethernet controller**
                vendor:** Realtek Semiconductor Co**., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: 90:e6:ba:c7:52:c1
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:d800(size=256) memory:f2fff000-f2ffffff memory:f2ff8000-f2ffbfff memory:f7ff0000-f7ffffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=8) ioport:7000(size=4) ioport:6000(size=16) memory:f3fffc00-f3ffffff
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f3ffe000-f3ffefff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f3ffd000-f3ffdfff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f3fff800-f3fff8ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f3ffc000-f3ffcfff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f3ffb000-f3ffbfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f3fff400-f3fff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f3ff4000-f3ff7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:e000(size=4096) memory:f8000000-febfffff
           *-multimedia:0
                description: Multimedia audio controller
                product: SB X-Fi
                vendor: Creative Labs
                physical id: 5
                bus info: pci@0000:04:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_ctxfi latency=64 maxlatency=5 mingnt=4
                resources: irq:20 ioport:ec00(size=32) memory:fea00000-febfffff memory:f8000000-fbffffff
         **  *-network**
                description: Ethernet interface
                product**: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY**
                vendor: **Sundance Technology Inc / IC Plus Corp**
                physical id: 6
                bus info: pci@0000:04:06.0
                logical name: eth1
                version: 31
                serial: 48:5b:39:bf:0b:55
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=full latency=64 maxlatency=10 mingnt=10 multicast=yes port=MII speed=100Mbit/s
                resources: irq:21 ioport:e880(size=128) memory:fe9ffc00-fe9ffdff memory:fe9e0000-fe9effff
           *-multimedia:1
                description: Multimedia video controller
                product: CX23880/1/2/3 PCI Video and Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: 7
                bus info: pci@0000:04:07.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20
                resources: irq:22 memory:fd000000-fdffffff
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f3ffa000-f3ffafff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

```

If You need something more i will post it.

---

### Post by firekage on 2012-06-23
Anybody? Please help ;)

---

### Post by firekage on 2012-06-23
I see that either only i have it, or more people and there is no answer and fix for it?

---

### Post by graphius on 2012-06-24
this may be the same problem many people, including me, are having, you need to edit the file /etc/resolv.conf as root.
In other words:
```
sudo nano /etc/resolve.conf
```
add the line:
> nameserver 8.8.8.8
However this will reset itself after a reboot. I am not sure how to make it permanent.

---

### Post by firekage on 2012-06-24
Thanks. So, in other words, it is some kind of bug and there is no fix for it? Can't this be done permamently?

---

### Post by firekage on 2012-06-24
> **graphius said:**
> this may be the same problem many people, including me, are having, you need to edit the file /etc/resolv.conf as root.
In other words:
```
sudo nano /etc/resolve.conf
```add the line:

However this will reset itself after a reboot. I am not sure how to make it permanent.

It doesen't work for me.



I checked two things:

-run from live instllation disk: also couldn't connect to internet, as soon as i booted i see "network disable"
-I CAN'T EVEN LOG TO MY ROUTER, i add ip addres in addres bar of firefox  and i see that i can't connect because there is no connection!

I just don't know what to do. I tried with

 	Code:
 	sudo dhcpcd ethX 
and i had this:

(sudo: dhcpcd: didn't find command - translated to english [IMG]http://static.linuxquestions.org/questions/images/smilies/wink.gif[/IMG] )

I attached files contains:

-sudo dhcpcd ethX
-my two wired connections in network menager (as you can see there are 3  connections right now cause it is from 11.10 and works, on 12.04 are  only Wired Connection 1 and Wired Connection 2 but doesen't work at all)

But despite it i have this info:

[http://img220.imageshack.us/img220/6...sconnected.png]("http://img220.imageshack.us/img220/6914/networkdisconnected.png")

---

### Post by firekage on 2012-06-24
Guys, i really would like to try and use new Ubuntu but without network it is not possible. Can somebody help me? I even started topic here:

[http://www.linuxquestions.org/questions/ubuntu-63/i-cant-connect-to-internet-there-is-no-internet-network-on-ubuntu-12-04-a-4175413008/](http://www.linuxquestions.org/questions/ubuntu-63/i-cant-connect-to-internet-there-is-no-internet-network-on-ubuntu-12-04-a-4175413008/)

with some infos but still no succedeed

---

### Post by graphius on 2012-06-24
Just to go through the obvious things.....
I am assuming this is a desktop. If so, you may have a bad network card. (yes a card can go between installs...)
Since you have two cards, try removing one and see if that changes things. or try disabling (commenting out) the cards, one at a time, of course making sure you move the network cable.
As a last resort, get a new network card (stick with a normal name brand) and install it
Or, as a very last resort, try reinstalling your older ubuntu to see if the card works.

Sorry, past that, I am not sure....

---

### Post by firekage on 2012-06-24
> **graphius said:**
> Just to go through the obvious things.....
I am assuming this is a desktop. If so, you may have a bad network card. (yes a card can go between installs...)

No, i can't. On windows both of them work. On 11.10 also they work fine.

> Since you have two cards, try removing one and see if that changes things. or try disabling (commenting out) the cards, one at a time, of course making sure you move the network cable.

Did earlier but this is not thing to consider because of no problem on Windows and 11.10 mentioned above..
> 
As a last resort, get a new network card (stick with a normal name brand) and install it
Or, as a very last resort, try reinstalling your older ubuntu to see if the card works.

Sorry, past that, I am not sure....

They are name brand. Both them are Asus, one on Realtek Semiconductor, other on IC Plus Corporation Sundance Technology.

---

### Post by firekage on 2012-06-24
Either kernel fault or meybe driver? I don't knoh how to check driver version for it.

---

### Post by firekage on 2012-06-25
> **firekage said:**
> Either kernel fault or meybe driver? I don't knoh how to check driver version for it.

I'm close.

I see "a light in the tunnel". I checked with other wired lan card - Realtek. Network works right after log in into Ubuntu.

I think that there is something wrong with kernel or driver for one Asus card - the one on ISC chipset with Sundance driver. I would like to know how to delete this driver and install new. 

**On Realtek after plugging cable i see: network connections auto; and network works. On Sundance lan card (also Asus) i see: device not ready. That is why it can't take ip.** 

If You know how to solve this than i'm listening :d It is not related to a network settings but hardware problems with Asus on IC PLUS chip

**This one doesen't work on 12.04:**

```
description: Ethernet interface
       product: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY
```

**This one works on 12.04 when i plug cable:**

```
description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
```

---

### Post by ranger1021994 on 2012-06-25
I dont know if this is the correct solution but i change connection setting to manual instead of Automatic[dhcp] and fill relevent details. 
:)

---

### Post by firekage on 2012-06-25
> **ranger1021994 said:**
> I dont know if this is the correct solution but i change connection setting to manual instead of Automatic[dhcp] and fill relevent details. 
:)
Where did you change it?

---

### Post by firekage on 2012-06-26
SolvedI think that there was something wrong with bringing up eth1.

This is what i entered to a /etc/network/interfaces

     ```

firekage@deusex:~$ cat /etc/network/interfaces 
#auto eth0 #iface eth0 inet dhcp 
 #auto eth1 #iface eth1 inet dhcp  

# The loopback network interface 
auto lo 
iface lo inet loopback  

# The primary network interface 
auto eth1
iface eth1 inet dhcp 
 
```
And with the secon
d one commands it works with eth1 (cable is  pluged here). If uncomment eth1 here than i don't have connection. Also  it there is only "the loopbasck network interface" without the "primary  network interface" section than there is no network either. 
This is what i added to a /etc/NetworkManager/Network.conf
       ```

  firekage@deusex:~$ cat /etc/NetworkManager/NetworkManager.conf   

[main] plugins=ifupdown,keyfile 
#dns=dnsmasq  

no-auto-default (my mac adres) 

 [ifupdown] 

managed=true   

firekage@deusex:~$ 

```

and my wired connections is managed in network-manager applet in Ubuntu.    

Internet/connection works. **_The problem is that i don't know why i  had to change these files when on 11.10 it was right after boot and  automatically. I had to add manually it on 12.04._**

---

### Post by dsa42 on 2012-06-29
The exact same thing happened to me.  On June 29, 2012, I upgraded to Ubuntu 12.04, and my internet is completely not working.  I can not even get to my router (using the IP 192.168.2.1).  I had to go to another computer to post this, so I can't post a complete system details list (everything has to be typed in manually - I suppose I could put things on a flash drive).

I'm using LXDE

Doing a ifconfig -a, I don't see an IP address under eth0

---

### Post by firekage on 2012-06-30
Try to put these two things above in their config files - maybe it will help you.


BTW - funny thing is that wireless network is connected right after log in (i tried it with few computers on Ubuntu live usb version), but wired is not recognized for all machines..

---

### Post by dsa42 on 2012-06-30
> **firekage said:**
> Try to put these two things above in their config files - maybe it will help you.

Which two things?

---

### Post by firekage on 2012-06-30
> **dsa42 said:**
> Which two things?

Post number 16 - i explained what helped me with my wired connections problem.

---

### Post by dsa42 on 2012-06-30
> **firekage said:**
> Post number 16 - i explained what helped me with my wired connections problem.

and then

> **firekage said:**
> I dont know if this is the correct solution

Thank you for your suggestion, firekage, but I don't feel comfortable making any random change without knowing the reason.  My network connectivity should not have stopped working just by doing an upgrade.  Can anyone please help me diagnose what the problem is?

---

### Post by firekage on 2012-07-01
You can try it. You can always do a backup of these two config biles by

sudo mv -v <file1> <file1.old> or <file1.backup> and see what will happen ;)

for an example of /etc/network/interfaces

sudo mv -v interfaces interfaces.backup 

or

sudo mv -v interfaces interfaces.old

and You have backuped it and You can now try to change it.

---

### Post by dsa42 on 2012-07-01
> **firekage said:**
> You can try it. 

Firekage, I really appreciate your help.  This just is not the right approach for me.  First, your changes don't make sense for me.  I don't even _have_ an eth1. 

However, I did try to see what I could take from your solution and apply it to my system.  It didn't work.

So, again, I am asking the community to help me diagnose my problem.  I'm really upset that a simple upgrade of Ubuntu would destroy my network connectivity.

---

