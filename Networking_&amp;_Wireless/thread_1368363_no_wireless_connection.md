---
title: "no wireless connection"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by dutchg on 2009-12-30
Hi:

I'm a complete and utter Linux beginner. I run a Thinkpad T42 and a Linksys wireless router. My first foray into Linux (two days ago) was with Puppy Linux. The wireless connection with Puppy was painless and simple.  I thought, OK, if I'm going into Linux, I'm going to go with Ubuntu. So I put Ubuntu 9.10 on my machine, but nothing I've tried will establish a working wireless connection. I would imagine the fix would be simple, since I'm using two very standard pieces of gear (the ibm and the linksys) and since the connections via Windows and Puppy were drop-dead simple. 

I was hoping Ubuntu was going to "just work," because I'm sick of Windows. As for diagnostics, I don't even know enough to do the data dump I've seen others doing here on these threads. This seems to be a common issue (wish I'd known that before I installed the software). Does anyone know a common and simple fix? I don't have the skills or the interest to go poking into a lot of arcana. 

Thanks for any ideas

Dutch.

---

### Post by dutchg on 2009-12-30
bump

---

### Post by shredder12 on 2009-12-30
Open System->administration->hardware drivers and see if there is a wireless driver mentioned, if yes then check if its activated.

If there is no wireless driver mentioned above then please post the output of
```
lspci
```

---

### Post by dutchg on 2009-12-31
Thanks for giving me a hand. I checked hardware drivers, and it found nothing. I ran lspci and here are the results:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

---

### Post by yumgnomeandthensome on 2009-12-31
your device (2200bg) is listed as works in the following link at the top of the networking forum:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

iwconfig from cmd line is helpful.
My wireless information is located at the top right of my screen, can you see if it is even trying to connect? left clicking on the icon will show you want ssid's it sees. If its hidden there is a 'connect to hidden' option as well.

You might want to 'dumb' down your connection and make your router accept open connections, once you prove you can connect then you can move to wep or wpa.

---

### Post by dutchg on 2009-12-31
Well, when I turn WEP off on the router, I AM able to connect! That's encouraging. 

Here's the iwconfig, with WEP turned off:

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"pilcrow"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:04:5A:CE:40:51   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-51 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dutchg on 2009-12-31
..and here's the output with WEP turned on, and the correct WEP key put in (but still no connection).


lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      unassociated  ESSID:"pilcrow"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:04:5A:CE:40:51   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dutchg on 2009-12-31
More info:


lsusb
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:11:25:85:d0:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:0e:35:a5:35:72  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fea5:3572/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1273 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2130193 (2.1 MB)  TX bytes:143754 (143.7 KB)
          Interrupt:11 Base address:0x8000 Memory:c0210000-c0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```lsmod
```

Module                  Size  Used by
binfmt_misc             8356  1 
pcmcia                 36808  0 
snd_intel8x0           30168  2 
iptable_filter          3100  0 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           24200  2 
ip_tables              11692  1 iptable_filter
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ipw2200               140292  0 
x_tables               16544  1 ip_tables
rsrc_nonstatic         11644  1 yenta_socket
soundcore               7264  1 snd
libipw                 43148  1 ipw2200
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
joydev                 10272  0 
lib80211                6432  2 ipw2200,libipw
thinkpad_acpi          67108  0 
shpchp                 32272  0 
led_class               4096  1 thinkpad_acpi
nsc_ircc               20976  0 
nvram                   7528  1 thinkpad_acpi
ppdev                   6688  0 
irda                  189564  1 nsc_ircc
parport_pc             31940  1 
psmouse                56180  0 
serio_raw               5280  0 
crc_ccitt               1852  1 irda
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
e1000                 119264  0 
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
floppy                 54916  0 
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp
```
```

PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:85:d0:68
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8000(size=64) memory:c0240000-c024ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:a5:35:72
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.103 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11b
       resources: irq:11 memory:c0210000-c0210fff

