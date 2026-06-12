---
title: "Problem connecting to Ethernet"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by i20234 on 2011-03-24
I'm running on a IBM T60p.

Runnning ubuntu-10.10-desktop-i386

Here is the ifconfog:
```

jonathan@jonathan-ThinkPad-T60p:~$ ifconfig -a
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
          RX packets:556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42880 (42.8 KB)  TX bytes:42880 (42.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:3a:43:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

I tried looking up how to use the ifconfig myself to fix it but couldn't find anything. Can you link me on how to do so or just explain in your own words? Would be much appreciated. trying to learn as much as I can from the get go.

Thanks

---

### Post by Cheesehead on 2011-03-24
Are you trying to connect to a wired network or a wireless network?

Are you connecting using Network Manager, or manually?

---

### Post by i20234 on 2011-03-24
Wired.

And I thought I could just connect directly and it would connect on its own because linux is great with drivers.

Do you mean Network tools under System>Administration?

here is a screen of  it and information about the unknown device:

[http://img3.imageshack.us/img3/2941/screenshotrym.png](http://img3.imageshack.us/img3/2941/screenshotrym.png)

---

### Post by spiky001 on 2011-03-24
If you are using a wired connection that is eth0 I dont know why it,s not showing up in ifconfig. Irda is infa red device. Try ifconfig only

---

### Post by i20234 on 2011-03-24
[http://img13.imageshack.us/img13/1563/screenshot1ll.png](http://img13.imageshack.us/img13/1563/screenshot1ll.png)

My old partition was of Win7 and after I installed the Ethernet driver it worked.

---

### Post by i20234 on 2011-03-24
Going to try the LTS version, see if it makes a difference...

---

### Post by i20234 on 2011-03-24
Nope, same problem

Someone help!  :(

---

### Post by Cheesehead on 2011-03-24
Post the results of the following commands:
```

dmesg | grep eth
cat /var/log/syslog | grep eth

```
These will show most of the relevant startup or operational errors with the word fragment 'eth' in them, including 'ethernet' or 'eth0'. With luck, one of those lines will tell us what is happening to the eth0 interface.

---

### Post by i20234 on 2011-03-24
I copied and pasted in terminal but nothing showed.

I put "dmesg cat" but so many results came up I cant even view them all even if I scroll up.

Sorry for my ignorance

---

### Post by josephmills on 2011-03-24
I am new to this gnu/linux but have you tried to pull the Ethernet cable out and put it back in? How long ago did you install ubuntu? Have you right clicked on the  network sign and enable networking? also have you tried to reset your modem/router? can you connect via wifi? also could you post 
```

lspci

```

---

### Post by i20234 on 2011-03-25
> **josephmills said:**
> I am new to this gnu/linux but have you tried to pull the Ethernet cable out and put it back in? How long ago did you install ubuntu? Have you right clicked on the  network sign and enable networking? also have you tried to reset your modem/router? can you connect via wifi? also could you post 
```

lspci

```

Just tried unplugging and plugging it back, still doesn't work.

I installed it about 2 hours ago.

I doubt it is the modems fault, I'm online using the same one, I can still do it if you think this is the cause.

I don't know if I can connect to the wifi, though i suspect I can because i used teh same laptop before with ubuntu and I could connect to it, I'll try to do it at a friends house tomorrow

lspci:
```

jonathan@jonathan-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5200]
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 60)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

```

---

### Post by josephmills on 2011-03-25
your eth0 card is a 
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 60)

I think you need a driver? But maybe not. When you get to wifi run
```
sudo apt-get update 
```
```
sudo apt-get upgrade 
``` 
```
sudo reboot 
```
then go to System-->Addmin--> Additional Drivers
if you need the driver then activate it.  if it is not a driver thing then I would look at this  
[http://forums.debian.net/viewtopic.php?f=7&t=54222](http://forums.debian.net/viewtopic.php?f=7&t=54222)
hope that this helps 
is it a ibm t60?

---

### Post by i20234 on 2011-03-25
T60P* Prob uses teh same network card as t60

that is a good idea, didn't think of that. Will do it, thanks :)

---

### Post by Cheesehead on 2011-03-25
> **i20234 said:**
> I copied and pasted in terminal but nothing showed.

I put "dmesg cat" but so many results came up I cant even view them all even if I scroll up.

Sorry for my ignorance

Read the instructions again. You run those commands separately. If they fail, read the error message. If you don't understand the error message, ask, search, check the man page, or post it here.

**The answers you need are in /var/log/dmesg and /var/log/syslog**.
The answers we need to help you are there, too.
The logs are indeed very long. That's why you filter them (grep is the filter).

Don't get sidetracked into hoping this 'driver' or that 'script' will somehow help. It could waste days of your time. Your system already knows exactly what the problem is, and helpfully logged it for you.

Spend your time wisely, and figure out how to access your /var/log/dmesg and /var/log/syslog. Figure out how to filter them through grep. Then post them here.

---

### Post by i20234 on 2011-03-25
Wireless Works  (sorry W doesnt Work on keyboard so copy an pasteing)

I ran all those update things but I have to go back to my house to see if it i anything, no additional drivers showed up.

Here is what showed up for teh results of **/var/log/dmesg** and [b]var
```

jonathan@jonathan-laptop:~$ /var/log/dmesg 
bash: /var/log/dmesg: Permission denied
jonathan@jonathan-laptop:~$ /var/log/syslog
bash: /var/log/syslog: Permission denied

```

I'm sure I'm inputing it wrong, I don't get what you are asking for me to put in.

---

### Post by i20234 on 2011-03-25
Here is dmesg:

```

