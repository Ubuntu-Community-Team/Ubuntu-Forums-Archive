---
title: "Hooking up Netgear WG311v3 - Warning error"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by littlboz on 2010-04-03
Hello I am an absolute beginner to Ubuntu and I need help setting up my wireless; I wrote more then I probably needed to.

My wireless card which came with the computer is "Netgear Wg311v3 802.11g Wireless PCI Adapter"

I am running Ubuntu on dual boot with a Gateway Windows XP computer.

My version of Ubuntu is Karmic Koala 9.10 (I am running 32 - bit even though my computer can use 64 - bit).

I followed these instruction: [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

It appeared to work, I followed all the steps and everything went smoothly, but when I restarted my computer my wireless was not being recognized nor the wireless driver  in system>administration>hardware drivers (only three drivers are recognized they are NVIDIA accelerated graphics driver (version <xxx>) where "x" is a number. 

I tried to do some of the commands over again and I continually get 
      "WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."

To try and remedy this I went to google and found this : [https://answers.launchpad.net/ubuntu/+question/68175](https://answers.launchpad.net/ubuntu/+question/68175)
It was too cryptic for me and I suspect the helper e-mailed the user so the answer is not explicitly stated.

I think errors might have resulted from the following:
In my Instruction  [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

-where it states "Installing your driver" my WG311v3 file was not a .INF, it is a .sys however I encountered no problems during this step that I can recall. In the same section it states, "replace 'devid' with PCI ID or the USB ID of your card in the form........."
I am rather positive that I did not replace the word devid with my PCI ID. I think this is where the largest error occurred.

If the easiest solution is to reinstall something then that is fine, just state how.

Additional info that might not matter: 
-I downloaded my Netgear software I think from here [http://www.downv.com/Windows/download-NETGEAR-WG311v3-802-11g-Wireless-PCI-Adapter-10019877.htm](http://www.downv.com/Windows/download-NETGEAR-WG311v3-802-11g-Wireless-PCI-Adapter-10019877.htm) 
-I downloaded the ndiswrapper software using system < administration < synaptic package manager.

When this was all said and done I noticed a ndiswrapper icon with a silver lock on the upper right-hand corner in the file places<boswell. (boswell is my user name). What is this? Can it be deleted? My unzipped version of the netgear software is also contained in this folder as well.

~thank you and have a sensual day.

---

### Post by chili555 on 2010-04-03
> I tried to do some of the commands over again and I continually get
"WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."That's a fairly harmless warning, and can be easily rectified. Open a terminal and do:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```Now, the real issue is, does your wireless work as expected? If so, what else do we need to fix? If not, please post:```
ndiswrapper -l
```Thanks.

---

### Post by littlboz on 2010-04-03
It states it is installed:

boswell@boswell-desktop:~$ ndiswrapper -l
wg311v3 : driver installed
    device (11AB:1FAA) present

I also went to find my PCI ID and I got the following:

boswell@boswell-desktop:~$ lspci -n
00:00.0 0500: 10de:02f1 (rev a2)
00:00.1 0500: 10de:02fa (rev a2)
00:00.2 0500: 10de:02fe (rev a2)
00:00.3 0500: 10de:02f8 (rev a2)
00:00.4 0500: 10de:02f9 (rev a2)
00:00.5 0500: 10de:02ff (rev a2)
00:00.6 0500: 10de:027f (rev a2)
00:00.7 0500: 10de:027e (rev a2)
00:02.0 0604: 10de:02fc (rev a1)
00:03.0 0604: 10de:02fd (rev a1)
00:04.0 0604: 10de:02fb (rev a1)
00:05.0 0300: 10de:0242 (rev a2)
00:09.0 0500: 10de:0270 (rev a2)
00:0a.0 0601: 10de:0261 (rev a2)
00:0a.1 0c05: 10de:0264 (rev a2)
00:0a.2 0500: 10de:0272 (rev a2)
00:0b.0 0c03: 10de:026d (rev a2)
00:0b.1 0c03: 10de:026e (rev a2)
00:0d.0 0101: 10de:0265 (rev a1)
00:0e.0 0101: 10de:0266 (rev a1)
00:10.0 0604: 10de:026f (rev a2)
00:10.1 0403: 10de:026c (rev a2)
00:14.0 0680: 10de:0269 (rev a1)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
04:06.0 0200: 11ab:1faa (rev 03)
04:07.0 0780: 14f1:2f20
04:08.0 0c00: 1106:3044 (rev 80)
boswell@boswell-desktop:~$

---

### Post by chili555 on 2010-04-03
> boswell@boswell-desktop:~$ ndiswrapper -l
wg311v3 : driver installed
device (11AB:1FAA) presentLooks perfect. My question remains: does your wireless work as expected? Do you see networks in Network Manager? Does it try to connect? What are your symptoms?

---

### Post by littlboz on 2010-04-03
> **chili555 said:**
> Looks perfect. My question remains: does your wireless work as expected? Do you see networks in Network Manager? Does it try to connect? What are your symptoms?


It is not trying to connect.

---

### Post by littlboz on 2010-04-03
in network connection under the wireless tab nothing shows up.

---

### Post by chili555 on 2010-04-03
Please post:```
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by littlboz on 2010-04-03
boswell@boswell-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

boswell@boswell-desktop:~$ sudo iwlist wlan0 sc

---

### Post by chili555 on 2010-04-03
No wireless interface is being created. Let's try to find out what's going wrong. Please post:```
dmesg | grep ndis
```That pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by littlboz on 2010-04-03
I wish I could make you cookies.

anyways I typed in your code but nothing happened. I then typed in just dsmg and got a big whollop of text:





    0.090933] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
[    0.090937] pci 0000:00:0e.0: reg 20 io port: [0xe000-0xe00f]
[    0.090942] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.091024] pci 0000:00:10.1: reg 10 32bit mmio: [0xfe028000-0xfe02bfff]
[    0.091056] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.091060] pci 0000:00:10.1: PME# disabled
[    0.091091] pci 0000:00:14.0: reg 10 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.091096] pci 0000:00:14.0: reg 14 io port: [0xdc00-0xdc07]
[    0.091119] pci 0000:00:14.0: supports D1 D2
[    0.091121] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091125] pci 0000:00:14.0: PME# disabled
[    0.091226] pci 0000:00:02.0: bridge io port: [0xc000-0xcfff]
[    0.091229] pci 0000:00:02.0: bridge 32bit mmio: [0xfd700000-0xfd7fffff]
[    0.091233] pci 0000:00:02.0: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    0.091269] pci 0000:00:03.0: bridge io port: [0xb000-0xbfff]
[    0.091272] pci 0000:00:03.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.091276] pci 0000:00:03.0: bridge 64bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.091312] pci 0000:00:04.0: bridge io port: [0x9000-0x9fff]
[    0.091315] pci 0000:00:04.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
[    0.091318] pci 0000:00:04.0: bridge 64bit mmio pref: [0xfd800000-0xfd8fffff]
[    0.091355] pci 0000:04:06.0: reg 10 32bit mmio: [0xfdbc0000-0xfdbcffff]
[    0.091361] pci 0000:04:06.0: reg 14 32bit mmio: [0xfdbe0000-0xfdbeffff]
[    0.091424] pci 0000:04:07.0: reg 10 32bit mmio: [0xfdbd0000-0xfdbdffff]
[    0.091430] pci 0000:04:07.0: reg 14 io port: [0xac00-0xac07]
[    0.091460] pci 0000:04:07.0: PME# supported from D3hot D3cold
[    0.091464] pci 0000:04:07.0: PME# disabled
[    0.091492] pci 0000:04:08.0: reg 10 32bit mmio: [0xfdbff000-0xfdbff7ff]
[    0.091498] pci 0000:04:08.0: reg 14 io port: [0xa800-0xa87f]
[    0.091532] pci 0000:04:08.0: supports D2
[    0.091534] pci 0000:04:08.0: PME# supported from D2 D3hot D3cold
[    0.091538] pci 0000:04:08.0: PME# disabled
[    0.091565] pci 0000:00:10.0: transparent bridge
[    0.091568] pci 0000:00:10.0: bridge io port: [0xa000-0xafff]
[    0.091571] pci 0000:00:10.0: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.091575] pci 0000:00:10.0: bridge 32bit mmio pref: [0xfda00000-0xfdafffff]
[    0.091584] pci_bus 0000:00: on NUMA node 0
[    0.091588] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.091803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.178465] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[    0.178619] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.178772] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[    0.178926] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 *10 11 14 15)
[    0.179078] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179230] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179384] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[    0.179536] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179690] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.179843] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.179997] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[    0.180153] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.180308] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.180462] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[    0.180614] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.180768] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.180924] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.181082] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.181236] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.181395] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.181583] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.181768] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.181952] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.182136] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.182319] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.182503] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.182687] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    0.182874] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.183058] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.183243] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.183430] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.183615] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.183801] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[    0.183986] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.184178] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.184364] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.184551] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.184737] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.184922] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.185108] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.185293] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.185450] SCSI subsystem initialized
[    0.185486] libata version 3.00 loaded.
[    0.185542] usbcore: registered new interface driver usbfs
[    0.185552] usbcore: registered new interface driver hub
[    0.185572] usbcore: registered new device driver usb
[    0.185676] ACPI: WMI: Mapper loaded
[    0.185678] PCI: Using ACPI for IRQ routing
[    0.185802] Bluetooth: Core ver 2.15
[    0.185823] NET: Registered protocol family 31
[    0.185824] Bluetooth: HCI device and connection manager initialized
[    0.185827] Bluetooth: HCI socket layer initialized
[    0.185829] NetLabel: Initializing
[    0.185830] NetLabel:  domain hash size = 128
[    0.185832] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.185842] NetLabel:  unlabeled traffic allowed by default
[    0.187131] pnp: PnP ACPI init
[    0.187145] ACPI: bus type pnp registered
[    0.191938] pnp: PnP ACPI: found 12 devices
[    0.191940] ACPI: ACPI bus type pnp unregistered
[    0.191944] PnPBIOS: Disabled by ACPI PNP
[    0.191952] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.191955] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.191958] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.191961] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.191964] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.191967] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.191969] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.191972] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.191976] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.191979] system 00:01: iomem range 0x38000000-0x3fffffff has been reserved
[    0.191984] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.191987] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.192012] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.192017] system 00:0b: iomem range 0xd1800-0xd3fff has been reserved
[    0.192020] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[    0.192023] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[    0.192026] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    0.192029] system 00:0b: iomem range 0x37ee0000-0x37efffff could not be reserved
[    0.192032] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.192035] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.192037] system 00:0b: iomem range 0x100000-0x37edffff could not be reserved
[    0.192040] system 00:0b: iomem range 0x37f00000-0x3fefffff could not be reserved
[    0.192044] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.192047] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.192050] system 00:0b: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.192053] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.192056] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.192059] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.226699] AppArmor: AppArmor Filesystem Enabled
[    0.226729] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.226732] pci 0000:00:02.0:   IO window: 0xc000-0xcfff
[    0.226735] pci 0000:00:02.0:   MEM window: 0xfd700000-0xfd7fffff
[    0.226739] pci 0000:00:02.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.226743] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.226745] pci 0000:00:03.0:   IO window: 0xb000-0xbfff
[    0.226748] pci 0000:00:03.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.226751] pci 0000:00:03.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.226755] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    0.226758] pci 0000:00:04.0:   IO window: 0x9000-0x9fff
[    0.226761] pci 0000:00:04.0:   MEM window: 0xfd900000-0xfd9fffff
[    0.226764] pci 0000:00:04.0:   PREFETCH window: 0x000000fd800000-0x000000fd8fffff
[    0.226768] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.226771] pci 0000:00:10.0:   IO window: 0xa000-0xafff
[    0.226775] pci 0000:00:10.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.226778] pci 0000:00:10.0:   PREFETCH window: 0xfda00000-0xfdafffff
[    0.226786] pci 0000:00:02.0: setting latency timer to 64
[    0.226791] pci 0000:00:03.0: setting latency timer to 64
[    0.226795] pci 0000:00:04.0: setting latency timer to 64
[    0.226799] pci 0000:00:10.0: setting latency timer to 64
[    0.226804] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.226806] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.226809] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.226811] pci_bus 0000:01: resource 1 mem: [0xfd700000-0xfd7fffff]
[    0.226814] pci_bus 0000:01: resource 2 pref mem [0xfde00000-0xfdefffff]
[    0.226817] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.226819] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.226822] pci_bus 0000:02: resource 2 pref mem [0xfdc00000-0xfdcfffff]
[    0.226824] pci_bus 0000:03: resource 0 io:  [0x9000-0x9fff]
[    0.226827] pci_bus 0000:03: resource 1 mem: [0xfd900000-0xfd9fffff]
[    0.226829] pci_bus 0000:03: resource 2 pref mem [0xfd800000-0xfd8fffff]
[    0.226832] pci_bus 0000:04: resource 0 io:  [0xa000-0xafff]
[    0.226834] pci_bus 0000:04: resource 1 mem: [0xfdb00000-0xfdbfffff]
[    0.226837] pci_bus 0000:04: resource 2 pref mem [0xfda00000-0xfdafffff]
[    0.226840] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.226842] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.226872] NET: Registered protocol family 2
[    0.226952] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.227257] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.227900] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.228026] Switched to high resolution mode on CPU 0
[    0.228277] TCP: Hash tables configured (established 131072 bind 65536)
[    0.228279] TCP reno registered
[    0.228357] NET: Registered protocol family 1
[    0.228409] Trying to unpack rootfs image as initramfs...
[    0.413171] Freeing initrd memory: 7470k freed
[    0.417203] cpufreq-nforce2: No nForce2 chipset.
[    0.417225] Scanning for low memory corruption every 60 seconds
[    0.417312] audit: initializing netlink socket (disabled)
[    0.417325] type=2000 audit(1270320310.416:1): initialized
[    0.425542] highmem bounce pool size: 64 pages
[    0.425547] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.426699] VFS: Disk quotas dquot_6.5.2
[    0.426749] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.427237] fuse init (API version 7.12)
[    0.427324] msgmni has been set to 1735
[    0.427485] alg: No test for stdrng (krng)
[    0.427495] io scheduler noop registered
[    0.427498] io scheduler anticipatory registered
[    0.427500] io scheduler deadline registered
[    0.427535] io scheduler cfq registered (default)
[    0.427555] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    0.427559] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.427591] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.427612] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.427638] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.427643] pci 0000:00:05.0: Boot video device
[    2.040023] pci 0000:00:0b.1: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    2.040079] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    2.040086] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    2.040139] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    2.040144] pci 0000:00:10.0: Enabling HT MSI Mapping
[    2.040200] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    2.040208] pci 0000:00:10.1: Enabling HT MSI Mapping
[    2.040310]   alloc irq_desc for 24 on node -1
[    2.040312]   alloc kstat_irqs on node -1
[    2.040319] pcieport-driver 0000:00:02.0: irq 24 for MSI/MSI-X
[    2.040324] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    2.040388]   alloc irq_desc for 25 on node -1
[    2.040390]   alloc kstat_irqs on node -1
[    2.040394] pcieport-driver 0000:00:03.0: irq 25 for MSI/MSI-X
[    2.040398] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    2.040455]   alloc irq_desc for 26 on node -1
[    2.040456]   alloc kstat_irqs on node -1
[    2.040460] pcieport-driver 0000:00:04.0: irq 26 for MSI/MSI-X
[    2.040464] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.040513] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.040535] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.040638] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.040641] ACPI: Power Button [PWRF]
[    2.040686] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.040688] ACPI: Power Button [PWRB]
[    2.040735] fan PNP0C0B:00: registered as cooling_device0
[    2.040740] ACPI: Fan [FAN] (on)
[    2.041140] processor LNXCPU:00: registered as cooling_device1
[    2.046701] thermal LNXTHERM:01: registered as thermal_zone0
[    2.046708] ACPI: Thermal Zone [THRM] (40 C)
[    2.046747] isapnp: Scanning for PnP cards...
[    2.399609] isapnp: No Plug & Play device found
[    2.400519] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.400630] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.400885] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.401699] brd: module loaded
[    2.402090] loop: module loaded
[    2.402155] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.402325] sata_nv 0000:00:0e.0: version 3.5
[    2.402625] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    2.402629]   alloc irq_desc for 23 on node -1
[    2.402630]   alloc kstat_irqs on node -1
[    2.402639] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    2.402641] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    2.402680] sata_nv 0000:00:0e.0: setting latency timer to 64
[    2.402808] scsi0 : sata_nv
[    2.402878] scsi1 : sata_nv
[    2.403012] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
[    2.403015] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
[    2.403086] pata_amd 0000:00:0d.0: version 0.4.1
[    2.403117] pata_amd 0000:00:0d.0: setting latency timer to 64
[    2.403197] scsi2 : pata_amd
[    2.403253] scsi3 : pata_amd
[    2.403875] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    2.403878] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    2.404451] Fixed MDIO Bus: probed
[    2.404479] PPP generic driver version 2.4.2
[    2.404548] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.404838] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    2.404841]   alloc irq_desc for 22 on node -1
[    2.404843]   alloc kstat_irqs on node -1
[    2.404850] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    2.404858] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.404860] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.404885] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    2.404916] ehci_hcd 0000:00:0b.1: debug port 1
[    2.404920] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    2.404937] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xfe02e000
[    2.416028] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    2.416099] usb usb1: configuration #1 chosen from 1 choice
[    2.416124] hub 1-0:1.0: USB hub found
[    2.416131] hub 1-0:1.0: 8 ports detected
[    2.416179] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.416467] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    2.416470]   alloc irq_desc for 21 on node -1
[    2.416472]   alloc kstat_irqs on node -1
[    2.416479] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    2.416486] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.416489] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.416512] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    2.416535] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xfe02f000
[    2.474055] usb usb2: configuration #1 chosen from 1 choice
[    2.474078] hub 2-0:1.0: USB hub found
[    2.474086] hub 2-0:1.0: 8 ports detected
[    2.474129] uhci_hcd: USB Universal Host Controller Interface driver
[    2.474183] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.474185] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.474615] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.474662] mice: PS/2 mouse device common for all mice
[    2.474740] rtc_cmos 00:04: RTC can wake from S4
[    2.474766] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.474797] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    2.474879] device-mapper: uevent: version 1.0.3
[    2.474955] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    2.475029] device-mapper: multipath: version 1.1.0 loaded
[    2.475031] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.475145] EISA: Probing bus 0 at eisa.0
[    2.475150] Cannot allocate resource for EISA slot 1
[    2.475152] Cannot allocate resource for EISA slot 2
[    2.475169] EISA: Detected 0 cards.
[    2.475207] cpuidle: using governor ladder
[    2.475209] cpuidle: using governor menu
[    2.475632] TCP cubic registered
[    2.475758] NET: Registered protocol family 10
[    2.476143] lo: Disabled Privacy Extensions
[    2.476409] NET: Registered protocol family 17
[    2.476421] Bluetooth: L2CAP ver 2.13
[    2.476423] Bluetooth: L2CAP socket layer initialized
[    2.476425] Bluetooth: SCO (Voice Link) ver 0.6
[    2.476427] Bluetooth: SCO socket layer initialized
[    2.476447] Bluetooth: RFCOMM TTY layer initialized
[    2.476449] Bluetooth: RFCOMM socket layer initialized
[    2.476451] Bluetooth: RFCOMM ver 1.11
[    2.476459] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (1 cpu cores) (version 2.20.00)
[    2.476494] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[    2.476496] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[    2.476499] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[    2.476501] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    2.476530] Using IPI No-Shortcut mode
[    2.476574] PM: Resume from disk failed.
[    2.476583] registered taskstats version 1
[    2.476693]   Magic number: 6:357:796
[    2.476780] rtc_cmos 00:04: setting system clock to 2010-04-03 18:45:13 UTC (1270320313)
[    2.476783] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.476784] EDD information not available.
[    2.494639] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.568434] ata3.00: ATA-7: ST3200826A, 3.03, max UDMA/100
[    2.568437] ata3.00: 390721968 sectors, multi 16: LBA48 
[    2.568458] ata3: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc600c500) ACPI=0x3f01f (20:600:0x13)
[    2.584378] ata3.00: configured for UDMA/100
[    2.722472] ata1: SATA link down (SStatus 0 SControl 300)
[    3.042472] ata2: SATA link down (SStatus 0 SControl 300)
[    3.042565] scsi 2:0:0:0: Direct-Access     ATA      ST3200826A       3.03 PQ: 0 ANSI: 5
[    3.042649] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    3.042680] sd 2:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    3.042715] sd 2:0:0:0: [sda] Write Protect is off
[    3.042717] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.042735] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.042832]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    3.085165] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.088020] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    3.204311] ata4.00: ATAPI: HL-DT-ST DVD-RW GWA-4165B, DG01, max UDMA/66
[    3.204332] ata4: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc600c500) ACPI=0x1f01f (30:600:0x13)
[    3.220262] ata4.00: configured for UDMA/66
[    3.225903] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4165B DG01 PQ: 0 ANSI: 5
[    3.237686] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.237689] Uniform CD-ROM driver Revision: 3.20
[    3.237743] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.237772] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.237787] Freeing unused kernel memory: 540k freed
[    3.238117] Write protecting the kernel text: 4580k
[    3.238145] Write protecting the kernel read-only data: 1840k
[    3.315150] usb 2-1: configuration #1 chosen from 1 choice
[    3.324987] usbcore: registered new interface driver hiddev
[    3.333493] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input4
[    3.333557] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-1/input0
[    3.333576] usbcore: registered new interface driver usbhid
[    3.333578] usbhid: v2.6:USB HID core driver
[    3.402847] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    3.403185] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    3.403189]   alloc irq_desc for 20 on node -1
[    3.403191]   alloc kstat_irqs on node -1
[    3.403202] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    3.403208] forcedeth 0000:00:14.0: setting latency timer to 64
[    3.403242] nv_probe: set workaround bit for reversed mac addr
[    3.480748] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    3.480754]   alloc irq_desc for 16 on node -1
[    3.480756]   alloc kstat_irqs on node -1
[    3.480766] ohci1394 0000:04:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    3.538041] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fdbff000-fdbff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.652026] usb 2-5: new full speed USB device using ohci_hcd and address 3
[    3.867116] usb 2-5: configuration #1 chosen from 1 choice
[    3.875518] Initializing USB Mass Storage driver...
[    3.875597] scsi4 : SCSI emulation for USB Mass Storage devices
[    3.875660] usbcore: registered new interface driver usb-storage
[    3.875662] USB Mass Storage support registered.
[    3.875712] usb-storage: device found at 3
[    3.875713] usb-storage: waiting for device to settle before scanning
[    3.920746] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x50ef @ 1, addr 00:40:ca:91:cf:77
[    3.920749] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    4.469722] PM: Starting manual resume from disk
[    4.469726] PM: Resume from partition 8:5
[    4.469728] PM: Checking hibernation image.
[    4.469858] PM: Resume from disk failed.
[    4.490619] kjournald starting.  Commit interval 5 seconds
[    4.490628] EXT3-fs: mounted filesystem with writeback data mode.
[    4.812113] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040ca0703045d32]
[    5.245022] type=1505 audit(1270320316.267:2): operation="profile_load" pid=420 name=/usr/share/gdm/guest-session/Xsession
[    5.253062] type=1505 audit(1270320316.275:3): operation="profile_load" pid=421 name=/sbin/dhclient3
[    5.253327] type=1505 audit(1270320316.275:4): operation="profile_load" pid=421 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.253479] type=1505 audit(1270320316.275:5): operation="profile_load" pid=421 name=/usr/lib/connman/scripts/dhclient-script
[    5.291295] type=1505 audit(1270320316.311:6): operation="profile_load" pid=422 name=/usr/bin/evince
[    5.295690] type=1505 audit(1270320316.315:7): operation="profile_load" pid=422 name=/usr/bin/evince-previewer
[    5.298300] type=1505 audit(1270320316.319:8): operation="profile_load" pid=422 name=/usr/bin/evince-thumbnailer
[    5.315608] type=1505 audit(1270320316.335:9): operation="profile_load" pid=424 name=/usr/lib/cups/backend/cups-pdf
[    5.315936] type=1505 audit(1270320316.335:10): operation="profile_load" pid=424 name=/usr/sbin/cupsd
[    8.873090] usb-storage: device scan complete
[    8.880063] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    8.887062] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    8.894059] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    8.901060] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    8.901374] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    8.901443] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    8.901512] sd 4:0:0:2: Attached scsi generic sg4 type 0
[    8.901579] sd 4:0:0:3: Attached scsi generic sg5 type 0
[    8.956055] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    8.967053] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[    8.978054] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[    8.989102] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   18.996640] Adding 1951856k swap on /dev/sda5.  Priority:-1 extents:1 across:1951856k 
[   19.012162] udev: starting version 147
[   19.062972] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   19.062978] ACPI: I/O resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM00 [0x1c40-0x1c45]
[   19.062981] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.062984] nForce2_smbus 0000:00:0a.1: Error probing SMB2.
[   19.112251] lp: driver loaded but no devices found
[   19.151991] parport_pc 00:08: reported by Plug and Play ACPI
[   19.152040] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   19.196920] EXT3 FS on sda6, internal journal
[   19.327681] lp0: using parport0 (interrupt-driven).
[   19.352579] ppdev: user-space parallel port driver
[   19.456282] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.482062] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   19.482068] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   19.482090] HDA Intel 0000:00:10.1: setting latency timer to 64
[   19.842712] __ratelimit: 3 callbacks suppressed
[   19.842716] type=1505 audit(1270334730.863:12): operation="profile_replace" pid=977 name=/usr/share/gdm/guest-session/Xsession
[   19.843889] type=1505 audit(1270334730.863:13): operation="profile_replace" pid=978 name=/sbin/dhclient3
[   19.844188] type=1505 audit(1270334730.867:14): operation="profile_replace" pid=978 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.844339] type=1505 audit(1270334730.867:15): operation="profile_replace" pid=978 name=/usr/lib/connman/scripts/dhclient-script
[   19.849281] type=1505 audit(1270334730.871:16): operation="profile_replace" pid=979 name=/usr/bin/evince
[   19.862872] type=1505 audit(1270334730.883:17): operation="profile_replace" pid=979 name=/usr/bin/evince-previewer
[   19.865573] type=1505 audit(1270334730.887:18): operation="profile_replace" pid=979 name=/usr/bin/evince-thumbnailer
[   19.870052] type=1505 audit(1270334730.891:19): operation="profile_replace" pid=986 name=/usr/lib/cups/backend/cups-pdf
[   19.870382] type=1505 audit(1270334730.891:20): operation="profile_replace" pid=986 name=/usr/sbin/cupsd
[   19.871766] type=1505 audit(1270334730.891:21): operation="profile_replace" pid=987 name=/usr/sbin/tcpdump
[   20.048227] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   20.072091] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input5
[   30.152019] eth0: no IPv6 routers present
[   82.724031] Clocksource tsc unstable (delta = -255115089 ns)
[ 2619.016518] mtrr: no MTRR for d0000000,8000000 found
[ 5980.379547] mtrr: no MTRR for d0000000,8000000 found
[ 6134.436616] mtrr: no MTRR for d0000000,8000000 found
boswell@boswell-desktop:~$