```


Any help appreciated. I can connect if I turn of WEP, but trying it with WEP key required is not working. 

thanks

---

### Post by leebaldwin on 2009-12-31
I am running Xubuntu and I looked at my settings. Under the wireless settings, I have put in my key, set the key type to shared key and saved  the settings. I am just trying to provide a little help here.

---

### Post by dutchg on 2009-12-31
> **leebaldwin said:**
> I am running Xubuntu and I looked at my settings. Under the wireless settings, I have put in my key, set the key type to shared key and saved  the settings. I am just trying to provide a little help here.

Thanks, Lee. I gave that a try, but it didn't help.

---

### Post by yumgnomeandthensome on 2009-12-31
can you  give more detail as to what happens? do you see your wireless icon in the top right 'spinning' as it tries to connect?
1/ compare the output of (from cmd line) below when it works and when does't.
cat /var/log/dmesg
2/ also if you have another pc, connect to your wap device and see what it says.
3/ unhide ur ssid (if using hidden)
4/ try connecting without any configuration - it should appear in detected wireless networks

I've just gone to using 'wicd' as i've got the odd issue where i cna't connect 10% of the time. Will let you know how that goes, as its connected in my first two attempts.

---

### Post by dutchg on 2010-01-01
> **yumgnomeandthensome said:**
> can you  give more detail as to what happens? do you see your wireless icon in the top right 'spinning' as it tries to connect?
1/ compare the output of (from cmd line) below when it works and when does't.
cat /var/log/dmesg
2/ also if you have another pc, connect to your wap device and see what it says.
3/ unhide ur ssid (if using hidden)
4/ try connecting without any configuration - it should appear in detected wireless networks

I've just gone to using 'wicd' as i've got the odd issue where i cna't connect 10% of the time. Will let you know how that goes, as its connected in my first two attempts.


I've got the outputs you asked for in 1 below.  As for the other questions:

2) I don't have another wireless computer to try Ubuntu on.

3) If by "unhide ssid" you mean that I should try it without a WEP key, I already did that, and it works just fine. But when I make WEP required, it doesn't work.

4) I don't understand what you're suggesting here. 

1) The outputs from** cat /var/log/dmesg**

while WEP is on, and I'm trying to connect:

```
[    0.004427]  [<c011d7e3>] native_apic_write_dummy+0x33/0x40
[    0.004436]  [<c011278c>] intel_init_thermal+0xac/0x1a0
[    0.004441]  [<c0111dbb>] mce_intel_feature_init+0xb/0x60
[    0.004446]  [<c010fcf0>] mce_cpu_features+0x10/0x40
[    0.004455]  [<c056ac3c>] mcheck_init+0x14a/0x188
[    0.004459]  [<c0569078>] ? init_hypervisor+0xb/0x2c
[    0.004464]  [<c0569030>] identify_cpu+0x20e/0x21d
[    0.004474]  [<c0795732>] identify_boot_cpu+0xd/0x23
[    0.004479]  [<c07958c8>] check_bugs+0xb/0xe9
[    0.004487]  [<c078e8c3>] start_kernel+0x2dc/0x2ec
[    0.004492]  [<c078e406>] ? unknown_bootoption+0x0/0x1ab
[    0.004497]  [<c078e07c>] i386_start_kernel+0x7c/0x83
[    0.004510] ---[ end trace a7919e7f17c0a725 ]---
[    0.004513] CPU0: Thermal monitoring enabled (TM1)
[    0.004529] Performance Counters: 
[    0.004532] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.004535] no hardware sampling interrupt available.
[    0.004537] p6 PMU driver.
[    0.004544] ... version:                 0
[    0.004547] ... bit width:               32
[    0.004549] ... generic counters:        2
[    0.004551] ... value mask:              00000000ffffffff
[    0.004554] ... max period:              000000007fffffff
[    0.004556] ... fixed-purpose counters:  0
[    0.004559] ... counter mask:            0000000000000003
[    0.004565] Checking 'hlt' instruction... OK.
[    0.020950] SMP alternatives: switching to UP code
[    0.028015] Freeing SMP alternatives: 19k freed
[    0.028027] ACPI: Core revision 20090521
[    0.047591] ACPI: setting ELCR to 0200 (from 0800)
[    0.048078] weird, boot CPU (#0) not listed by the BIOS.
[    0.048081] SMP motherboard not detected.
[    0.048085] Local APIC not detected. Using dummy APIC emulation.
[    0.048087] SMP disabled
[    0.048252] Brought up 1 CPUs
[    0.048255] Total of 1 processors activated (3197.51 BogoMIPS).
[    0.048269] CPU0 attaching NULL sched-domain.
[    0.048516] Booting paravirtualized kernel on bare hardware
[    0.048764] regulator: core version 0.5
[    0.048787] Time: 19:33:52  Date: 01/01/10
[    0.048850] NET: Registered protocol family 16
[    0.049007] EISA bus registered
[    0.049024] ACPI: bus type pci registered
[    0.049290] PCI: PCI BIOS revision 2.10 entry at 0xfd8d6, last bus=8
[    0.049293] PCI: Using configuration type 1 for base access
[    0.052356] bio: create slab <bio-0> at 0
[    0.053598] ACPI: EC: EC description table is found, configuring boot EC
[    0.062068] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.073394] ACPI: Interpreter enabled
[    0.073400] ACPI: (supports S0 S3 S4 S5)
[    0.073428] ACPI: Using PIC for interrupt routing
[    0.092522] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.092526] ACPI: EC: driver started in interrupt mode
[    0.092572] ACPI: Power Resource [PUBS] (on)
[    0.093081] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.093108] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.093155] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.096086] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.096140] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.096193] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.096255] pci 0000:00:1d.7: reg 10 32bit mmio: [0xc0000000-0xc00003ff]
[    0.096313] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.096318] pci 0000:00:1d.7: PME# disabled
[    0.096409] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.096414] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.096439] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.096447] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.096454] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.096462] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.096470] pci 0000:00:1f.1: reg 20 io port: [0x1860-0x186f]
[    0.096478] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.096530] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.096574] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.096582] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.096589] pci 0000:00:1f.5: reg 18 32bit mmio: [0xc0000c00-0xc0000dff]
[    0.096597] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xc0000800-0xc00008ff]
[    0.096626] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.096631] pci 0000:00:1f.5: PME# disabled
[    0.096662] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.096669] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.096707] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.096712] pci 0000:00:1f.6: PME# disabled
[    0.096749] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.096756] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.096763] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.096779] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.096799] pci 0000:01:00.0: supports D1 D2
[    0.096835] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.096839] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.096843] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.096880] pci 0000:02:00.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
[    0.096900] pci 0000:02:00.0: supports D1 D2
[    0.096902] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.096907] pci 0000:02:00.0: PME# disabled
[    0.096943] pci 0000:02:00.1: reg 10 32bit mmio: [0xb1000000-0xb1000fff]
[    0.096963] pci 0000:02:00.1: supports D1 D2
[    0.096966] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.096971] pci 0000:02:00.1: PME# disabled
[    0.097011] pci 0000:02:01.0: reg 10 32bit mmio: [0xc0220000-0xc023ffff]
[    0.097019] pci 0000:02:01.0: reg 14 32bit mmio: [0xc0200000-0xc020ffff]
[    0.097027] pci 0000:02:01.0: reg 18 io port: [0x8000-0x803f]
[    0.097047] pci 0000:02:01.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.097067] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.097072] pci 0000:02:01.0: PME# disabled
[    0.097105] pci 0000:02:02.0: reg 10 32bit mmio: [0xc0210000-0xc0210fff]
[    0.097150] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.097155] pci 0000:02:02.0: PME# disabled
[    0.097195] pci 0000:00:1e.0: transparent bridge
[    0.097201] pci 0000:00:1e.0: bridge io port: [0x4000-0x8fff]
[    0.097206] pci 0000:00:1e.0: bridge 32bit mmio: [0xc0200000-0xcfffffff]
[    0.097212] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.097252] pci_bus 0000:00: on NUMA node 0
[    0.097258] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.097315] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.097346] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.101225] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.101428] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.101628] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.101827] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.102005] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.102186] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.102371] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.102573] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.102820] SCSI subsystem initialized
[    0.102875] libata version 3.00 loaded.
[    0.102963] usbcore: registered new interface driver usbfs
[    0.102992] usbcore: registered new interface driver hub
[    0.103022] usbcore: registered new device driver usb
[    0.103175] ACPI: WMI: Mapper loaded
[    0.103177] PCI: Using ACPI for IRQ routing
[    0.103481] Bluetooth: Core ver 2.15
[    0.103513] NET: Registered protocol family 31
[    0.103515] Bluetooth: HCI device and connection manager initialized
[    0.103519] Bluetooth: HCI socket layer initialized
[    0.103522] NetLabel: Initializing
[    0.103524] NetLabel:  domain hash size = 128
[    0.103526] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.103542] NetLabel:  unlabeled traffic allowed by default
[    0.105732] pnp: PnP ACPI init
[    0.105753] ACPI: bus type pnp registered
[    0.109856] pnp: PnP ACPI: found 13 devices
[    0.109859] ACPI: ACPI bus type pnp unregistered
[    0.109864] PnPBIOS: Disabled by ACPI PNP
[    0.109879] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.109883] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.109887] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.109891] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.109895] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.109899] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.109903] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.109907] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.109911] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.109915] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.109919] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.109922] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.109927] system 00:00: iomem range 0x100000-0x4fffffff could not be reserved
[    0.109931] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.109940] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.109944] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.109948] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.109952] system 00:02: ioport range 0x1600-0x162f has been reserved
[    0.109955] system 00:02: ioport range 0x1632-0x167f has been reserved
[    0.109959] system 00:02: ioport range 0x1630-0x1631 has been reserved
[    0.144648] AppArmor: AppArmor Filesystem Enabled
[    0.144682] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.144686] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.144691] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.144696] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.144705] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.144709] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
[    0.144714] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
[    0.144720] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.144725] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.144731] pci 0000:02:00.1: CardBus bridge, secondary bus 0000:07
[    0.144734] pci 0000:02:00.1:   IO window: 0x004800-0x0048ff
[    0.144739] pci 0000:02:00.1:   IO window: 0x004c00-0x004cff
[    0.144745] pci 0000:02:00.1:   PREFETCH window: 0xec000000-0xefffffff
[    0.144750] pci 0000:02:00.1:   MEM window: 0xc8000000-0xcbffffff
[    0.144756] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.144760] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
[    0.144766] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
[    0.144771] pci 0000:00:1e.0:   PREFETCH window: 0xe8000000-0xefffffff
[    0.144788] pci 0000:00:1e.0: setting latency timer to 64
[    0.145142] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.145146] PCI: setting IRQ 11 as level-triggered
[    0.145152] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.145491] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.145496] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.145504] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.145508] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.145512] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.145515] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.145519] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.145523] pci_bus 0000:02: resource 0 io:  [0x4000-0x8fff]
[    0.145526] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xcfffffff]
[    0.145530] pci_bus 0000:02: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.145533] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.145536] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.145540] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.145543] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.145547] pci_bus 0000:03: resource 2 pref mem [0xe8000000-0xebffffff]
[    0.145551] pci_bus 0000:03: resource 3 mem: [0xc4000000-0xc7ffffff]
[    0.145554] pci_bus 0000:07: resource 0 io:  [0x4800-0x48ff]
[    0.145557] pci_bus 0000:07: resource 1 io:  [0x4c00-0x4cff]
[    0.145561] pci_bus 0000:07: resource 2 pref mem [0xec000000-0xefffffff]
[    0.145564] pci_bus 0000:07: resource 3 mem: [0xc8000000-0xcbffffff]
[    0.145605] NET: Registered protocol family 2
[    0.145717] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.146123] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.147546] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.148503] TCP: Hash tables configured (established 131072 bind 65536)
[    0.148507] TCP reno registered
[    0.148661] NET: Registered protocol family 1
[    0.148772] Trying to unpack rootfs image as initramfs...
[    0.414771] Freeing initrd memory: 7463k freed
[    0.425157] Simple Boot Flag at 0x35 set to 0x1
[    0.425270] cpufreq-nforce2: No nForce2 chipset.
[    0.425320] Scanning for low memory corruption every 60 seconds
[    0.425486] audit: initializing netlink socket (disabled)
[    0.425521] type=2000 audit(1262374432.424:1): initialized
[    0.436615] highmem bounce pool size: 64 pages
[    0.436623] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.438409] VFS: Disk quotas dquot_6.5.2
[    0.438481] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.439150] fuse init (API version 7.12)
[    0.439253] msgmni has been set to 1725
[    0.439497] alg: No test for stdrng (krng)
[    0.439511] io scheduler noop registered
[    0.439514] io scheduler anticipatory registered
[    0.439516] io scheduler deadline registered
[    0.439571] io scheduler cfq registered (default)
[    0.439659] pci 0000:01:00.0: Boot video device
[    0.439778] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.439806] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.440778] ACPI: AC Adapter [AC] (on-line)
[    0.440864] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.440870] ACPI: Power Button [PWRF]
[    0.440928] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.441655] ACPI: Lid Switch [LID]
[    0.441712] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.441718] ACPI: Sleep Button [SLPB]
[    0.444090] Marking TSC unstable due to TSC halts in idle
[    0.444111] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.444140] processor LNXCPU:00: registered as cooling_device0
[    0.444145] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.448018] Switched to high resolution mode on CPU 0
[    0.451096] thermal LNXTHERM:01: registered as thermal_zone0
[    0.451106] ACPI: Thermal Zone [THM0] (48 C)
[    0.451158] isapnp: Scanning for PnP cards...
[    0.804515] isapnp: No Plug & Play device found
[    0.805834] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.806763] serial 00:0a: activated
[    0.806855] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.806971] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.806978] serial 0000:00:1f.6: PCI INT B disabled
[    0.808163] brd: module loaded
[    0.808720] loop: module loaded
[    0.808806] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.808931] ata_piix 0000:00:1f.1: version 2.13
[    0.808940] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.809294] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.809299] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.809347] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.809427] scsi0 : ata_piix
[    0.809577] scsi1 : ata_piix
[    0.810575] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    0.810579] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    0.811589] Fixed MDIO Bus: probed
[    0.811632] PPP generic driver version 2.4.2
[    0.811733] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.844348] ACPI: Battery Slot [BAT0] (battery present)
[    0.849360] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.849702] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.849707] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.849721] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.849726] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.849791] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.853706] ehci_hcd 0000:00:1d.7: debug port 1
[    0.853713] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.853723] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    0.868037] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.868126] usb usb1: configuration #1 chosen from 1 choice
[    0.868162] hub 1-0:1.0: USB hub found
[    0.868172] hub 1-0:1.0: 6 ports detected
[    0.868245] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.868269] uhci_hcd: USB Universal Host Controller Interface driver
[    0.868732] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.868739] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.868747] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.868751] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.868786] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.868808] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    0.868901] usb usb2: configuration #1 chosen from 1 choice
[    0.868933] hub 2-0:1.0: USB hub found
[    0.868949] hub 2-0:1.0: 2 ports detected
[    0.869470] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.869811] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.869816] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.869823] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.869827] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.869868] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.869889] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    0.869978] usb usb3: configuration #1 chosen from 1 choice
[    0.870010] hub 3-0:1.0: USB hub found
[    0.870017] hub 3-0:1.0: 2 ports detected
[    0.870069] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.870076] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.870080] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.870112] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.870134] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    0.870232] usb usb4: configuration #1 chosen from 1 choice
[    0.870266] hub 4-0:1.0: USB hub found
[    0.870274] hub 4-0:1.0: 2 ports detected
[    0.870381] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.877461] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.877468] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.877532] mice: PS/2 mouse device common for all mice
[    0.877649] rtc_cmos 00:06: RTC can wake from S4
[    0.877688] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.877705] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.877826] device-mapper: uevent: version 1.0.3
[    0.877921] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.878009] device-mapper: multipath: version 1.1.0 loaded
[    0.878013] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.878148] EISA: Probing bus 0 at eisa.0
[    0.878154] Cannot allocate resource for EISA slot 1
[    0.878157] Cannot allocate resource for EISA slot 2
[    0.878159] Cannot allocate resource for EISA slot 3
[    0.878162] Cannot allocate resource for EISA slot 4
[    0.878165] Cannot allocate resource for EISA slot 5
[    0.878167] Cannot allocate resource for EISA slot 6
[    0.878170] Cannot allocate resource for EISA slot 7
[    0.878173] Cannot allocate resource for EISA slot 8
[    0.878175] EISA: Detected 0 cards.
[    0.878268] cpuidle: using governor ladder
[    0.878340] cpuidle: using governor menu
[    0.878919] TCP cubic registered
[    0.879117] NET: Registered protocol family 10
[    0.879616] lo: Disabled Privacy Extensions
[    0.879969] NET: Registered protocol family 17
[    0.879988] Bluetooth: L2CAP ver 2.13
[    0.879991] Bluetooth: L2CAP socket layer initialized
[    0.879994] Bluetooth: SCO (Voice Link) ver 0.6
[    0.879996] Bluetooth: SCO socket layer initialized
[    0.880056] Bluetooth: RFCOMM TTY layer initialized
[    0.880060] Bluetooth: RFCOMM socket layer initialized
[    0.880062] Bluetooth: RFCOMM ver 1.11
[    0.880195] P-state transition latency capped at 20 uS
[    0.880489] Using IPI No-Shortcut mode
[    0.880554] PM: Resume from disk failed.
[    0.880574] registered taskstats version 1
[    0.880698]   Magic number: 10:88:596
[    0.880783] rtc_cmos 00:06: setting system clock to 2010-01-01 19:33:53 UTC (1262374433)
[    0.880788] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.880791] EDD information not available.
[    0.883556] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.972584] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0201, max UDMA/33
[    0.973086] ata1.00: ATA-6: HTS541040G9AT00, MB2IA60A, max UDMA/100
[    0.973090] ata1.00: 78140160 sectors, multi 16: LBA 
[    0.988372] ata2.00: configured for UDMA/33
[    0.988785] ata1.00: configured for UDMA/100
[    0.988936] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2I PQ: 0 ANSI: 5
[    0.989094] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.989145] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.989203] sd 0:0:0:0: [sda] Write Protect is off
[    0.989207] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.989236] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.989381]  sda:
[    0.994200] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4242N 0201 PQ: 0 ANSI: 5
[    1.006971] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.006976] Uniform CD-ROM driver Revision: 3.20
[    1.007066] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.007111] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.008868]  sda1 sda2 sda3 < sda5 sda6 >
[    1.048247] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.048266] Freeing unused kernel memory: 540k freed
[    1.048676] Write protecting the kernel text: 4568k
[    1.048720] Write protecting the kernel read-only data: 1836k
[    1.251120] Linux agpgart interface v0.103
[    1.255469] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    1.258926] Floppy drive(s): fd0 is 1.44M
[    1.263569] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/device:04/input/input5
[    1.263616] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.293349] FDC 0 is a National Semiconductor PC87306
[    1.392269] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.410888] [drm] Initialized drm 1.1.0 20060810
[    1.436492] [drm] radeon default to kernel modesetting DISABLED.
[    1.436655] pci 0000:01:00.0: power state changed by ACPI to D0
[    1.436669] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.438115] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    1.444358] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    1.444362] Copyright (c) 1999-2006 Intel Corporation.
[    1.444407] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.699760] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:85:d0:68
[    1.733543] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.125834] PM: Starting manual resume from disk
[    3.125840] PM: Resume from partition 8:6
[    3.125842] PM: Checking hibernation image.
[    3.125998] PM: Resume from disk failed.
[    3.144002] EXT4-fs (sda5): 
[    3.144025] Clocksource tsc unstable (delta = -122278568 ns)
[    3.144029] barriers enabled
[    3.175447] kjournald2 starting: pid 361, dev sda5:8, commit interval 5 seconds
[    3.175459] EXT4-fs (sda5): delayed allocation enabled
[    3.175464] EXT4-fs: file extents enabled
[    3.176822] EXT4-fs: mballoc enabled
[    3.176839] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    3.937214] type=1505 audit(1262374436.555:2): operation="profile_load" pid=384 name=/usr/share/gdm/guest-session/Xsession
[    3.939996] type=1505 audit(1262374436.555:3): operation="profile_load" pid=385 name=/sbin/dhclient3
[    3.940804] type=1505 audit(1262374436.559:4): operation="profile_load" pid=385 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.941235] type=1505 audit(1262374436.559:5): operation="profile_load" pid=385 name=/usr/lib/connman/scripts/dhclient-script
[    3.981463] type=1505 audit(1262374436.599:6): operation="profile_load" pid=386 name=/usr/bin/evince
[    3.993877] type=1505 audit(1262374436.611:7): operation="profile_load" pid=386 name=/usr/bin/evince-previewer
[    4.001205] type=1505 audit(1262374436.619:8): operation="profile_load" pid=386 name=/usr/bin/evince-thumbnailer
[    4.042331] type=1505 audit(1262374436.659:9): operation="profile_load" pid=388 name=/usr/lib/cups/backend/cups-pdf
[    4.876891] Adding 562232k swap on /dev/sda6.  Priority:-1 extents:1 across:562232k 
[    5.088412] EXT4-fs (sda5): internal journal on sda5:8
[    5.238572] udev: starting version 147
[    5.997792] lp: driver loaded but no devices found
[    6.005928] parport_pc 00:0b: reported by Plug and Play ACPI
[    6.005970] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[    6.070246] ppdev: user-space parallel port driver
[    6.100245] lp0: using parport0 (interrupt-driven).
[    6.299237] Non-volatile memory driver v1.3
[    6.303011] intel_rng: FWH not detected
[    6.395355] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.974670] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[    6.974677] serio: Synaptics pass-through port at isa0060/serio1/input0
[    7.025370] irda_init()
[    7.025383] NET: Registered protocol family 23
[    7.029111] lib80211: common routines for IEEE802.11 drivers
[    7.029114] lib80211_crypt: registered algorithm 'NULL'
[    7.032031] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    7.572408] ieee80211: 802.11 data/management/control stack, git-1.1.13
[    7.572414] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    7.647558] thinkpad_acpi: ThinkPad ACPI Extras v0.23
[    7.647563] thinkpad_acpi: http://ibm-acpi.sf.net/
[    7.647566] thinkpad_acpi: ThinkPad BIOS 1RETDIWW (3.14 ), EC 1RHT71WW-3.04
[    7.647569] thinkpad_acpi: IBM ThinkPad T42, model 2378R4U
[    7.654208] Registered led device: tpacpi::thinklight
[    7.654245] Registered led device: tpacpi::power
[    7.654264] Registered led device: tpacpi::standby
[    7.658611] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[    7.729866] nsc-ircc 00:0c: activated
[    7.729873] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[    7.730040] nsc-ircc, chip->init
[    7.730049] nsc-ircc, Found chip at base=0x02e
[    7.730073] nsc-ircc, driver loaded (Dag Brattli)
[    7.730846] IrDA: Registered device irda0
[    7.730849] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[    7.756347] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.800879] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    7.800884] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    7.800984] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    7.801049] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    7.801094] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[    8.104405] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[    8.104469] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0552]
[    8.104489] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[    8.104493] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[    8.104499] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21b22, devctl 0x64
[    8.336453] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0430, PCI irq 11
[    8.336459] yenta_cardbus 0000:02:00.0: Socket status: 30000086
[    8.336468] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[    8.336473] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
[    8.337829] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[    8.337834] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[    8.338047] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0552]
[    8.338063] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
[    8.338067] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
[    8.338072] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21b22, devctl 0x64
[    8.451022] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    8.451057] Intel ICH 0000:00:1f.5: setting latency timer to 64
[    8.466758] __ratelimit: 6 callbacks suppressed
[    8.466763] type=1505 audit(1262392441.083:12): operation="profile_replace" pid=781 name=/usr/share/gdm/guest-session/Xsession
[    8.468626] type=1505 audit(1262392441.087:13): operation="profile_replace" pid=782 name=/sbin/dhclient3
[    8.469416] type=1505 audit(1262392441.087:14): operation="profile_replace" pid=782 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.469852] type=1505 audit(1262392441.087:15): operation="profile_replace" pid=782 name=/usr/lib/connman/scripts/dhclient-script
[    8.474968] type=1505 audit(1262392441.091:16): operation="profile_replace" pid=783 name=/usr/bin/evince
[    8.488384] type=1505 audit(1262392441.107:17): operation="profile_replace" pid=783 name=/usr/bin/evince-previewer
[    8.495787] type=1505 audit(1262392441.111:18): operation="profile_replace" pid=783 name=/usr/bin/evince-thumbnailer
[    8.507308] type=1505 audit(1262392441.123:19): operation="profile_replace" pid=785 name=/usr/lib/cups/backend/cups-pdf
[    8.508297] type=1505 audit(1262392441.127:20): operation="profile_replace" pid=785 name=/usr/sbin/cupsd
[    8.511107] type=1505 audit(1262392441.127:21): operation="profile_replace" pid=786 name=/usr/sbin/tcpdump
[    8.568455] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0430, PCI irq 11
[    8.568461] yenta_cardbus 0000:02:00.1: Socket status: 30000086
[    8.568471] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[    8.568476] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
[    8.569864] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[    8.569869] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[    9.376038] intel8x0_measure_ac97_clock: measured 55375 usecs (2668 samples)
[    9.376043] intel8x0: clocking to 48000
[    9.760470] psmouse serio2: ID: 10 00 64
[    9.761587] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[    9.762600] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[    9.763034] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[    9.763414] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[    9.763936] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[    9.764702] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[    9.765693] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[    9.766126] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    9.766495] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    9.767011] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   13.293795] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   13.516755] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[   13.651558] ADDRCONF(NETDEV_UP): eth0: link is not ready
```While WEP is NOT required, and I'm connected:
```

