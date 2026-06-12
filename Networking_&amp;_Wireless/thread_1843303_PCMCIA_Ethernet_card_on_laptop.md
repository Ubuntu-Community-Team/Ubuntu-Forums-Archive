---
title: "PCMCIA Ethernet card on laptop"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by pwbecker on 2011-09-13
I am trying to set up an old Toshiba laptop (Satellite 4080XCDT) on Ubuntu Desktop with kernel 2.6.35-22

When I insert the PCMCIA card, it appears via lspci, but doesn't seem to bring up the interface (no green light on hub). The syslog contains the following.  Any help much appreciated!

Sep 13 12:44:54 Toshiba kernel: [ 2175.113003] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
Sep 13 12:44:54 Toshiba kernel: [ 2175.113118] pci 0000:01:00.0: reg 10: [io  0x0000-0x007f]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113149] pci 0000:01:00.0: reg 14: [mem 0x00000000-0x0000007f]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113178] pci 0000:01:00.0: reg 18: [mem 0x00000000-0x0000007f]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113234] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113304] pci 0000:01:00.0: supports D1 D2
Sep 13 12:44:54 Toshiba kernel: [ 2175.113322] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
Sep 13 12:44:54 Toshiba kernel: [ 2175.113343] pci 0000:01:00.0: PME# disabled
Sep 13 12:44:54 Toshiba kernel: [ 2175.113395] pci 0000:01:00.0: BAR 6: assigned [mem 0x14000000-0x1401ffff pref]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113419] pci 0000:01:00.0: BAR 0: assigned [io  0x1000-0x107f]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113448] pci 0000:01:00.0: BAR 0: set to [io  0x1000-0x107f] (PCI address [0x1000-0x107f]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113473] pci 0000:01:00.0: BAR 1: assigned [mem 0x18000000-0x1800007f]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113502] pci 0000:01:00.0: BAR 1: set to [mem 0x18000000-0x1800007f] (PCI address [0x18000000-0x1800007f]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113528] pci 0000:01:00.0: BAR 2: assigned [mem 0x18000080-0x180000ff]
Sep 13 12:44:54 Toshiba kernel: [ 2175.113557] pci 0000:01:00.0: BAR 2: set to [mem 0x18000080-0x180000ff] (PCI address [0x18000080-0x180000ff]
Sep 13 12:44:54 Toshiba kernel: [ 2175.116723] 3c59x 0000:01:00.0: enabling device (0000 -> 0003)
Sep 13 12:44:54 Toshiba kernel: [ 2175.116820] 0000:01:00.0: 3Com PCI 3CCFE575BT Cyclone CardBus at cc83c000.
Sep 13 12:44:54 Toshiba kernel: [ 2175.116855] 3c59x 0000:01:00.0: setting latency timer to 64
Sep 13 12:44:54 Toshiba NetworkManager[532]: <info> (eth0): carrier is OFF
Sep 13 12:44:54 Toshiba NetworkManager[532]: <info> (eth0): new Ethernet device (driver: '3c59x' ifindex: 5)
Sep 13 12:44:54 Toshiba NetworkManager[532]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/2
Sep 13 12:44:54 Toshiba NetworkManager[532]: <info> (eth0): now managed
Sep 13 12:44:54 Toshiba NetworkManager[532]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Sep 13 12:44:54 Toshiba NetworkManager[532]: <info> (eth0): bringing up device.
Sep 13 12:44:54 Toshiba kernel: [ 2175.485032] eth0:  setting half-duplex.
Sep 13 12:44:54 Toshiba NetworkManager[532]: <info> (eth0): preparing device.
Sep 13 12:44:54 Toshiba NetworkManager[532]: <info> (eth0): deactivating device (reason: 2).
Sep 13 12:44:54 Toshiba kernel: [ 2175.497473] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 13 12:44:54 Toshiba NetworkManager[532]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/net/eth0
Sep 13 12:44:54 Toshiba NetworkManager[532]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/net/eth0, iface: eth0)
Sep 13 12:44:54 Toshiba NetworkManager[532]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.