---

### Post by littlboz on 2010-04-03
I also just typed it in without the line in the middle

boswell@boswell-desktop:~$ dmesg grep ndis
Usage: dmesg [-c] [-n level] [-s bufsize]
boswell@boswell-desktop:~$

---

### Post by chili555 on 2010-04-03
Please do the following commands, in order, proofreading carefully. Post the result of the last one:```
sudo su
echo ndiswrapper >> /etc/modules
modprobe ndiswrapper
exit
iwconfig
```Thanks.

My diet won't handle cookies, but thanks for the thought!

---

### Post by littlboz on 2010-04-03
boswell@boswell-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

boswell@boswell-desktop:~$

---

### Post by chili555 on 2010-04-03
It appears that the only problem was that the module ndiswrapper was not loading automagically, which we fixed. Now you have a wireless interface. Now does Network Manager see networks and connect?

---

### Post by littlboz on 2010-04-03
woh, I don't know how this got here but when I right click on the icon of my internet connection (on the desktop right hand corner-ish) it now states enable netowrking AND enable wireless. 

In the same drop down menu it states "connection information" and then "edit connections"

I click "Edit connection" which has the following tabs: "wired" "wireless" "mobile broadband" "VPN" and "DSL"

I click on wireless and it is blank, recognizing no router.