[    0.269479] pci_bus 0000:03: resource 1 mem: [0xec000000-0xedffffff]
[    0.269482] pci_bus 0000:03: resource 2 pref mem [0xe4000000-0xe40fffff]
[    0.269485] pci_bus 0000:04: resource 0 io:  [0x6000-0x7fff]
[    0.269488] pci_bus 0000:04: resource 1 mem: [0xe8000000-0xe9ffffff]
[    0.269490] pci_bus 0000:04: resource 2 pref mem [0xe4100000-0xe41fffff]
[    0.269493] pci_bus 0000:0c: resource 0 io:  [0x8000-0x9fff]
[    0.269496] pci_bus 0000:0c: resource 1 mem: [0xea000000-0xebffffff]
[    0.269499] pci_bus 0000:0c: resource 2 pref mem [0xe4200000-0xe42fffff]
[    0.269501] pci_bus 0000:15: resource 0 io:  [0xa000-0xdfff]
[    0.269504] pci_bus 0000:15: resource 1 mem: [0xe4300000-0xe7ffffff]
[    0.269507] pci_bus 0000:15: resource 2 pref mem [0xe0000000-0xe3ffffff]
[    0.269509] pci_bus 0000:15: resource 3 io:  [0x00-0xffff]
[    0.269512] pci_bus 0000:15: resource 4 mem: [0x000000-0xffffffff]
[    0.269515] pci_bus 0000:16: resource 0 io:  [0xa000-0xa0ff]
[    0.269517] pci_bus 0000:16: resource 1 io:  [0xa400-0xa4ff]
[    0.269520] pci_bus 0000:16: resource 2 pref mem [0xe0000000-0xe3ffffff]
[    0.269523] pci_bus 0000:16: resource 3 mem: [0xc4000000-0xc7ffffff]
[    0.269564] NET: Registered protocol family 2
[    0.269668] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.269988] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.270599] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.270918] TCP: Hash tables configured (established 131072 bind 65536)
[    0.270921] TCP reno registered
[    0.271029] NET: Registered protocol family 1
[    0.271162] pci 0000:01:00.0: Boot video device
[    0.271198] Simple Boot Flag at 0x35 set to 0x1
[    0.271385] cpufreq-nforce2: No nForce2 chipset.
[    0.271422] Scanning for low memory corruption every 60 seconds
[    0.271557] audit: initializing netlink socket (disabled)
[    0.271568] type=2000 audit(1301088784.268:1): initialized
[    0.281366] highmem bounce pool size: 64 pages
[    0.281372] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.282987] VFS: Disk quotas dquot_6.5.2
[    0.283049] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.283649] fuse init (API version 7.13)
[    0.283739] msgmni has been set to 1664
[    0.283960] alg: No test for stdrng (krng)
[    0.284040] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.284043] io scheduler noop registered
[    0.284045] io scheduler anticipatory registered
[    0.284047] io scheduler deadline registered
[    0.284091] io scheduler cfq registered (default)
[    0.284232]   alloc irq_desc for 24 on node -1
[    0.284234]   alloc kstat_irqs on node -1
[    0.284243] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.284250] pcieport 0000:00:01.0: setting latency timer to 64
[    0.284371]   alloc irq_desc for 25 on node -1
[    0.284373]   alloc kstat_irqs on node -1
[    0.284382] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.284393] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.284546]   alloc irq_desc for 26 on node -1
[    0.284548]   alloc kstat_irqs on node -1
[    0.284556] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.284567] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.284718]   alloc irq_desc for 27 on node -1
[    0.284720]   alloc kstat_irqs on node -1
[    0.284728] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.284739] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.284893]   alloc irq_desc for 28 on node -1
[    0.284895]   alloc kstat_irqs on node -1
[    0.284903] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.284914] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.285016] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.285584] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 27d0 ss_vid 0 ss_did 0
[    0.285633] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.285655] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 27d2 ss_vid 0 ss_did 0
[    0.285693] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded
[    0.285714] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 27d4 ss_vid 0 ss_did 0
[    0.285751] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
[    0.285772] pciehp 0000:00:1c.3:pcie04: HPC vendor_id 8086 device_id 27d6 ss_vid 0 ss_did 0
[    0.285816] pciehp 0000:00:1c.3:pcie04: service driver pciehp loaded
[    0.285824] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.286042] ACPI: AC Adapter [AC] (on-line)
[    0.286115] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.286284] ACPI: Lid Switch [LID]
[    0.286333] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.286339] ACPI: Sleep Button [SLPB]
[    0.286396] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.286398] ACPI: Power Button [PWRF]
[    0.287079] ACPI: SSDT bfef1d36 00282 (v01  PmRef  Cpu0Ist 00000100 INTL 20050513)
[    0.287786] ACPI: SSDT bfef203d 0065A (v01  PmRef  Cpu0Cst 00000100 INTL 20050513)
[    0.290750] processor LNXCPU:00: registered as cooling_device0
[    0.291126] ACPI: SSDT bfef1c6e 000C8 (v01  PmRef  Cpu1Ist 00000100 INTL 20050513)
[    0.291627] ACPI: SSDT bfef1fb8 00085 (v01  PmRef  Cpu1Cst 00000100 INTL 20050513)
[    0.293118] processor LNXCPU:01: registered as cooling_device1
[    0.298149] thermal LNXTHERM:01: registered as thermal_zone0
[    0.298158] ACPI: Thermal Zone [THM0] (72 C)
[    0.299526] thermal LNXTHERM:02: registered as thermal_zone1
[    0.299534] ACPI: Thermal Zone [THM1] (77 C)
[    0.301070] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.302468] brd: module loaded
[    0.302945] loop: module loaded
[    0.303039] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.303147] ata_piix 0000:00:1f.2: version 2.13
[    0.303167] ata_piix 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.303173] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.305631] isapnp: Scanning for PnP cards...
[    0.386427] Freeing initrd memory: 7780k freed
[    0.414613] ACPI: Battery Slot [BAT0] (battery present)
[    0.457031] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.461056] scsi0 : ata_piix
[    0.461167] scsi1 : ata_piix
[    0.462103] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    0.462106] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    0.462476] Fixed MDIO Bus: probed
[    0.462513] PPP generic driver version 2.4.2
[    0.462590] tun: Universal TUN/TAP device driver, 1.6
[    0.462592] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.462691] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.471924] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.472160] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.472171]   alloc irq_desc for 19 on node -1
[    0.472173]   alloc kstat_irqs on node -1
[    0.472180] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.472197] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.472202] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.472236] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.472259] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.472272] ehci_hcd 0000:00:1d.7: debug port 1
[    0.476147] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.476163] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xee404000
[    0.493015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.493104] usb usb1: configuration #1 chosen from 1 choice
[    0.493137] hub 1-0:1.0: USB hub found
[    0.493146] hub 1-0:1.0: 8 ports detected
[    0.493216] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.493230] uhci_hcd: USB Universal Host Controller Interface driver
[    0.493459] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.493626] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.493631] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.493639] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.493642] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.493675] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.493710] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[    0.493804] usb usb2: configuration #1 chosen from 1 choice
[    0.493830] hub 2-0:1.0: USB hub found
[    0.493837] hub 2-0:1.0: 2 ports detected
[    0.493883]   alloc irq_desc for 17 on node -1
[    0.493886]   alloc kstat_irqs on node -1
[    0.493890] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.493896] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.493900] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.493934] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.493968] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
[    0.494061] usb usb3: configuration #1 chosen from 1 choice
[    0.494086] hub 3-0:1.0: USB hub found
[    0.494093] hub 3-0:1.0: 2 ports detected
[    0.494312] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    0.494479] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    0.494485]   alloc irq_desc for 18 on node -1
[    0.494486]   alloc kstat_irqs on node -1
[    0.494491] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.494497] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.494500] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.494532] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.494570] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    0.494667] usb usb4: configuration #1 chosen from 1 choice
[    0.494693] hub 4-0:1.0: USB hub found
[    0.494701] hub 4-0:1.0: 2 ports detected
[    0.494748] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.494754] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.494758] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.494798] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.494825] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
[    0.494914] usb usb5: configuration #1 chosen from 1 choice
[    0.494940] hub 5-0:1.0: USB hub found
[    0.494946] hub 5-0:1.0: 2 ports detected
[    0.495045] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.503430] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.503437] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.503516] mice: PS/2 mouse device common for all mice
[    0.503638] rtc_cmos 00:07: RTC can wake from S4
[    0.503678] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.503710] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.503820] device-mapper: uevent: version 1.0.3
[    0.503923] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.503987] device-mapper: multipath: version 1.1.0 loaded
[    0.503990] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.504108] EISA: Probing bus 0 at eisa.0
[    0.504115] Cannot allocate resource for EISA slot 1
[    0.504118] Cannot allocate resource for EISA slot 2
[    0.504120] Cannot allocate resource for EISA slot 3
[    0.504122] Cannot allocate resource for EISA slot 4
[    0.504124] Cannot allocate resource for EISA slot 5
[    0.504127] Cannot allocate resource for EISA slot 6
[    0.504129] Cannot allocate resource for EISA slot 7
[    0.504131] Cannot allocate resource for EISA slot 8
[    0.504133] EISA: Detected 0 cards.
[    0.504281] cpuidle: using governor ladder
[    0.504402] cpuidle: using governor menu
[    0.504846] TCP cubic registered
[    0.505024] NET: Registered protocol family 10
[    0.505479] lo: Disabled Privacy Extensions
[    0.505803] NET: Registered protocol family 17
[    0.506481] Using IPI No-Shortcut mode
[    0.506557] PM: Resume from disk failed.
[    0.506570] registered taskstats version 1
[    0.507108]   Magic number: 3:119:602
[    0.507209] rtc_cmos 00:07: setting system clock to 2011-03-25 21:33:04 UTC (1301088784)
[    0.507212] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.507214] EDD information not available.
[    0.511433] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.637527] ata2.00: ATAPI: MATSHITADVD-RAM UJ-842, RB01, max UDMA/33
[    0.653437] ata2.00: configured for UDMA/33
[    0.670449] isapnp: No Plug & Play device found
[    0.676346] ata1.00: HPA unlocked: 195369455 -> 195371568, native 195371568
[    0.676351] ata1.00: ATA-7: HTS721010G9SA00, MCZIC10H, max UDMA/100
[    0.676354] ata1.00: 195371568 sectors, multi 16: LBA48 
[    0.692642] ata1.00: configured for UDMA/100
[    0.692780] scsi 0:0:0:0: Direct-Access     ATA      HTS721010G9SA00  MCZI PQ: 0 ANSI: 5
[    0.692907] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.692919] sd 0:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    0.692969] sd 0:0:0:0: [sda] Write Protect is off
[    0.692972] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.693050] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.693191]  sda:
[    0.694927] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-842   RB01 PQ: 0 ANSI: 5
[    0.699478] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.699481] Uniform CD-ROM driver Revision: 3.20
[    0.699563] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.699604] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.711316]  sda1 sda2 < sda5 >
[    0.730216] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.730250] Freeing unused kernel memory: 660k freed
[    0.730655] Write protecting the kernel text: 4680k
[    0.730710] Write protecting the kernel read-only data: 1844k
[    0.745930] udev: starting version 151
[    0.850205] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.850209] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.850263] e1000e 0000:02:00.0: Disabling L1 ASPM
[    0.850286] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.850328] e1000e 0000:02:00.0: setting latency timer to 64
[    0.850504]   alloc irq_desc for 29 on node -1
[    0.850507]   alloc kstat_irqs on node -1
[    0.850527] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[    0.918632] 0000:02:00.0: 0000:02:00.0: The NVM Checksum Is Not Valid
[    0.928945] e1000e 0000:02:00.0: PCI INT A disabled
[    0.928956] e1000e: probe of 0000:02:00.0 failed with error -5
[    1.160462] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.192058] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.357997] usb 5-1: configuration #1 chosen from 1 choice
[    1.600048] usb 5-2: new full speed USB device using uhci_hcd and address 3
[    1.772973] usb 5-2: configuration #1 chosen from 1 choice
[    3.403828] Adding 4016120k swap on /dev/sda5.  Priority:-1 extents:1 across:4016120k 
[    3.874571] udev: starting version 151
[    5.040040] lp: driver loaded but no devices found
[    5.088320] acpi device:05: registered as cooling_device2
[    5.089435] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/LNXVIDEO:01/input/input5
[    5.089559] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    5.141858] type=1505 audit(1301088789.132:2):  operation="profile_load" pid=517 name="/sbin/dhclient3"
[    5.142664] type=1505 audit(1301088789.132:3):  operation="profile_load" pid=517 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    5.143002] type=1505 audit(1301088789.132:4):  operation="profile_load" pid=517 name="/usr/lib/connman/scripts/dhclient-script"
[    5.296268] Bluetooth: Core ver 2.15
[    5.296718] NET: Registered protocol family 31
[    5.296720] Bluetooth: HCI device and connection manager initialized
[    5.296723] Bluetooth: HCI socket layer initialized
[    5.353523] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    5.353848] usbcore: registered new interface driver btusb
[    5.395968] irda_init()
[    5.395981] NET: Registered protocol family 23
[    5.472765] nsc-ircc 00:0a: activated
[    5.472769] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[    5.472810] nsc-ircc, chip->init
[    5.472824] nsc-ircc, Found chip at base=0x164e
[    5.472865] nsc-ircc, driver loaded (Dag Brattli)
[    5.473609] IrDA: Registered device irda0
[    5.473611] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[    5.491211] Non-volatile memory driver v1.3
[    5.643761] cfg80211: Calling CRDA to update world regulatory domain
[    6.061051] intel_rng: FWH not detected
[    6.076665] Linux agpgart interface v0.103
[    6.083510] tpm_tis 00:0b: 1.2 TPM (device-id 0x3202, rev-id 5)
[    6.160589] [drm] Initialized drm 1.1.0 20060810
[    6.301141] cfg80211: World regulatory domain updated:
[    6.301145]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.301148]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.301151]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.301154]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.301156]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.301159]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.659211] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:2012]
[    6.659240] yenta_cardbus 0000:15:00.0: Using INTVAL to route CSC interrupts to PCI
[    6.659242] yenta_cardbus 0000:15:00.0: Routing CardBus interrupts to PCI
[    6.659249] yenta_cardbus 0000:15:00.0: TI: mfunc 0x01d01002, devctl 0x64
[    6.889820] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cf0, PCI irq 16
[    6.889826] yenta_cardbus 0000:15:00.0: Socket status: 30000007
[    6.889833] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xdfff
[    6.889838] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xdfff: clean.
[    6.890731] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
[    6.890734] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
[    7.283944] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[    7.283965] serio: Synaptics pass-through port at isa0060/serio1/input0
[    7.327838] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    7.457392] [drm] radeon defaulting to kernel modesetting.
[    7.457396] [drm] radeon kernel modesetting enabled.
[    7.457507] radeon 0000:01:00.0: power state changed by ACPI to D0
[    7.457550] radeon 0000:01:00.0: power state changed by ACPI to D0
[    7.457566] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.457585] radeon 0000:01:00.0: setting latency timer to 64
[    7.459435] [drm] radeon: Initializing kernel modesetting.
[    7.459543] [drm] register mmio base: 0xEE100000
[    7.459545] [drm] register mmio size: 65536
[    7.459662] ATOM BIOS: Lenovo
[    7.459904] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[    7.459953] [drm] Generation 2 PCI interface, using max accessible memory
[    7.459956] [drm] radeon: VRAM 256M
[    7.459958] [drm] radeon: VRAM from 0x00000000 to 0x0FFFFFFF
[    7.459960] [drm] radeon: GTT 512M
[    7.459962] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[    7.460120] radeon 0000:01:00.0: irq 29 for MSI/MSI-X
[    7.460136] [drm] radeon: using MSI.
[    7.460194] [drm] radeon: irq initialized.
[    7.460879] [drm] Detected VRAM RAM=256M, BAR=256M
[    7.460883] [drm] RAM width 128bits DDR
[    7.460988] [TTM] Zone  kernel: Available graphics memory: 430274 kiB.
[    7.460990] [TTM] Zone highmem: Available graphics memory: 1547878 kiB.
[    7.461036] [drm] radeon: 256M of VRAM memory ready
[    7.461038] [drm] radeon: 512M of GTT memory ready.
[    7.461061] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    7.462564] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[    7.462614] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[    7.462635] [drm] radeon: cp idle (0x10000C03)
[    7.462685] [drm] Loading R500 Microcode
[    7.462780] platform radeon_cp.0: firmware: requesting radeon/R520_cp.bin
[    7.560969] [drm] radeon: ring at 0x0000000020000000
[    7.561022] [drm] ring test succeeded in 1 usecs
[    7.561204] [drm] radeon: ib pool ready.
[    7.561299] [drm] ib test succeeded in 0 usecs
[    7.561491] [drm] Radeon Display Connectors
[    7.561494] [drm] Connector 0:
[    7.561496] [drm]   VGA
[    7.561498] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    7.561500] [drm]   Encoders:
[    7.561502] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    7.561504] [drm] Connector 1:
[    7.561506] [drm]   LVDS
[    7.561508] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[    7.561510] [drm]   Encoders:
[    7.561512] [drm]     LCD1: INTERNAL_LVTM1
[    7.561513] [drm] Connector 2:
[    7.561515] [drm]   DVI-I
[    7.561516] [drm]   HPD1
[    7.561519] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    7.561521] [drm]   Encoders:
[    7.561522] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[    7.742300] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    7.742304] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[    7.742418] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.742432] iwl3945 0000:03:00.0: setting latency timer to 64
[    7.812059] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    7.812064] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    7.812178]   alloc irq_desc for 30 on node -1
[    7.812181]   alloc kstat_irqs on node -1
[    7.812214] iwl3945 0000:03:00.0: irq 30 for MSI/MSI-X
[    7.988177] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[    7.991279] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[    7.996383] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    7.997466] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    7.998751] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    8.010014] [drm] fb mappable at 0xD00C0000
[    8.010017] [drm] vram apper at 0xD0000000
[    8.010019] [drm] size 7680000
[    8.010021] [drm] fb depth is 24
[    8.010022] [drm]    pitch is 6400
[    8.010161] fb0: radeondrmfb frame buffer device
[    8.010163] registered panic notifier
[    8.010169] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[    8.222747] vga16fb: initializing
[    8.222752] vga16fb: mapped to 0xc00a0000
[    8.222755] vga16fb: not registering due to another framebuffer present
[    8.560351] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[    8.560354] thinkpad_acpi: http://ibm-acpi.sf.net/
[    8.560356] thinkpad_acpi: ThinkPad BIOS 79ETE3WW (2.23 ), EC 79HT50WW-1.07
[    8.560359] thinkpad_acpi: Lenovo ThinkPad T60p, model 200793U
[    8.560925] thinkpad_acpi: radio switch found; radios are enabled
[    8.561025] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[    8.561028] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[    8.566094] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    8.567000] Registered led device: tpacpi::thinklight
[    8.567035] Registered led device: tpacpi::power
[    8.567052] Registered led device: tpacpi::standby
[    8.567068] Registered led device: tpacpi::thinkvantage
[    8.567627] phy0: Selected rate control algorithm 'iwl-3945-rs'
[    8.571016] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[    8.571237] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[    8.574083] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[    8.715838] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    8.715842] hda_intel: probe_mask set to 0x1 for device 17aa:2010
[    8.716016] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.749077] Console: switching to colour frame buffer device 200x75
[    8.923498] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[    9.948237] psmouse serio2: ID: 10 00 64
[   10.054973] type=1505 audit(1301088794.044:5):  operation="profile_replace" pid=846 name="/sbin/dhclient3"
[   10.055596] type=1505 audit(1301088794.044:6):  operation="profile_replace" pid=846 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.055942] type=1505 audit(1301088794.044:7):  operation="profile_replace" pid=846 name="/usr/lib/connman/scripts/dhclient-script"
[   10.419097] type=1505 audit(1301088794.408:8):  operation="profile_load" pid=847 name="/usr/bin/evince"
[   10.426910] type=1505 audit(1301088794.416:9):  operation="profile_load" pid=847 name="/usr/bin/evince-previewer"
[   10.431758] type=1505 audit(1301088794.420:10):  operation="profile_load" pid=847 name="/usr/bin/evince-thumbnailer"
[   10.923837] type=1505 audit(1301088794.912:11):  operation="profile_load" pid=845 name="/usr/share/gdm/guest-session/Xsession"
[   10.985213] type=1505 audit(1301088794.976:12):  operation="profile_load" pid=853 name="/usr/bin/freshclam"
[   10.996375] type=1505 audit(1301088794.988:13):  operation="profile_load" pid=854 name="/usr/lib/cups/backend/cups-pdf"
[   10.997136] type=1505 audit(1301088794.988:14):  operation="profile_load" pid=854 name="/usr/sbin/cupsd"
[   12.244607] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   12.291954] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   12.361656] Registered led device: iwl-phy0::radio
[   12.361677] Registered led device: iwl-phy0::assoc
[   12.361731] Registered led device: iwl-phy0::RX
[   12.361747] Registered led device: iwl-phy0::TX
[   12.373117] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.517388] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   13.750109] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   17.052388] Bluetooth: L2CAP ver 2.14
[   17.052391] Bluetooth: L2CAP socket layer initialized
[   17.105396] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.105400] Bluetooth: BNEP filters: protocol multicast
[   17.146482] ppdev: user-space parallel port driver
[   17.159305] Bridge firewalling registered
[   17.460246] Bluetooth: SCO (Voice Link) ver 0.6
[   17.460249] Bluetooth: SCO socket layer initialized
[   17.954257] Bluetooth: RFCOMM TTY layer initialized
[   17.954263] Bluetooth: RFCOMM socket layer initialized
[   17.954265] Bluetooth: RFCOMM ver 1.11
[  354.764300] wlan0: deauthenticating from 00:0c:41:a3:f8:e3 by local choice (reason=3)
[  354.765367] wlan0: direct probe to AP 00:0c:41:a3:f8:e3 (try 1)
[  354.774159] wlan0: direct probe responded
[  354.774167] wlan0: authenticate with AP 00:0c:41:a3:f8:e3 (try 1)
[  354.776132] wlan0: authenticated
[  354.776204] wlan0: associate with AP 00:0c:41:a3:f8:e3 (try 1)
[  354.778307] wlan0: RX AssocResp from 00:0c:41:a3:f8:e3 (capab=0x411 status=0 aid=5)
[  354.778313] wlan0: associated
[  354.780612] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  365.688018] wlan0: no IPv6 routers present
[  573.024062] CE: hpet increasing min_delta_ns to 15000 nsec
[  573.024136] CE: hpet increasing min_delta_ns to 22500 nsec
[  573.024213] CE: hpet increasing min_delta_ns to 33750 nsec
[  947.079579] e1000: Unknown parameter `eeprom_bad_csum_allow'


```