[    0.089797] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.089804] pci 0000:01:00.0: reg 14 io port: [0x3000-0x30ff]
[    0.089810] pci 0000:01:00.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.089826] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.089846] pci 0000:01:00.0: supports D1 D2
[    0.089882] pci 0000:00:01.0: bridge io port: [0x3000-0x3fff]
[    0.089887] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.089891] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
[    0.089927] pci 0000:02:00.0: reg 10 32bit mmio: [0xb0000000-0xb0000fff]
[    0.089947] pci 0000:02:00.0: supports D1 D2
[    0.089950] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089955] pci 0000:02:00.0: PME# disabled
[    0.089991] pci 0000:02:00.1: reg 10 32bit mmio: [0xb1000000-0xb1000fff]
[    0.090010] pci 0000:02:00.1: supports D1 D2
[    0.090013] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090018] pci 0000:02:00.1: PME# disabled
[    0.090059] pci 0000:02:01.0: reg 10 32bit mmio: [0xc0220000-0xc023ffff]
[    0.090067] pci 0000:02:01.0: reg 14 32bit mmio: [0xc0200000-0xc020ffff]
[    0.090075] pci 0000:02:01.0: reg 18 io port: [0x8000-0x803f]
[    0.090095] pci 0000:02:01.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.090115] pci 0000:02:01.0: PME# supported from D0 D3hot D3cold
[    0.090120] pci 0000:02:01.0: PME# disabled
[    0.090153] pci 0000:02:02.0: reg 10 32bit mmio: [0xc0210000-0xc0210fff]
[    0.090198] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.090203] pci 0000:02:02.0: PME# disabled
[    0.090243] pci 0000:00:1e.0: transparent bridge
[    0.090248] pci 0000:00:1e.0: bridge io port: [0x4000-0x8fff]
[    0.090254] pci 0000:00:1e.0: bridge 32bit mmio: [0xc0200000-0xcfffffff]
[    0.090260] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.090300] pci_bus 0000:00: on NUMA node 0
[    0.090306] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.090363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.090394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.094275] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.094478] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.094679] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.094878] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.095057] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.095238] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.095423] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.095624] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.095872] SCSI subsystem initialized
[    0.095928] libata version 3.00 loaded.
[    0.096028] usbcore: registered new interface driver usbfs
[    0.096057] usbcore: registered new interface driver hub
[    0.096088] usbcore: registered new device driver usb
[    0.096239] ACPI: WMI: Mapper loaded
[    0.096241] PCI: Using ACPI for IRQ routing
[    0.096545] Bluetooth: Core ver 2.15
[    0.096576] NET: Registered protocol family 31
[    0.096579] Bluetooth: HCI device and connection manager initialized
[    0.096582] Bluetooth: HCI socket layer initialized
[    0.096585] NetLabel: Initializing
[    0.096587] NetLabel:  domain hash size = 128
[    0.096589] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.096606] NetLabel:  unlabeled traffic allowed by default
[    0.098782] pnp: PnP ACPI init
[    0.098803] ACPI: bus type pnp registered
[    0.102898] pnp: PnP ACPI: found 13 devices
[    0.102902] ACPI: ACPI bus type pnp unregistered
[    0.102907] PnPBIOS: Disabled by ACPI PNP
[    0.102922] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.102927] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.102930] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.102934] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.102938] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.102942] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.102946] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.102950] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.102954] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.102958] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.102962] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.102966] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.102970] system 00:00: iomem range 0x100000-0x4fffffff could not be reserved
[    0.102974] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.102984] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.102988] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.102992] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.102995] system 00:02: ioport range 0x1600-0x162f has been reserved
[    0.102999] system 00:02: ioport range 0x1632-0x167f has been reserved
[    0.103003] system 00:02: ioport range 0x1630-0x1631 has been reserved
[    0.137691] AppArmor: AppArmor Filesystem Enabled
[    0.137724] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.137728] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.137734] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.137738] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.137748] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.137751] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
[    0.137757] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
[    0.137762] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.137768] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.137773] pci 0000:02:00.1: CardBus bridge, secondary bus 0000:07
[    0.137776] pci 0000:02:00.1:   IO window: 0x004800-0x0048ff
[    0.137782] pci 0000:02:00.1:   IO window: 0x004c00-0x004cff
[    0.137787] pci 0000:02:00.1:   PREFETCH window: 0xec000000-0xefffffff
[    0.137792] pci 0000:02:00.1:   MEM window: 0xc8000000-0xcbffffff
[    0.137798] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.137802] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
[    0.137808] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
[    0.137814] pci 0000:00:1e.0:   PREFETCH window: 0xe8000000-0xefffffff
[    0.137830] pci 0000:00:1e.0: setting latency timer to 64
[    0.138187] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.138190] PCI: setting IRQ 11 as level-triggered
[    0.138196] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.138535] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.138539] pci 0000:02:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.138548] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.138552] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.138556] pci_bus 0000:01: resource 0 io:  [0x3000-0x3fff]
[    0.138559] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.138563] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.138566] pci_bus 0000:02: resource 0 io:  [0x4000-0x8fff]
[    0.138570] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xcfffffff]
[    0.138574] pci_bus 0000:02: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.138577] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.138580] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.138584] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.138587] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.138591] pci_bus 0000:03: resource 2 pref mem [0xe8000000-0xebffffff]
[    0.138595] pci_bus 0000:03: resource 3 mem: [0xc4000000-0xc7ffffff]
[    0.138598] pci_bus 0000:07: resource 0 io:  [0x4800-0x48ff]
[    0.138601] pci_bus 0000:07: resource 1 io:  [0x4c00-0x4cff]
[    0.138605] pci_bus 0000:07: resource 2 pref mem [0xec000000-0xefffffff]
[    0.138609] pci_bus 0000:07: resource 3 mem: [0xc8000000-0xcbffffff]
[    0.138650] NET: Registered protocol family 2
[    0.138762] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.139170] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.140630] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.141543] TCP: Hash tables configured (established 131072 bind 65536)
[    0.141547] TCP reno registered
[    0.141704] NET: Registered protocol family 1
[    0.141815] Trying to unpack rootfs image as initramfs...
[    0.407857] Freeing initrd memory: 7463k freed
[    0.418223] Simple Boot Flag at 0x35 set to 0x1
[    0.418336] cpufreq-nforce2: No nForce2 chipset.
[    0.418384] Scanning for low memory corruption every 60 seconds
[    0.418551] audit: initializing netlink socket (disabled)
[    0.418587] type=2000 audit(1262375263.416:1): initialized
[    0.429682] highmem bounce pool size: 64 pages
[    0.429690] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.431475] VFS: Disk quotas dquot_6.5.2
[    0.431548] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.432235] fuse init (API version 7.12)
[    0.432338] msgmni has been set to 1725
[    0.432582] alg: No test for stdrng (krng)
[    0.432596] io scheduler noop registered
[    0.432599] io scheduler anticipatory registered
[    0.432601] io scheduler deadline registered
[    0.432656] io scheduler cfq registered (default)
[    0.432744] pci 0000:01:00.0: Boot video device
[    0.432863] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.432893] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.433432] ACPI: AC Adapter [AC] (on-line)
[    0.433519] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.433524] ACPI: Power Button [PWRF]
[    0.433583] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.434067] ACPI: Lid Switch [LID]
[    0.434124] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.434130] ACPI: Sleep Button [SLPB]
[    0.436356] Marking TSC unstable due to TSC halts in idle
[    0.436378] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.436407] processor LNXCPU:00: registered as cooling_device0
[    0.436411] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.440021] Switched to high resolution mode on CPU 0
[    0.442895] thermal LNXTHERM:01: registered as thermal_zone0
[    0.442905] ACPI: Thermal Zone [THM0] (55 C)
[    0.442957] isapnp: Scanning for PnP cards...
[    0.796391] isapnp: No Plug & Play device found
[    0.797715] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.798643] serial 00:0a: activated
[    0.798735] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.798851] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.798858] serial 0000:00:1f.6: PCI INT B disabled
[    0.799964] brd: module loaded
[    0.800594] loop: module loaded
[    0.800681] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.800807] ata_piix 0000:00:1f.1: version 2.13
[    0.800817] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.801169] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.801174] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.801223] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.801300] scsi0 : ata_piix
[    0.801447] scsi1 : ata_piix
[    0.802445] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    0.802449] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    0.803456] Fixed MDIO Bus: probed
[    0.803499] PPP generic driver version 2.4.2
[    0.803600] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.835517] ACPI: Battery Slot [BAT0] (battery present)
[    0.840404] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.840746] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.840751] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.840766] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.840770] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.840836] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.844735] ehci_hcd 0000:00:1d.7: debug port 1
[    0.844742] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.844751] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    0.860036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.860125] usb usb1: configuration #1 chosen from 1 choice
[    0.860161] hub 1-0:1.0: USB hub found
[    0.860171] hub 1-0:1.0: 6 ports detected
[    0.860246] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.860270] uhci_hcd: USB Universal Host Controller Interface driver
[    0.860780] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.860787] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.860794] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.860798] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.860833] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.860855] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    0.860949] usb usb2: configuration #1 chosen from 1 choice
[    0.860980] hub 2-0:1.0: USB hub found
[    0.860996] hub 2-0:1.0: 2 ports detected
[    0.861443] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.861787] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.861792] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.861799] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.861803] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.861843] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.861865] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    0.861953] usb usb3: configuration #1 chosen from 1 choice
[    0.861984] hub 3-0:1.0: USB hub found
[    0.861992] hub 3-0:1.0: 2 ports detected
[    0.862044] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.862051] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.862055] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.862087] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.862109] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    0.862206] usb usb4: configuration #1 chosen from 1 choice
[    0.862240] hub 4-0:1.0: USB hub found
[    0.862248] hub 4-0:1.0: 2 ports detected
[    0.862355] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.869324] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.869331] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.869395] mice: PS/2 mouse device common for all mice
[    0.869511] rtc_cmos 00:06: RTC can wake from S4
[    0.869550] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.869568] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.869688] device-mapper: uevent: version 1.0.3
[    0.869784] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.869872] device-mapper: multipath: version 1.1.0 loaded
[    0.869876] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.870010] EISA: Probing bus 0 at eisa.0
[    0.870017] Cannot allocate resource for EISA slot 1
[    0.870020] Cannot allocate resource for EISA slot 2
[    0.870023] Cannot allocate resource for EISA slot 3
[    0.870025] Cannot allocate resource for EISA slot 4
[    0.870028] Cannot allocate resource for EISA slot 5
[    0.870031] Cannot allocate resource for EISA slot 6
[    0.870033] Cannot allocate resource for EISA slot 7
[    0.870036] Cannot allocate resource for EISA slot 8
[    0.870038] EISA: Detected 0 cards.
[    0.870131] cpuidle: using governor ladder
[    0.870204] cpuidle: using governor menu
[    0.870782] TCP cubic registered
[    0.870980] NET: Registered protocol family 10
[    0.871476] lo: Disabled Privacy Extensions
[    0.871829] NET: Registered protocol family 17
[    0.871849] Bluetooth: L2CAP ver 2.13
[    0.871851] Bluetooth: L2CAP socket layer initialized
[    0.871854] Bluetooth: SCO (Voice Link) ver 0.6
[    0.871856] Bluetooth: SCO socket layer initialized
[    0.871895] Bluetooth: RFCOMM TTY layer initialized
[    0.871899] Bluetooth: RFCOMM socket layer initialized
[    0.871901] Bluetooth: RFCOMM ver 1.11
[    0.872055] P-state transition latency capped at 20 uS
[    0.872340] Using IPI No-Shortcut mode
[    0.872405] PM: Resume from disk failed.
[    0.872424] registered taskstats version 1
[    0.872557]   Magic number: 10:294:798
[    0.872639] rtc_cmos 00:06: setting system clock to 2010-01-01 19:47:44 UTC (1262375264)
[    0.872644] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.872647] EDD information not available.
[    0.874738] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.964583] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0201, max UDMA/33
[    0.965087] ata1.00: ATA-6: HTS541040G9AT00, MB2IA60A, max UDMA/100
[    0.965091] ata1.00: 78140160 sectors, multi 16: LBA 
[    0.980373] ata2.00: configured for UDMA/33
[    0.980785] ata1.00: configured for UDMA/100
[    0.980937] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2I PQ: 0 ANSI: 5
[    0.981077] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.981128] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.981186] sd 0:0:0:0: [sda] Write Protect is off
[    0.981190] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.981219] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.981366]  sda:
[    0.986539] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4242N 0201 PQ: 0 ANSI: 5
[    0.999204]  sda1 sda2 sda3 <sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.999303] Uniform CD-ROM driver Revision: 3.20
[    0.999394] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.999439] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.018379]  sda5 sda6 >
[    1.038572] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.038591] Freeing unused kernel memory: 540k freed
[    1.039003] Write protecting the kernel text: 4568k
[    1.039048] Write protecting the kernel read-only data: 1836k
[    1.202625] Linux agpgart interface v0.103
[    1.207010] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[    1.222941] Floppy drive(s): fd0 is 1.44M
[    1.240158] FDC 0 is a National Semiconductor PC87306
[    1.257408] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/device:04/input/input5
[    1.257469] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.371427] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.395775] [drm] Initialized drm 1.1.0 20060810
[    1.421440] [drm] radeon default to kernel modesetting DISABLED.
[    1.421603] pci 0000:01:00.0: power state changed by ACPI to D0
[    1.421618] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.423099] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    1.429348] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    1.429352] Copyright (c) 1999-2006 Intel Corporation.
[    1.429398] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.682683] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:85:d0:68
[    1.717534] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.105311] PM: Starting manual resume from disk
[    3.105316] PM: Resume from partition 8:6
[    3.105319] PM: Checking hibernation image.
[    3.105474] PM: Resume from disk failed.
[    3.123422] EXT4-fs (sda5): barriers enabled
[    3.136024] Clocksource tsc unstable (delta = -122272639 ns)
[    3.154725] kjournald2 starting: pid 342, dev sda5:8, commit interval 5 seconds
[    3.154736] EXT4-fs (sda5): delayed allocation enabled
[    3.154741] EXT4-fs: file extents enabled
[    3.156096] EXT4-fs: mballoc enabled
[    3.156115] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    3.905441] type=1505 audit(1262375267.531:2): operation="profile_load" pid=365 name=/usr/share/gdm/guest-session/Xsession
[    3.908216] type=1505 audit(1262375267.535:3): operation="profile_load" pid=366 name=/sbin/dhclient3
[    3.909004] type=1505 audit(1262375267.535:4): operation="profile_load" pid=366 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.909436] type=1505 audit(1262375267.535:5): operation="profile_load" pid=366 name=/usr/lib/connman/scripts/dhclient-script
[    3.949630] type=1505 audit(1262375267.575:6): operation="profile_load" pid=367 name=/usr/bin/evince
[    3.962067] type=1505 audit(1262375267.587:7): operation="profile_load" pid=367 name=/usr/bin/evince-previewer
[    3.969407] type=1505 audit(1262375267.595:8): operation="profile_load" pid=367 name=/usr/bin/evince-thumbnailer
[    4.010553] type=1505 audit(1262375267.635:9): operation="profile_load" pid=369 name=/usr/lib/cups/backend/cups-pdf
[    4.986061] Adding 562232k swap on /dev/sda6.  Priority:-1 extents:1 across:562232k 
[    5.114303] udev: starting version 147
[    5.740981] lp: driver loaded but no devices found
[    5.759634] parport_pc 00:0b: reported by Plug and Play ACPI
[    5.759678] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[    5.876841] lp0: using parport0 (interrupt-driven).
[    5.934868] ppdev: user-space parallel port driver
[    5.968692] Non-volatile memory driver v1.3
[    5.997357] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.019394] intel_rng: FWH not detected
[    6.426041] thinkpad_acpi: ThinkPad ACPI Extras v0.23
[    6.426046] thinkpad_acpi: http://ibm-acpi.sf.net/
[    6.426048] thinkpad_acpi: ThinkPad BIOS 1RETDIWW (3.14 ), EC 1RHT71WW-3.04
[    6.426051] thinkpad_acpi: IBM ThinkPad T42, model 2378R4U
[    6.433199] Registered led device: tpacpi::thinklight
[    6.433236] Registered led device: tpacpi::power
[    6.433259] Registered led device: tpacpi::standby
[    6.436928] input: ThinkPad Extra Buttons as /devices/virtual/input/input6
[    6.606943] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[    6.606951] serio: Synaptics pass-through port at isa0060/serio1/input0
[    6.650657] irda_init()
[    6.650669] NET: Registered protocol family 23
[    6.658243] lib80211: common routines for IEEE802.11 drivers
[    6.658247] lib80211_crypt: registered algorithm 'NULL'
[    6.663712] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[    7.062055] ieee80211: 802.11 data/management/control stack, git-1.1.13
[    7.062060] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    7.130414] nsc-ircc 00:0c: activated
[    7.130420] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[    7.130587] nsc-ircc, chip->init
[    7.130596] nsc-ircc, Found chip at base=0x02e
[    7.130620] nsc-ircc, driver loaded (Dag Brattli)
[    7.131404] IrDA: Registered device irda0
[    7.131408] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[    7.176344] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.282142] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    7.282146] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    7.282250] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    7.282322] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    7.282379] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[    7.585562] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[    7.585626] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0552]
[    7.585646] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[    7.585649] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[    7.585655] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21b22, devctl 0x64
[    7.824857] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x0430, PCI irq 11
[    7.824864] yenta_cardbus 0000:02:00.0: Socket status: 30000086
[    7.824872] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[    7.824876] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
[    7.826233] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[    7.826237] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[    7.826442] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0552]
[    7.826459] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
[    7.826462] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
[    7.826468] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21b22, devctl 0x64
[    8.056464] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0430, PCI irq 11
[    8.056470] yenta_cardbus 0000:02:00.1: Socket status: 30000086
[    8.056479] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[    8.056483] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
[    8.057847] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[    8.057852] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[    8.170828] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    8.170863] Intel ICH 0000:00:1f.5: setting latency timer to 64
[    8.293037] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[    8.294067] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[    8.294502] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[    8.294871] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[    8.295388] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[    8.717262] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[    8.718257] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[    8.718691] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    8.719071] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    8.719589] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    9.096097] intel8x0_measure_ac97_clock: measured 55460 usecs (2672 samples)
[    9.096173] intel8x0: clocking to 48000
[    9.503219] psmouse serio2: ID: 10 00 64
[   13.139628] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   13.377541] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[   24.743203] EXT4-fs (sda5): internal journal on sda5:8
[   25.598395] __ratelimit: 6 callbacks suppressed
[   25.598400] type=1505 audit(1262393289.223:12): operation="profile_replace" pid=898 name=/usr/share/gdm/guest-session/Xsession
[   25.600267] type=1505 audit(1262393289.227:13): operation="profile_replace" pid=899 name=/sbin/dhclient3
[   25.601060] type=1505 audit(1262393289.227:14): operation="profile_replace" pid=899 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   25.601500] type=1505 audit(1262393289.227:15): operation="profile_replace" pid=899 name=/usr/lib/connman/scripts/dhclient-script
[   25.607881] type=1505 audit(1262393289.231:16): operation="profile_replace" pid=900 name=/usr/bin/evince
[   25.624566] type=1505 audit(1262393289.251:17): operation="profile_replace" pid=900 name=/usr/bin/evince-previewer
[   25.632423] type=1505 audit(1262393289.259:18): operation="profile_replace" pid=900 name=/usr/bin/evince-thumbnailer
[   25.650203] type=1505 audit(1262393289.275:19): operation="profile_replace" pid=908 name=/usr/lib/cups/backend/cups-pdf
[   25.651140] type=1505 audit(1262393289.275:20): operation="profile_replace" pid=908 name=/usr/sbin/cupsd
[   25.654800] type=1505 audit(1262393289.279:21): operation="profile_replace" pid=910 name=/usr/sbin/tcpdump
[   26.776256] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   26.776277] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   26.776316] pci 0000:01:00.0: putting AGP V2 device into 4x mode
```

---

### Post by DumpsterCat on 2010-01-01
it should be noted that while Ubuntu does detect a wired network "out of the box" it does Not automatically detect wireless.  Discovered this detail when trying to "sell" ubuntu to my xp using wife.  So, you Will need to, if you havent already, set network name, ssid, etc, before a connection can be obtained.

---

### Post by dutchg on 2010-01-01
> **DumpsterCat said:**
> it should be noted that while Ubuntu does detect a wired network "out of the box" it does Not automatically detect wireless.  Discovered this detail when trying to "sell" ubuntu to my xp using wife.  So, you Will need to, if you havent already, set network name, ssid, etc, before a connection can be obtained.


I thought I'd done that. I mean, it sees the ssid, I tell it yes, that's the one I want to connect with, and I put in the required WEP key. Is there some more basic setting I'm not thinking about? How does "network name" differ from SSID?  Thanks much.

---

### Post by yumgnomeandthensome on 2010-01-01
After reading your output and doing some reading on other posts i reckon you should check page two of this link, a post made by chilli555 is very helpful.

[http://ubuntuforums.org/showthread.php?t=172810&page=2](http://ubuntuforums.org/showthread.php?t=172810&page=2)

other things to consider/explain
1/ hiding ssid just means that you do not broadcast it, ie your neighbours will not see it (unless they use scanning software not just the OS detection)
2/ wpa is more secure than wep, you might want to use this once you get wep working
3/ without configuring any network details in your ubuntu, you should be able to view your ssid in the detected list, or if you are hiding your ssid, you should be able to choose the 'connect to hidden network' option - this is a good option for ur problem, as it will show you that your ubuntu detects the authentication method 'wep' when you type in your ssid. But yeah, read that post above and you should be right

on that note my use of  'wcid' is proving fruitful, i've not had the 10% not connecting problem since using it. Very nice easy graphicaly display to. Just search for ubuntu wcid install. 

Wireless networking/default.keyrings have been the only painful problem i've had since using linux (2 months). Its the only thing that puts me off hyping my friends up to stop using Windows.

Evan

---

### Post by dutchg on 2010-01-01
Thanks for the ideas, Evan. I'm going to poke at it some more tomorrow, and will report results. I appreciate your help. 

Dutch

---

### Post by dutchg on 2010-01-03
Evan, I'm just exploring that link you gave me for the wireless fix. I'm such I newbie I don't know what I'm looking at. When he says:

```
sudo gedit /etc/network/interfaces to make the relevant interface entry look like this:

auto wlan0 
iface wlan0 inet dhcp
wireless-key 93c8530b2df51711bad5596f91
```

I'm not sure what that means. I assume it means to open up terminal and type in **sudo gedit /etc/network/interfaces**, yah? But what does that do? Pull up a text file I'm supposed to edit and then what? 

And if my connection is eth01, what do I replace in that formula? the wlan0?

Thanks for the help. You won't find a greener user than me.

Dutch

---

### Post by yumgnomeandthensome on 2010-01-04
from what i am reading with v9.10 you should't need  to delve into the cmd line in order to get your wireless working unless you have a serious problem.
the fact that you can connect without encryption is a good sign. 
I think you need to determine that your key is correctly entered in. Is it possible to look at your linksys logs once you have tried to connect with WEP? Have a search for web key issues (capitals or not etc). Maybe make your wep key more basic to start with?

as mentioned i've moved to using the network mgr 'wcid'. I've found it useful in showing me at what stage i have the odd problem with connecting.
If you want to try using this then install it via
1/ system/administration/synaptic package mgr
2/ put wcip in the search bar (top right - ish)
3/ then mark it for install
4/ once marked hit the green tick for APPLY

once installed you'll find it in the list
1/ applications/internet (from top left of your screen)

For more info about wcid just search the ubuntu information base there is a great explaination of it.

good luck

---

### Post by dutchg on 2010-01-04
> **yumgnomeandthensome said:**
> 
as mentioned i've moved to using the network mgr 'wcid'. I've found it useful in showing me at what stage i have the odd problem with connecting.
If you want to try using this then install it via
1/ system/administration/synaptic package mgr
2/ put wcip in the search bar (top right - ish)
3/ then mark it for install
4/ once marked hit the green tick for APPLY

once installed you'll find it in the list
1/ applications/internet (from top left of your screen)

For more info about wcid just search the ubuntu information base there is a great explaination of it.

good luck

I followed these steps to the letter, and I reloaded from the web, but the synaptic package mgr could not find wcid.  What am I doing wrong?

Re the WEP key, I don't know how to do the linksys log, but I've double-checked the WEP key a hundred times. It works for Windows, so I'm confident I'm typing the right key.

---

### Post by dutchg on 2010-01-07
Bump.

Would appreciate any more help here. I don't want to give up on Linux yet!

thanks,
Dutchg

---

### Post by dutchg on 2010-01-09
Bump again.  Any more ideas?

---

### Post by yumgnomeandthensome on 2010-01-09
With a bit of searching you should be able to install wcid, you can try from cmd line if synaptic is't working for you. A quick search result for wcid how to will show you how.

by using wcid i could see that I was having the odd problem with actually 'obtaining an ip address' not authenticating like i first thought, wcid would show you each step and where it fails.

I've now statically assigned my reserved ip address and don't have the odd problem of not connecting.

---