---

### Post by littlboz on 2010-04-03
> **littlboz said:**
> woh, I don't know how this got here but when I right click on the icon of my internet connection (on the desktop right hand corner-ish) it now states enable netowrking AND enable wireless. 

In the same drop down menu it states "connection information" and then "edit connections"

I click "Edit connection" which has the following tabs: "wired" "wireless" "mobile broadband" "VPN" and "DSL"

I click on wireless and it is blank, recognizing no router.
The wireless tab also has a little button that says "add" I can add a wireless connection. A little lost on how to do that though and I feel that it should "see" it rather then me adding it.

---

### Post by chili555 on 2010-04-03
*Left*-click the icon and see if you see networks, hopefully yours, like the attached. Connect and give us a woo-hoo.

---

### Post by littlboz on 2010-04-03
erm, I don't follow, here are some attached pictures of what I was talking about 
[IMG]http://%20/home/boswell/Desktop/Screenshot.png[/IMG]

---

### Post by littlboz on 2010-04-03
ah, left click. Yehp 

That was my only problem lol!!!!!!!!!


>.<

Thank you soooo much

---

### Post by chili555 on 2010-04-03
Those are what you see if you right-click the icon. I am asking you to ***left***-click the icon so as to see available networks.

Left-click, please.

---

### Post by chili555 on 2010-04-03
> **littlboz said:**
> ah, left click. Yehp 

That was my only problem lol!!!!!!!!!


>.<

Thank you soooo muchSo, are you connected?

---

### Post by littlboz on 2010-04-03
Yehp, my eathernet is out and it works fine. amazing how clicking with a different finger changes everything.

---

### Post by chili555 on 2010-04-03
Glad it's working! Enjoy.

---