---

### Post by i20234 on 2011-03-25
and of "dmesg /var/log/syslog"

```

[    0.269479] pci_bus 0000:03: resource 1 mem: [0xec000000-0xedffffff]
[    0.269482] pci_bus 0000:03: resource 2 pref mem [0xe4000000-0xe40fffff]
[    0.269485] pci_bus 0000:04: resource 0 io:  [0x6000-0x7fff]
[    0.269488] pci_bus 0000:04: resource 1 mem: [0xe8000000-0xe9ffffff]
[    0.269490] pci_bus 0000:04: resource 2 pref mem [0xe4100000-0xe41fffff]
[    0.269493] pci_bus 0000:0c: resource 0 io:  [0x8000-0x9fff]
[    0.269496] pci_bus 0000:0c: resource 1 mem: [0xea000000-0xebffffff]
[    0.269499] pci_bus 0000:0c: resource 2 pref mem [0xe4200000-0xe42fffff]
[    0.269501] pci_bus 0000:15: resource 0 io:  [0xa000-0xdfff]
[    0.269504] pci_bus 0000:15: resource 1 mem: [0xe4300000-0xe7ffffff]
[    0.269507] pci_bus 0000:15: resource 2 pref mem [0xe0000000-0xe3ffffff]
[    0.269509] pci_bus 0000:15: resource 3 io:  [0x00-0xffff]
[    0.269512] pci_bus 0000:15: resource 4 mem: [0x000000-0xffffffff]
[    0.269515] pci_bus 0000:16: resource 0 io:  [0xa000-0xa0ff]
[    0.269517] pci_bus 0000:16: resource 1 io:  [0xa400-0xa4ff]
[    0.269520] pci_bus 0000:16: resource 2 pref mem [0xe0000000-0xe3ffffff]
[    0.269523] pci_bus 0000:16: resource 3 mem: [0xc4000000-0xc7ffffff]
[    0.269564] NET: Registered protocol family 2
[    0.269668] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.269988] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.270599] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.270918] TCP: Hash tables configured (established 131072 bind 65536)
[    0.270921] TCP reno registered
[    0.271029] NET: Registered protocol family 1
[    0.271162] pci 0000:01:00.0: Boot video device
[    0.271198] Simple Boot Flag at 0x35 set to 0x1
[    0.271385] cpufreq-nforce2: No nForce2 chipset.
[    0.271422] Scanning for low memory corruption every 60 seconds
[    0.271557] audit: initializing netlink socket (disabled)
[    0.271568] type=2000 audit(1301088784.268:1): initialized
[    0.281366] highmem bounce pool size: 64 pages
[    0.281372] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.282987] VFS: Disk quotas dquot_6.5.2
[    0.283049] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.283649] fuse init (API version 7.13)
[    0.283739] msgmni has been set to 1664
[    0.283960] alg: No test for stdrng (krng)
[    0.284040] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.284043] io scheduler noop registered
[    0.284045] io scheduler anticipatory registered
[    0.284047] io scheduler deadline registered
[    0.284091] io scheduler cfq registered (default)
[    0.284232]   alloc irq_desc for 24 on node -1
[    0.284234]   alloc kstat_irqs on node -1
[    0.284243] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.284250] pcieport 0000:00:01.0: setting latency timer to 64
[    0.284371]   alloc irq_desc for 25 on node -1
[    0.284373]   alloc kstat_irqs on node -1
[    0.284382] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.284393] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.284546]   alloc irq_desc for 26 on node -1
[    0.284548]   alloc kstat_irqs on node -1
[    0.284556] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.284567] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.284718]   alloc irq_desc for 27 on node -1
[    0.284720]   alloc kstat_irqs on node -1
[    0.284728] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.284739] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.284893]   alloc irq_desc for 28 on node -1
[    0.284895]   alloc kstat_irqs on node -1
[    0.284903] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.284914] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.285016] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.285584] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 27d0 ss_vid 0 ss_did 0
[    0.285633] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.285655] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 27d2 ss_vid 0 ss_did 0
[    0.285693] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded
[    0.285714] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 27d4 ss_vid 0 ss_did 0
[    0.285751] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
[    0.285772] pciehp 0000:00:1c.3:pcie04: HPC vendor_id 8086 device_id 27d6 ss_vid 0 ss_did 0
[    0.285816] pciehp 0000:00:1c.3:pcie04: service driver pciehp loaded
[    0.285824] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.286042] ACPI: AC Adapter [AC] (on-line)
[    0.286115] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.286284] ACPI: Lid Switch [LID]
[    0.286333] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.286339] ACPI: Sleep Button [SLPB]
[    0.286396] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.286398] ACPI: Power Button [PWRF]
[    0.287079] ACPI: SSDT bfef1d36 00282 (v01  PmRef  Cpu0Ist 00000100 INTL 20050513)
[    0.287786] ACPI: SSDT bfef203d 0065A (v01  PmRef  Cpu0Cst 00000100 INTL 20050513)
[    0.290750] processor LNXCPU:00: registered as cooling_device0
[    0.291126] ACPI: SSDT bfef1c6e 000C8 (v01  PmRef  Cpu1Ist 00000100 INTL 20050513)
[    0.291627] ACPI: SSDT bfef1fb8 00085 (v01  PmRef  Cpu1Cst 00000100 INTL 20050513)
[    0.293118] processor LNXCPU:01: registered as cooling_device1
[    0.298149] thermal LNXTHERM:01: registered as thermal_zone0
[    0.298158] ACPI: Thermal Zone [THM0] (72 C)
[    0.299526] thermal LNXTHERM:02: registered as thermal_zone1
[    0.299534] ACPI: Thermal Zone [THM1] (77 C)
[    0.301070] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.302468] brd: module loaded
[    0.302945] loop: module loaded
[    0.303039] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.303147] ata_piix 0000:00:1f.2: version 2.13
[    0.303167] ata_piix 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.303173] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.305631] isapnp: Scanning for PnP cards...
[    0.386427] Freeing initrd memory: 7780k freed
[    0.414613] ACPI: Battery Slot [BAT0] (battery present)
[    0.457031] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.461056] scsi0 : ata_piix
[    0.461167] scsi1 : ata_piix
[    0.462103] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    0.462106] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    0.462476] Fixed MDIO Bus: probed
[    0.462513] PPP generic driver version 2.4.2
[    0.462590] tun: Universal TUN/TAP device driver, 1.6
[    0.462592] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.462691] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.471924] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.472160] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.472171]   alloc irq_desc for 19 on node -1
[    0.472173]   alloc kstat_irqs on node -1
[    0.472180] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.472197] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.472202] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.472236] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.472259] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.472272] ehci_hcd 0000:00:1d.7: debug port 1
[    0.476147] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.476163] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xee404000
[    0.493015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.493104] usb usb1: configuration #1 chosen from 1 choice
[    0.493137] hub 1-0:1.0: USB hub found
[    0.493146] hub 1-0:1.0: 8 ports detected
[    0.493216] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.493230] uhci_hcd: USB Universal Host Controller Interface driver
[    0.493459] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.493626] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.493631] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.493639] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.493642] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.493675] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.493710] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[    0.493804] usb usb2: configuration #1 chosen from 1 choice
[    0.493830] hub 2-0:1.0: USB hub found
[    0.493837] hub 2-0:1.0: 2 ports detected
[    0.493883]   alloc irq_desc for 17 on node -1
[    0.493886]   alloc kstat_irqs on node -1
[    0.493890] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.493896] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.493900] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.493934] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.493968] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
[    0.494061] usb usb3: configuration #1 chosen from 1 choice
[    0.494086] hub 3-0:1.0: USB hub found
[    0.494093] hub 3-0:1.0: 2 ports detected
[    0.494312] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    0.494479] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    0.494485]   alloc irq_desc for 18 on node -1
[    0.494486]   alloc kstat_irqs on node -1
[    0.494491] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.494497] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.494500] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.494532] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.494570] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    0.494667] usb usb4: configuration #1 chosen from 1 choice
[    0.494693] hub 4-0:1.0: USB hub found
[    0.494701] hub 4-0:1.0: 2 ports detected
[    0.494748] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.494754] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.494758] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.494798] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.494825] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
[    0.494914] usb usb5: configuration #1 chosen from 1 choice
[    0.494940] hub 5-0:1.0: USB hub found
[    0.494946] hub 5-0:1.0: 2 ports detected
[    0.495045] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.503430] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.503437] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.503516] mice: PS/2 mouse device common for all mice
[    0.503638] rtc_cmos 00:07: RTC can wake from S4
[    0.503678] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.503710] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.503820] device-mapper: uevent: version 1.0.3
[    0.503923] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.503987] device-mapper: multipath: version 1.1.0 loaded
[    0.503990] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.504108] EISA: Probing bus 0 at eisa.0
[    0.504115] Cannot allocate resource for EISA slot 1
[    0.504118] Cannot allocate resource for EISA slot 2
[    0.504120] Cannot allocate resource for EISA slot 3
[    0.504122] Cannot allocate resource for EISA slot 4
[    0.504124] Cannot allocate resource for EISA slot 5
[    0.504127] Cannot allocate resource for EISA slot 6
[    0.504129] Cannot allocate resource for EISA slot 7
[    0.504131] Cannot allocate resource for EISA slot 8
[    0.504133] EISA: Detected 0 cards.
[    0.504281] cpuidle: using governor ladder
[    0.504402] cpuidle: using governor menu
[    0.504846] TCP cubic registered
[    0.505024] NET: Registered protocol family 10
[    0.505479] lo: Disabled Privacy Extensions
[    0.505803] NET: Registered protocol family 17
[    0.506481] Using IPI No-Shortcut mode
[    0.506557] PM: Resume from disk failed.
[    0.506570] registered taskstats version 1
[    0.507108]   Magic number: 3:119:602
[    0.507209] rtc_cmos 00:07: setting system clock to 2011-03-25 21:33:04 UTC (1301088784)
[    0.507212] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.507214] EDD information not available.
[    0.511433] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.637527] ata2.00: ATAPI: MATSHITADVD-RAM UJ-842, RB01, max UDMA/33
[    0.653437] ata2.00: configured for UDMA/33
[    0.670449] isapnp: No Plug & Play device found
[    0.676346] ata1.00: HPA unlocked: 195369455 -> 195371568, native 195371568
[    0.676351] ata1.00: ATA-7: HTS721010G9SA00, MCZIC10H, max UDMA/100
[    0.676354] ata1.00: 195371568 sectors, multi 16: LBA48 
[    0.692642] ata1.00: configured for UDMA/100
[    0.692780] scsi 0:0:0:0: Direct-Access     ATA      HTS721010G9SA00  MCZI PQ: 0 ANSI: 5
[    0.692907] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.692919] sd 0:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    0.692969] sd 0:0:0:0: [sda] Write Protect is off
[    0.692972] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.693050] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.693191]  sda:
[    0.694927] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-842   RB01 PQ: 0 ANSI: 5
[    0.699478] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.699481] Uniform CD-ROM driver Revision: 3.20
[    0.699563] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.699604] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.711316]  sda1 sda2 < sda5 >
[    0.730216] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.730250] Freeing unused kernel memory: 660k freed
[    0.730655] Write protecting the kernel text: 4680k
[    0.730710] Write protecting the kernel read-only data: 1844k
[    0.745930] udev: starting version 151
[    0.850205] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.850209] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.850263] e1000e 0000:02:00.0: Disabling L1 ASPM
[    0.850286] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.850328] e1000e 0000:02:00.0: setting latency timer to 64
[    0.850504]   alloc irq_desc for 29 on node -1
[    0.850507]   alloc kstat_irqs on node -1
[    0.850527] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[    0.918632] 0000:02:00.0: 0000:02:00.0: The NVM Checksum Is Not Valid
[    0.928945] e1000e 0000:02:00.0: PCI INT A disabled
[    0.928956] e1000e: probe of 0000:02:00.0 failed with error -5
[    1.160462] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.192058] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.357997] usb 5-1: configuration #1 chosen from 1 choice
[    1.600048] usb 5-2: new full speed USB device using uhci_hcd and address 3
[    1.772973] usb 5-2: configuration #1 chosen from 1 choice
[    3.403828] Adding 4016120k swap on /dev/sda5.  Priority:-1 extents:1 across:4016120k 
[    3.874571] udev: starting version 151
[    5.040040] lp: driver loaded but no devices found
[    5.088320] acpi device:05: registered as cooling_device2
[    5.089435] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:04/LNXVIDEO:01/input/input5
[    5.089559] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    5.141858] type=1505 audit(1301088789.132:2):  operation="profile_load" pid=517 name="/sbin/dhclient3"
[    5.142664] type=1505 audit(1301088789.132:3):  operation="profile_load" pid=517 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    5.143002] type=1505 audit(1301088789.132:4):  operation="profile_load" pid=517 name="/usr/lib/connman/scripts/dhclient-script"
[    5.296268] Bluetooth: Core ver 2.15
[    5.296718] NET: Registered protocol family 31
[    5.296720] Bluetooth: HCI device and connection manager initialized
[    5.296723] Bluetooth: HCI socket layer initialized
[    5.353523] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    5.353848] usbcore: registered new interface driver btusb
[    5.395968] irda_init()
[    5.395981] NET: Registered protocol family 23
[    5.472765] nsc-ircc 00:0a: activated
[    5.472769] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[    5.472810] nsc-ircc, chip->init
[    5.472824] nsc-ircc, Found chip at base=0x164e
[    5.472865] nsc-ircc, driver loaded (Dag Brattli)
[    5.473609] IrDA: Registered device irda0
[    5.473611] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[    5.491211] Non-volatile memory driver v1.3
[    5.643761] cfg80211: Calling CRDA to update world regulatory domain
[    6.061051] intel_rng: FWH not detected
[    6.076665] Linux agpgart interface v0.103
[    6.083510] tpm_tis 00:0b: 1.2 TPM (device-id 0x3202, rev-id 5)
[    6.160589] [drm] Initialized drm 1.1.0 20060810
[    6.301141] cfg80211: World regulatory domain updated:
[    6.301145]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.301148]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.301151]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.301154]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.301156]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.301159]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.659211] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:2012]
[    6.659240] yenta_cardbus 0000:15:00.0: Using INTVAL to route CSC interrupts to PCI
[    6.659242] yenta_cardbus 0000:15:00.0: Routing CardBus interrupts to PCI
[    6.659249] yenta_cardbus 0000:15:00.0: TI: mfunc 0x01d01002, devctl 0x64
[    6.889820] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cf0, PCI irq 16
[    6.889826] yenta_cardbus 0000:15:00.0: Socket status: 30000007
[    6.889833] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xdfff
[    6.889838] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xdfff: clean.
[    6.890731] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
[    6.890734] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
[    7.283944] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04793/0x300000
[    7.283965] serio: Synaptics pass-through port at isa0060/serio1/input0
[    7.327838] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    7.457392] [drm] radeon defaulting to kernel modesetting.
[    7.457396] [drm] radeon kernel modesetting enabled.
[    7.457507] radeon 0000:01:00.0: power state changed by ACPI to D0
[    7.457550] radeon 0000:01:00.0: power state changed by ACPI to D0
[    7.457566] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.457585] radeon 0000:01:00.0: setting latency timer to 64
[    7.459435] [drm] radeon: Initializing kernel modesetting.
[    7.459543] [drm] register mmio base: 0xEE100000
[    7.459545] [drm] register mmio size: 65536
[    7.459662] ATOM BIOS: Lenovo
[    7.459904] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[    7.459953] [drm] Generation 2 PCI interface, using max accessible memory
[    7.459956] [drm] radeon: VRAM 256M
[    7.459958] [drm] radeon: VRAM from 0x00000000 to 0x0FFFFFFF
[    7.459960] [drm] radeon: GTT 512M
[    7.459962] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[    7.460120] radeon 0000:01:00.0: irq 29 for MSI/MSI-X
[    7.460136] [drm] radeon: using MSI.
[    7.460194] [drm] radeon: irq initialized.
[    7.460879] [drm] Detected VRAM RAM=256M, BAR=256M
[    7.460883] [drm] RAM width 128bits DDR
[    7.460988] [TTM] Zone  kernel: Available graphics memory: 430274 kiB.
[    7.460990] [TTM] Zone highmem: Available graphics memory: 1547878 kiB.
[    7.461036] [drm] radeon: 256M of VRAM memory ready
[    7.461038] [drm] radeon: 512M of GTT memory ready.
[    7.461061] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    7.462564] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[    7.462614] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[    7.462635] [drm] radeon: cp idle (0x10000C03)
[    7.462685] [drm] Loading R500 Microcode
[    7.462780] platform radeon_cp.0: firmware: requesting radeon/R520_cp.bin
[    7.560969] [drm] radeon: ring at 0x0000000020000000
[    7.561022] [drm] ring test succeeded in 1 usecs
[    7.561204] [drm] radeon: ib pool ready.
[    7.561299] [drm] ib test succeeded in 0 usecs
[    7.561491] [drm] Radeon Display Connectors
[    7.561494] [drm] Connector 0:
[    7.561496] [drm]   VGA
[    7.561498] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    7.561500] [drm]   Encoders:
[    7.561502] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    7.561504] [drm] Connector 1:
[    7.561506] [drm]   LVDS
[    7.561508] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[    7.561510] [drm]   Encoders:
[    7.561512] [drm]     LCD1: INTERNAL_LVTM1
[    7.561513] [drm] Connector 2:
[    7.561515] [drm]   DVI-I
[    7.561516] [drm]   HPD1
[    7.561519] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    7.561521] [drm]   Encoders:
[    7.561522] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[    7.742300] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    7.742304] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[    7.742418] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.742432] iwl3945 0000:03:00.0: setting latency timer to 64
[    7.812059] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    7.812064] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    7.812178]   alloc irq_desc for 30 on node -1
[    7.812181]   alloc kstat_irqs on node -1
[    7.812214] iwl3945 0000:03:00.0: irq 30 for MSI/MSI-X
[    7.988177] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[    7.991279] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[    7.996383] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    7.997466] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    7.998751] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    8.010014] [drm] fb mappable at 0xD00C0000
[    8.010017] [drm] vram apper at 0xD0000000
[    8.010019] [drm] size 7680000
[    8.010021] [drm] fb depth is 24
[    8.010022] [drm]    pitch is 6400
[    8.010161] fb0: radeondrmfb frame buffer device
[    8.010163] registered panic notifier
[    8.010169] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[    8.222747] vga16fb: initializing
[    8.222752] vga16fb: mapped to 0xc00a0000
[    8.222755] vga16fb: not registering due to another framebuffer present
[    8.560351] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[    8.560354] thinkpad_acpi: http://ibm-acpi.sf.net/
[    8.560356] thinkpad_acpi: ThinkPad BIOS 79ETE3WW (2.23 ), EC 79HT50WW-1.07
[    8.560359] thinkpad_acpi: Lenovo ThinkPad T60p, model 200793U
[    8.560925] thinkpad_acpi: radio switch found; radios are enabled
[    8.561025] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[    8.561028] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[    8.566094] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    8.567000] Registered led device: tpacpi::thinklight
[    8.567035] Registered led device: tpacpi::power
[    8.567052] Registered led device: tpacpi::standby
[    8.567068] Registered led device: tpacpi::thinkvantage
[    8.567627] phy0: Selected rate control algorithm 'iwl-3945-rs'
[    8.571016] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[    8.571237] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[    8.574083] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[    8.715838] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    8.715842] hda_intel: probe_mask set to 0x1 for device 17aa:2010
[    8.716016] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.749077] Console: switching to colour frame buffer device 200x75
[    8.923498] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[    9.948237] psmouse serio2: ID: 10 00 64
[   10.054973] type=1505 audit(1301088794.044:5):  operation="profile_replace" pid=846 name="/sbin/dhclient3"
[   10.055596] type=1505 audit(1301088794.044:6):  operation="profile_replace" pid=846 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.055942] type=1505 audit(1301088794.044:7):  operation="profile_replace" pid=846 name="/usr/lib/connman/scripts/dhclient-script"
[   10.419097] type=1505 audit(1301088794.408:8):  operation="profile_load" pid=847 name="/usr/bin/evince"
[   10.426910] type=1505 audit(1301088794.416:9):  operation="profile_load" pid=847 name="/usr/bin/evince-previewer"
[   10.431758] type=1505 audit(1301088794.420:10):  operation="profile_load" pid=847 name="/usr/bin/evince-thumbnailer"
[   10.923837] type=1505 audit(1301088794.912:11):  operation="profile_load" pid=845 name="/usr/share/gdm/guest-session/Xsession"
[   10.985213] type=1505 audit(1301088794.976:12):  operation="profile_load" pid=853 name="/usr/bin/freshclam"
[   10.996375] type=1505 audit(1301088794.988:13):  operation="profile_load" pid=854 name="/usr/lib/cups/backend/cups-pdf"
[   10.997136] type=1505 audit(1301088794.988:14):  operation="profile_load" pid=854 name="/usr/sbin/cupsd"
[   12.244607] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   12.291954] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   12.361656] Registered led device: iwl-phy0::radio
[   12.361677] Registered led device: iwl-phy0::assoc
[   12.361731] Registered led device: iwl-phy0::RX
[   12.361747] Registered led device: iwl-phy0::TX
[   12.373117] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.517388] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   13.750109] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   17.052388] Bluetooth: L2CAP ver 2.14
[   17.052391] Bluetooth: L2CAP socket layer initialized
[   17.105396] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.105400] Bluetooth: BNEP filters: protocol multicast
[   17.146482] ppdev: user-space parallel port driver
[   17.159305] Bridge firewalling registered
[   17.460246] Bluetooth: SCO (Voice Link) ver 0.6
[   17.460249] Bluetooth: SCO socket layer initialized
[   17.954257] Bluetooth: RFCOMM TTY layer initialized
[   17.954263] Bluetooth: RFCOMM socket layer initialized
[   17.954265] Bluetooth: RFCOMM ver 1.11
[  354.764300] wlan0: deauthenticating from 00:0c:41:a3:f8:e3 by local choice (reason=3)
[  354.765367] wlan0: direct probe to AP 00:0c:41:a3:f8:e3 (try 1)
[  354.774159] wlan0: direct probe responded
[  354.774167] wlan0: authenticate with AP 00:0c:41:a3:f8:e3 (try 1)
[  354.776132] wlan0: authenticated
[  354.776204] wlan0: associate with AP 00:0c:41:a3:f8:e3 (try 1)
[  354.778307] wlan0: RX AssocResp from 00:0c:41:a3:f8:e3 (capab=0x411 status=0 aid=5)
[  354.778313] wlan0: associated
[  354.780612] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  365.688018] wlan0: no IPv6 routers present
[  573.024062] CE: hpet increasing min_delta_ns to 15000 nsec
[  573.024136] CE: hpet increasing min_delta_ns to 22500 nsec
[  573.024213] CE: hpet increasing min_delta_ns to 33750 nsec
[  947.079579] e1000: Unknown parameter `eeprom_bad_csum_allow'


```

---

### Post by i20234 on 2011-03-26
bump

looks exactly like my problem, but the swiss forums deleted the instructions? :/
[http://ubuntuforums.org/showthread.php?p=10603796#post10603796](http://ubuntuforums.org/showthread.php?p=10603796#post10603796)

---