---

### Post by praseodym on 2011-09-13
Hi,

please show:

```
lspci -nnk
pccardctl info
lsmod
ifconfig -a
```

---

### Post by pwbecker on 2011-09-13
Thanks for the quick response.
```
# lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) [8086:7192] (rev 03)
    Subsystem: Toshiba America Info Systems Satellite 4010 [1179:0001]
00:02.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC97 [1179:060f] (rev 05)
    Subsystem: Toshiba America Info Systems Satellite 4010 [1179:0001]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
00:02.1 CardBus bridge [0607]: Toshiba America Info Systems ToPIC97 [1179:060f] (rev 05)
    Subsystem: Toshiba America Info Systems Satellite 4010 [1179:0001]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
00:04.0 VGA compatible controller [0300]: Trident Microsystems Cyber 9525 [1023:9525] (rev 49)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel modules: tridentfb
00:05.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:05.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
    Kernel driver in use: ata_piix
00:05.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
    Kernel driver in use: uhci_hcd
00:05.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 02)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:0a.0 Communication controller [0780]: Toshiba America Info Systems FIR Port Type-O [1179:0701] (rev 23)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel driver in use: donauboe
    Kernel modules: donauboe
00:0c.0 Multimedia audio controller [0401]: ESS Technology ES1978 Maestro 2E [125d:1978] (rev 10)
    Subsystem: Toshiba America Info Systems ES1978 Maestro-2E Audiodrive [1179:0001]
    Kernel driver in use: ES1968 (ESS Maestro)
    Kernel modules: snd-es1968, radio-maestro
01:00.0 Ethernet controller [0200]: 3Com Corporation 3cCFE575BT Megahertz 10/100 LAN CardBus [Cyclone] [10b7:5157] (rev 01)
    Subsystem: 3Com Corporation 3C575 Megahertz 10/100 LAN Cardbus PC Card [10b7:5b57]
    Kernel driver in use: 3c59x
    Kernel modules: 3c59x
# pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
# pccardctl ls
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:02.0)
  CardBus card -- see "lspci" for more information
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:02.1)
# lsmod

Module                  Size  Used by
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  1 vfat
usb_storage            40172  0 
binfmt_misc             6599  1 
parport_pc             26058  1 
ppdev                   5556  0 
snd_es1968             22249  2 
gameport                9327  1 snd_es1968
snd_ac97_codec         99227  1 snd_es1968
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_es1968,snd_ac97_codec
snd_page_alloc          7120  2 snd_es1968,snd_pcm
snd_mpu401_uart         5661  1 snd_es1968
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
3c59x                  32011  0 
snd                    49006  12 snd_es1968,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
donauboe               12408  0 
mii                     4425  1 3c59x
soundcore                880  1 snd
pcmcia                 35973  0 
radio_maestro           4833  0 
irda                  178938  1 donauboe
v4l2_common            17329  1 radio_maestro
yenta_socket           21518  0 
psmouse                59033  0 
pcmcia_rsrc            10566  1 yenta_socket
videodev               43098  2 radio_maestro,v4l2_common
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4022  0 
lp                      7342  0 
i2c_piix4               8635  0 
v4l1_compat            13359  1 videodev
crc_ccitt               1351  2 donauboe,irda
parport                31492  3 parport_pc,ppdev,lp
# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:04:5e:0f:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x4000 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9600 (9.6 KB)  TX bytes:9600 (9.6 KB)


```

---

### Post by praseodym on 2011-09-13
Did you check the cable? Checkbox all user rights in "Users&Groups", login again, remove your profile in the network-manager applet and reboot the system.

Is that a router/modem combination or a single modem?

---

### Post by pwbecker on 2011-09-13
I switched the ethernet cable with a working system, yes.  However, the short cable which connects the PCMCIA card to the ethernet cable I cannot test, as I only have the one. 

BUT...! :) I just had a close look at this short cable and it can go into the PCMCIA card either way around.  I tried it the other way up, and it all works now!

Thanks for your suggestions!

---

