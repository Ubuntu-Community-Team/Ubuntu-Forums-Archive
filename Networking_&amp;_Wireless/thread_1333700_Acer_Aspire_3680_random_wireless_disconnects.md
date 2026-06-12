---
title: "Acer Aspire 3680 random wireless disconnects"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by N00bDud3 on 2009-11-21
Hi, I'm relatively new to these forums.
On my Acer laptop I have an Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
Both randomly and when I adjust the brightness settings with the Fn keys, the wireless will drop out. In the logs I get a message like
```
NetworkManager: <info> Wireless now disabled by radio killswitch
```
I understand it when it disconnects when I am idle, but when it's being used it shouldn't go down. I don't even know why adjusting the brightness does anything. Any suggestions?

EDIT:
I may have fixed it by looking through the forums. I blacklisted the acer-wmi drivers, and now my connection strength is better, and adjusting the brightness doesn't send a killswitch trigger to the wireless.

---

### Post by N00bDud3 on 2009-11-22
The fix I found does keep the brightness changing from disabling the wireless card, but it also keeps everything else from disabling it too. It also doesn't show the bar with the current brightness setting when the brightness is changed. Is there any way that both problems can be fixed?

---

### Post by coffeecat on 2009-11-22
I have no fix for you, but a couple of comments.

The AR5001 wireless chipset in my Asus netbook gives me a stable wireless connection in Karmic, so I don't know why you were getting random disconnects when you weren't adjusting the brightness.

With regard to the acer_wmi module, I found this:

[http://www.mjmwired.net/kernel/Documentation/laptops/acer-wmi.txt](http://www.mjmwired.net/kernel/Documentation/laptops/acer-wmi.txt)

It's interesting (and depressing) that this driver has been developed without any input from Acer. Anyway, you seem to have uncovered a bug and I should imagine that the lead developer would be interested in what you have found. His email address is in that link.

Or you may wish to file a bug at [launchpad]("https://bugs.launchpad.net/ubuntu/"). Or do both.

Good luck!

---

### Post by N00bDud3 on 2009-11-22
Thanks for your comment. I will have to report this bug. I think the random disconnects were when the screen dimmed from being idle, so it all still relates to the brightness settings.

---

### Post by coffeecat on 2009-11-22
I'm actually posting from an Acer Aspire 7540 laptop which has a different Atheros wireless chipset, but I haven't had your problem. Changing the brightness with the Fn key and arrow keys doesn't disconnect the wireless - so clearly a model-specific thing.

I've set up both Karmic and Fedora 12 in different partitions on this machine. (Posting from Fedora atm). Both Fedora12 and Karmic have the 2.6.31 kernel, so you'd expect that acer_wmi would be the same in both. But - and I hate to say this :) - the Fn key combinations work better in Fedora. In Karmic, when I adjust the brightness, the level jumps two notches for each key press, but in Fedora it works just fine.

---

### Post by N00bDud3 on 2009-11-22
Hmm... Very strange... I'm only using Ubuntu because the laptop previously had Vista (not that it's horrible, I can just do more w/ Linux/XP than in Vista) and Ubuntu is the only distro I've used before. I might have to try some others in the future.

EDIT:
Aren't Fedora updates/modules able to run on any distro? Maybe we could try to compile the Fedora version of acer-wmi for Ubuntu?

---

### Post by N00bDud3 on 2009-11-22
What is with acer-wmi being this messed up? Any time that I adjust a setting that uses it at all, I lose wireless connection. Every time it will trigger the radio killswitch for no reason. Is there any way to fix this other than blacklisting it? Because I like using it so the brightness can be auto-dimmed when idle.

---

### Post by coffeecat on 2009-11-23
> **N00bDud3 said:**
> EDIT:
Aren't Fedora updates/modules able to run on any distro? Maybe we could try to compile the Fedora version of acer-wmi for Ubuntu?

Fedora packages are in the rpm format. Even if you converted them with alien, they might not be compatible with the Ubuntu kernel. Even though the Fedora and Ubuntu devs have used the same kernel version number, they will have patched them differently. Having said that though, I doubt whether the source code for acer_wmi in the two distros was any different. The difference I've experienced may be down to something else in the system.

> **N00bDud3 said:**
> What is with acer-wmi being this messed up? Any time that I adjust a setting that uses it at all, I lose wireless connection. Every time it will trigger the radio killswitch for no reason. Is there any way to fix this other than blacklisting it? Because I like using it so the brightness can be auto-dimmed when idle.

Sorry - I have no further ideas, but the dev for acer_wmi may have. If you look under "Supported Hardware" in the link I gave, you'll see a further link. In that one your laptop is listed as supported whereas mine is not. But it's you that's got a near showstopper bug, not me. So I'm sure he would like the dsdt for both machines. I'm going to send him mine. Why not send him your DSDT with a request for help? I'm sure he would appreciate getting the DSDT. The only way he can improve the driver is by information from the community since he is getting zero help from Acer.

Anyway, I've bumped your thread by posting, so hopefully other Acer laptop owners may see this and have something else to offer.

---

### Post by N00bDud3 on 2009-11-23
Thanks for the reply and the info. I sent him my dsdt, and I am also updating this post because the problem has changed somewhat. Now when I change the brightness instead of seeing a radio killswitch message in the logs, I see
```
kernel: [  510.030759] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```
This is just becoming frustrating. I will blacklist the acer-wmi again until I get an email back, or if I find something useful.

---

### Post by virtualsamurai on 2009-12-04
How did you blacklist the acer-wmi drivers? I have the same laptop, and am experiencing a similar issue. I notice constant disconnects, but I haven't noticed the correlation between the screen dimming. 
 
I thought i would give your solution a shot, but am uncertain of the steps you took.

---

### Post by coffeecat on 2009-12-04
I don't know how the OP did it - perhaps they will post in due course - but if I wanted to blacklist a driver, I would edit /etc/modprobe.d/blacklist.conf and add the line...

> blacklist *name_of_module*By the way, do 'lsmod' and check the form of the acer_wmi module. I'm fairly sure it's acer_wmi, not acer-wmi, but I'm not using my Acer laptop atm so I can't check this myself.

---

### Post by flavanoid on 2009-12-22
Exact same issue here.  Acer Aspire 3680-2682.  I've always had issues with this wifi card becasue it seems there have been a lot of discrepancies with identifying what model the card actually is and for the longest time (before I started suing Ubuntu) I used ndiswrapper to get it up and running.  Now I'm using Karmic and the included acer drivers.  Anywho, heres some info:

lspci:
```

03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

Some dmesg love:
```

[89979.041629] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[89990.453428] wlan0: authenticate with AP 00:1c:10:49:b5:43
[89990.454964] wlan0: authenticated
[89990.454970] wlan0: associate with AP 00:1c:10:49:b5:43
[89990.457321] wlan0: RX AssocResp from 00:1c:10:49:b5:43 (capab=0x411 status=0 aid=1)
[89990.457327] wlan0: associated
[89990.458371] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[90001.196043] wlan0: no IPv6 routers present
[90126.229285] wlan0: deauthenticating by local choice (reason=3)
[90126.299367] wlan0: disassociating by local choice (reason=3)
[90128.097695] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[90129.013162] wlan0: deauthenticating by local choice (reason=3)
[90130.057533] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[90135.086820] wlan0: direct probe to AP 00:1c:10:49:b5:43 try 1
[90135.088976] wlan0 direct probe responded
[90135.088983] wlan0: authenticate with AP 00:1c:10:49:b5:43
[90135.090463] wlan0: authenticated
[90135.090469] wlan0: associate with AP 00:1c:10:49:b5:43
[90135.092782] wlan0: RX AssocResp from 00:1c:10:49:b5:43 (capab=0x411 status=0 aid=1)
[90135.092788] wlan0: associated
[90135.095556] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[90146.076121] wlan0: no IPv6 routers present

```

mesages:
```

tail  /var/log/messages
Dec 22 19:33:36 kernel: [89545.460103] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 22 19:35:13 kernel: [89643.040614] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 22 19:35:25 kernel: [89654.497993] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 22 19:36:46 kernel: [89736.049519] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 22 19:36:58 kernel: [89747.470061] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 22 19:40:49 kernel: [89979.041629] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 22 19:41:01 kernel: [89990.458371] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 22 19:43:18 kernel: [90128.097695] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 22 19:43:20 kernel: [90130.057533] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 22 19:43:25 kernel: [90135.095556] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

### Post by cathectic on 2009-12-23
Having read through all of this, I'm not really convinced acer-wmi is at fault here.

acer-wmi is just a mechanism for toggling the rfkill switch - something has to tell acer-wmi to actually do that though, it doesn't do it of its' own accord (and it doesn't respond/ handle in anyway keyboard presses, or any other notification of the backlight changing).

What's more likely is either something in userspace is doing naughty things when the brightness changes (and anything brightness related would normally lead me to blame Gnome Power Manager...)

To test that, you can run the following from the command line:

```
echo 0 | sudo tee /sys/devices/platform/acer-wmi/backlight/acer-wmi/brightness
```

This will turn the brightness down to the minimum level. If that causes the radio to be killed, then acer-wmi is doing something odd. If it doesn't, then something else (probably in userspace) is at fault.

(And no more DSDT's for the Aspire 3680 please, three is more than enough :)

---

### Post by flavanoid on 2009-12-23
> **cathectic said:**
> 
```
echo 0 | sudo tee /sys/devices/platform/acer-wmi/backlight/acer-wmi/brightness
```

This will turn the brightness down to the minimum level. If that causes the radio to be killed, then acer-wmi is doing something odd. If it doesn't, then something else (probably in userspace) is at fault.

This command did kill the radio intermittently.  I've found that even using the brightness hotkeys isn't consistent in killing the radio, it only happens occasionally, but it does happen.  This is strange...  You're probably right Carlos, this may not point to acer-wmi being the problem but may indicate that it is not playing well with something else...

If there is anything further I can assist you with in sorting this out let me know.

I would also like to note that I've been using Ubuntu since 8.04.  9.04 was the first time my wireless card worked "out of the box" and 9.10 is the first time the activity LED worked as well.  The reason I state this is because I'm obviously seeing progress here but perhaps this "progress" caused something else to take a few steps back.  I had no disconnects in 9.04.

---

### Post by cathectic on 2009-12-27
> **flavanoid said:**
> This command did kill the radio intermittently.  I've found that even using the brightness hotkeys isn't consistent in killing the radio, it only happens occasionally, but it does happen.  This is strange...  You're probably right Carlos, this may not point to acer-wmi being the problem but may indicate that it is not playing well with something else...

If there is anything further I can assist you with in sorting this out let me know.

Posting the full dmesg when you trigger this may be of some help. You could also check using 'showkey' what keycodes the brightness keys emit (and check that it doesn't change when you see the strange rfkill behaviour).

Failing that, we'd need to start adding some more debugging to the kernel to try and figure out exactly what is going on.

Also, which wireless driver are you using? ndiswrapper or ath5k?

---

### Post by flavanoid on 2009-12-27
dmesg:

```
[    1.173956] pci 0000:0a:09.0: CardBus bridge, secondary bus 0000:0b
[    1.173959] pci 0000:0a:09.0:   IO window: 0x003000-0x0030ff
[    1.173966] pci 0000:0a:09.0:   IO window: 0x003400-0x0034ff
[    1.173972] pci 0000:0a:09.0:   PREFETCH window: 0x40000000-0x43ffffff
[    1.173979] pci 0000:0a:09.0:   MEM window: 0x48000000-0x4bffffff
[    1.173985] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    1.173990] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    1.173997] pci 0000:00:1e.0:   MEM window: 0xd0200000-0xd02fffff
[    1.174004] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x43ffffff
[    1.174017] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    1.174023]   alloc irq_desc for 16 on node -1
[    1.174026]   alloc kstat_irqs on node -1
[    1.174032] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.174040] pci 0000:00:1c.0: setting latency timer to 64
[    1.174050] pci 0000:00:1c.1: enabling device (0000 -> 0002)
[    1.174054]   alloc irq_desc for 17 on node -1
[    1.174056]   alloc kstat_irqs on node -1
[    1.174060] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.174068] pci 0000:00:1c.1: setting latency timer to 64
[    1.174077]   alloc irq_desc for 18 on node -1
[    1.174079]   alloc kstat_irqs on node -1
[    1.174083] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.174091] pci 0000:00:1c.2: setting latency timer to 64
[    1.174097] pci 0000:00:1e.0: enabling device (0004 -> 0007)
[    1.174104] pci 0000:00:1e.0: setting latency timer to 64
[    1.174114] pci 0000:0a:09.0: enabling device (0000 -> 0003)
[    1.174119]   alloc irq_desc for 20 on node -1
[    1.174121]   alloc kstat_irqs on node -1
[    1.174125] pci 0000:0a:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.174135] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.174138] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    1.174141] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    1.174144] pci_bus 0000:02: resource 1 mem: [0x44000000-0x440fffff]
[    1.174148] pci_bus 0000:02: resource 2 mem: [0x0-0xfffff]
[    1.174151] pci_bus 0000:03: resource 0 mem: [0x0-0xfff]
[    1.174153] pci_bus 0000:03: resource 1 mem: [0x44100000-0x441fffff]
[    1.174157] pci_bus 0000:03: resource 2 mem: [0x0-0xfffff]
[    1.174160] pci_bus 0000:04: resource 0 mem: [0x0-0xfff]
[    1.174163] pci_bus 0000:04: resource 1 mem: [0x0-0xfffff]
[    1.174165] pci_bus 0000:04: resource 2 mem: [0x0-0xfffff]
[    1.174168] pci_bus 0000:0a: resource 0 io:  [0x3000-0x3fff]
[    1.174171] pci_bus 0000:0a: resource 1 mem: [0xd0200000-0xd02fffff]
[    1.174174] pci_bus 0000:0a: resource 2 pref mem [0x40000000-0x43ffffff]
[    1.174178] pci_bus 0000:0a: resource 3 io:  [0x00-0xffff]
[    1.174180] pci_bus 0000:0a: resource 4 mem: [0x000000-0xffffffff]
[    1.174184] pci_bus 0000:0b: resource 0 io:  [0x3000-0x30ff]
[    1.174187] pci_bus 0000:0b: resource 1 io:  [0x3400-0x34ff]
[    1.174190] pci_bus 0000:0b: resource 2 pref mem [0x40000000-0x43ffffff]
[    1.174193] pci_bus 0000:0b: resource 3 mem: [0x48000000-0x4bffffff]
[    1.174233] NET: Registered protocol family 2
[    1.174347] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.174721] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.175310] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.175589] TCP: Hash tables configured (established 131072 bind 65536)
[    1.175592] TCP reno registered
[    1.175671] NET: Registered protocol family 1
[    1.175747] Trying to unpack rootfs image as initramfs...
[    1.408348] Freeing initrd memory: 7708k freed
[    1.412867] Simple Boot Flag at 0x36 set to 0x1
[    1.413105] cpufreq-nforce2: No nForce2 chipset.
[    1.413141] Scanning for low memory corruption every 60 seconds
[    1.413267] audit: initializing netlink socket (disabled)
[    1.413288] type=2000 audit(1261852560.412:1): initialized
[    1.423558] highmem bounce pool size: 64 pages
[    1.423564] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.425350] VFS: Disk quotas dquot_6.5.2
[    1.425427] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.426091] fuse init (API version 7.12)
[    1.426202] msgmni has been set to 1732
[    1.426474] alg: No test for stdrng (krng)
[    1.426493] io scheduler noop registered
[    1.426496] io scheduler anticipatory registered
[    1.426499] io scheduler deadline registered
[    1.426550] io scheduler cfq registered (default)
[    1.426565] pci 0000:00:02.0: Boot video device
[    1.426841]   alloc irq_desc for 24 on node -1
[    1.426844]   alloc kstat_irqs on node -1
[    1.426858] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    1.426871] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.427046]   alloc irq_desc for 25 on node -1
[    1.427049]   alloc kstat_irqs on node -1
[    1.427059] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    1.427071] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.427240]   alloc irq_desc for 26 on node -1
[    1.427242]   alloc kstat_irqs on node -1
[    1.427252] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    1.427264] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.427387] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.427516] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.464121] ACPI: AC Adapter [ACAD] (off-line)
[    1.464197] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.464203] ACPI: Power Button [PWRF]
[    1.464279] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.464344] ACPI: Lid Switch [LID]
[    1.464396] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.464400] ACPI: Power Button [PWRB]
[    1.464453] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.464456] ACPI: Sleep Button [SLPB]
[    1.465170] ACPI: SSDT 3f691cba 001F6 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    1.465780] ACPI: SSDT 3f69177f 004B6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    1.466403] Marking TSC unstable due to TSC halts in idle
[    1.466425] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.466456] processor LNXCPU:00: registered as cooling_device0
[    1.466460] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.466878] ACPI: SSDT 3f691eb0 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    1.467308] ACPI: SSDT 3f691c35 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    1.468021] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.468052] processor LNXCPU:01: registered as cooling_device1
[    1.468056] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.784075] thermal LNXTHERM:01: registered as thermal_zone0
[    1.784085] ACPI: Thermal Zone [THRM] (28 C)
[    1.784151] isapnp: Scanning for PnP cards...
[    1.796104] ACPI: Battery Slot [BAT1] (battery absent)
[    2.138127] isapnp: No Plug & Play device found
[    2.139529] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.141089] brd: module loaded
[    2.141629] loop: module loaded
[    2.141709] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.141833] ata_piix 0000:00:1f.2: version 2.13
[    2.141849]   alloc irq_desc for 19 on node -1
[    2.141852]   alloc kstat_irqs on node -1
[    2.141859] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.141866] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.296029] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.296124] scsi0 : ata_piix
[    2.296228] scsi1 : ata_piix
[    2.296367] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    2.296370] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    2.297432] Fixed MDIO Bus: probed
[    2.297476] PPP generic driver version 2.4.2
[    2.297577] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.297599]   alloc irq_desc for 23 on node -1
[    2.297601]   alloc kstat_irqs on node -1
[    2.297606] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.297618] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.297623] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.297678] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.301588] ehci_hcd 0000:00:1d.7: debug port 1
[    2.301596] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.301617] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0644000
[    2.316020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.316104] usb usb1: configuration #1 chosen from 1 choice
[    2.316138] hub 1-0:1.0: USB hub found
[    2.316148] hub 1-0:1.0: 8 ports detected
[    2.316237] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.316256] uhci_hcd: USB Universal Host Controller Interface driver
[    2.316280] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.316288] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.316292] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.316328] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.316357] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    2.316448] usb usb2: configuration #1 chosen from 1 choice
[    2.316479] hub 2-0:1.0: USB hub found
[    2.316487] hub 2-0:1.0: 2 ports detected
[    2.316542] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.316549] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.316553] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.316595] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.316633] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    2.316719] usb usb3: configuration #1 chosen from 1 choice
[    2.316753] hub 3-0:1.0: USB hub found
[    2.316760] hub 3-0:1.0: 2 ports detected
[    2.316816] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.316824] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.316828] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.316864] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.316901] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    2.316988] usb usb4: configuration #1 chosen from 1 choice
[    2.317030] hub 4-0:1.0: USB hub found
[    2.317038] hub 4-0:1.0: 2 ports detected
[    2.317093] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.317101] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.317105] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.317141] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.317178] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    2.317265] usb usb5: configuration #1 chosen from 1 choice
[    2.317296] hub 5-0:1.0: USB hub found
[    2.317303] hub 5-0:1.0: 2 ports detected
[    2.317418] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.331166] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.338710] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.338717] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.338721] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.338725] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.338728] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.338806] mice: PS/2 mouse device common for all mice
[    2.338974] rtc_cmos 00:06: RTC can wake from S4
[    2.339009] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.339047] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.339161] device-mapper: uevent: version 1.0.3
[    2.339272] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.339387] device-mapper: multipath: version 1.1.0 loaded
[    2.339390] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.339535] EISA: Probing bus 0 at eisa.0
[    2.339541] Cannot allocate resource for EISA slot 1
[    2.339544] Cannot allocate resource for EISA slot 2
[    2.339547] Cannot allocate resource for EISA slot 3
[    2.339569] EISA: Detected 0 cards.
[    2.339793] cpuidle: using governor ladder
[    2.339944] cpuidle: using governor menu
[    2.340537] TCP cubic registered
[    2.340730] NET: Registered protocol family 10
[    2.341269] lo: Disabled Privacy Extensions
[    2.341684] NET: Registered protocol family 17
[    2.341705] Bluetooth: L2CAP ver 2.13
[    2.341708] Bluetooth: L2CAP socket layer initialized
[    2.341711] Bluetooth: SCO (Voice Link) ver 0.6
[    2.341713] Bluetooth: SCO socket layer initialized
[    2.341762] Bluetooth: RFCOMM TTY layer initialized
[    2.341766] Bluetooth: RFCOMM socket layer initialized
[    2.341768] Bluetooth: RFCOMM ver 1.11
[    2.342368] Using IPI No-Shortcut mode
[    2.342438] PM: Resume from disk failed.
[    2.342452] registered taskstats version 1
[    2.342582]   Magic number: 5:929:595
[    2.342669] rtc_cmos 00:06: setting system clock to 2009-12-26 18:36:01 UTC (1261852561)
[    2.342673] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.342675] EDD information not available.
[    2.375900] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.460612] ata2.00: ATAPI: Optiarc DVD RW AD-7590A, 1.04, max UDMA/33
[    2.468440] ata1.00: ATA-8: FUJITSU MHZ2250BH G2, 8909, max UDMA/100
[    2.468444] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.476504] ata2.00: configured for UDMA/33
[    2.484501] ata1.00: configured for UDMA/100
[    2.484695] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2250B 8909 PQ: 0 ANSI: 5
[    2.484825] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.484868] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.484923] sd 0:0:0:0: [sda] Write Protect is off
[    2.484926] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.484955] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.485100]  sda: sda1 sda2 sda3 < sda5 > sda4
[    2.486197] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.486803] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7590A  1.04 PQ: 0 ANSI: 5
[    2.494843] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.494849] Uniform CD-ROM driver Revision: 3.20
[    2.494980] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.495061] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.495117] Freeing unused kernel memory: 540k freed
[    2.495495] Write protecting the kernel text: 4568k
[    2.495559] Write protecting the kernel read-only data: 1836k
[    2.500021] Clocksource tsc unstable (delta = -128845495 ns)
[    2.638611] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input6
[    2.638659] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.673372] Linux agpgart interface v0.103
[    2.676692] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    2.677403] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    2.680472] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    2.731827] [drm] Initialized drm 1.1.0 20060810
[    2.748771] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.748778] i915 0000:00:02.0: setting latency timer to 64
[    2.755157] sky2 driver version 1.23
[    2.755197] sky2 0000:02:00.0: enabling device (0000 -> 0003)
[    2.755207] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.755223] sky2 0000:02:00.0: setting latency timer to 64
[    2.755249] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    2.755360]   alloc irq_desc for 27 on node -1
[    2.755362]   alloc kstat_irqs on node -1
[    2.755380] sky2 0000:02:00.0: irq 27 for MSI/MSI-X
[    2.756301] sky2 eth0: addr 00:1b:24:28:15:aa
[    3.460339] [drm] TV-14: set mode NTSC 480i 0
[    3.586114] [drm] fb0: inteldrmfb frame buffer device
[    3.586125] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.653535] [drm] LVDS-8: set mode 1280x800 17
[    3.917471] Console: switching to colour frame buffer device 160x50
[    4.131901] xor: automatically using best checksumming function: pIII_sse
[    4.149017]    pIII_sse  :  5914.000 MB/sec
[    4.149020] xor: using function: pIII_sse (5914.000 MB/sec)
[    4.151947] device-mapper: dm-raid45: initialized v0.2594b
[    4.497270] PM: Starting manual resume from disk
[    4.497275] PM: Resume from partition 8:5
[    4.497278] PM: Checking hibernation image.
[    4.497540] PM: Resume from disk failed.
[    4.516487] EXT4-fs (sda4): barriers enabled
[    4.540692] kjournald2 starting: pid 403, dev sda4:8, commit interval 5 seconds
[    4.540710] EXT4-fs (sda4): delayed allocation enabled
[    4.540716] EXT4-fs: file extents enabled
[    4.551655] EXT4-fs: mballoc enabled
[    4.551672] EXT4-fs (sda4): mounted filesystem with ordered data mode
[    5.154071] type=1505 audit(1261852564.310:2): operation="profile_load" pid=426 name=/usr/share/gdm/guest-session/Xsession
[    5.157581] type=1505 audit(1261852564.313:3): operation="profile_load" pid=427 name=/sbin/dhclient3
[    5.158574] type=1505 audit(1261852564.313:4): operation="profile_load" pid=427 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.159043] type=1505 audit(1261852564.313:5): operation="profile_load" pid=427 name=/usr/lib/connman/scripts/dhclient-script
[    5.210347] type=1505 audit(1261852564.365:6): operation="profile_load" pid=428 name=/usr/bin/evince
[    5.224307] type=1505 audit(1261852564.381:7): operation="profile_load" pid=428 name=/usr/bin/evince-previewer
[    5.232471] type=1505 audit(1261852564.389:8): operation="profile_load" pid=428 name=/usr/bin/evince-thumbnailer
[    5.253972] type=1505 audit(1261852564.409:9): operation="profile_load" pid=430 name=/usr/lib/cups/backend/cups-pdf
[   17.208519] udev: starting version 147
[   17.243769] lp: driver loaded but no devices found
[   17.257345] Adding 2996080k swap on /dev/sda5.  Priority:-1 extents:1 across:2996080k 
[   17.703594] intel_rng: FWH not detected
[   17.748318] acer-wmi: Acer Laptop ACPI-WMI Extras
[   17.773234] yenta_cardbus 0000:0a:09.0: CardBus bridge found [1025:0110]
[   17.773262] yenta_cardbus 0000:0a:09.0: Using CSCINT to route CSC interrupts to PCI
[   17.773265] yenta_cardbus 0000:0a:09.0: Routing CardBus interrupts to PCI
[   17.773272] yenta_cardbus 0000:0a:09.0: TI: mfunc 0x01321b22, devctl 0x66
[   17.830423] cfg80211: Calling CRDA to update world regulatory domain
[   17.848413] EXT4-fs (sda4): internal journal on sda4:8
[   17.867451] ath5k 0000:03:00.0: enabling device (0000 -> 0002)
[   17.867463] ath5k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.867478] ath5k 0000:03:00.0: setting latency timer to 64
[   17.867514] ath5k 0000:03:00.0: registered as 'phy0'
[   17.891517] cfg80211: World regulatory domain updated:
[   17.891521] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.891525] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.891529] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.891532] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.891535] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.891538] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.936466] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.973132] ath: EEPROM regdomain: 0x65
[   17.973135] ath: EEPROM indicates we should expect a direct regpair map
[   17.973140] ath: Country alpha2 being used: 00
[   17.973142] ath: Regpair used: 0x65
[   18.003547]   alloc irq_desc for 22 on node -1
[   18.003551]   alloc kstat_irqs on node -1
[   18.003559] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.003611] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.012357] phy0: Selected rate control algorithm 'minstrel'
[   18.013279] Registered led device: ath5k-phy0::rx
[   18.013301] Registered led device: ath5k-phy0::tx
[   18.013305] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   18.022499] yenta_cardbus 0000:0a:09.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   18.022505] yenta_cardbus 0000:0a:09.0: Socket status: 30000006
[   18.022509] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   18.022519] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   18.022523] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   18.022791] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   18.022795] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   18.023376] tifm_7xx1 0000:0a:09.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.087990] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   18.350975] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   18.353047] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.353909] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   18.354617] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   18.355522] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.690758] sky2 eth0: enabling interface
[   18.690985] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.736480] ath5k phy0: noise floor calibration failed (2412MHz)
[   18.761351] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.774443] __ratelimit: 6 callbacks suppressed
[   18.774447] type=1505 audit(1261877777.929:12): operation="profile_replace" pid=963 name=/usr/share/gdm/guest-session/Xsession
[   18.776376] type=1505 audit(1261877777.933:13): operation="profile_replace" pid=964 name=/sbin/dhclient3
[   18.777286] type=1505 audit(1261877777.933:14): operation="profile_replace" pid=964 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.777799] type=1505 audit(1261877777.933:15): operation="profile_replace" pid=964 name=/usr/lib/connman/scripts/dhclient-script
[   18.782045] type=1505 audit(1261877777.937:16): operation="profile_replace" pid=965 name=/usr/bin/evince
[   18.796622] type=1505 audit(1261877777.953:17): operation="profile_replace" pid=965 name=/usr/bin/evince-previewer
[   18.804836] type=1505 audit(1261877777.961:18): operation="profile_replace" pid=965 name=/usr/bin/evince-thumbnailer
[   18.825710] type=1505 audit(1261877777.981:19): operation="profile_replace" pid=972 name=/usr/lib/cups/backend/cups-pdf
[   18.826718] type=1505 audit(1261877777.981:20): operation="profile_replace" pid=972 name=/usr/sbin/cupsd
[   18.849290] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   18.855991] type=1505 audit(1261877778.009:21): operation="profile_replace" pid=973 name=/usr/sbin/tcpdump
[   18.909038] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   18.985687] ath5k phy0: noise floor calibration failed (2417MHz)
[   19.287087] [drm] TV-14: set mode NTSC 480i 0
[   19.427287] [drm] TV-14: set mode NTSC 480i 0
[   19.712043] [drm] TV-14: set mode NTSC 480i 0
[   19.852913] [drm] TV-14: set mode NTSC 480i 0
[   20.206132] ppdev: user-space parallel port driver
[   20.659462] ath5k phy0: noise floor calibration failed (2412MHz)
[   22.143126] [drm] TV-14: set mode NTSC 480i 0
[   22.283607] [drm] TV-14: set mode NTSC 480i 0
[   22.559393] [drm] TV-14: set mode NTSC 480i 0
[   22.699416] [drm] TV-14: set mode NTSC 480i 0
[   22.991031] [drm] TV-14: set mode NTSC 480i 0
[   23.131052] [drm] TV-14: set mode NTSC 480i 0
[   33.276453] [drm] TV-14: set mode NTSC 480i 0
[   33.416562] [drm] TV-14: set mode NTSC 480i 0
[   33.696350] [drm] TV-14: set mode NTSC 480i 0
[   33.837728] [drm] TV-14: set mode NTSC 480i 0
[   34.116312] [drm] TV-14: set mode NTSC 480i 0
[   34.257238] [drm] TV-14: set mode NTSC 480i 0
[   35.188095] [drm] TV-14: set mode NTSC 480i 0
[   35.328197] [drm] TV-14: set mode NTSC 480i 0
[   37.380827] ath5k phy0: noise floor calibration failed (2417MHz)
[   38.681593] ath5k phy0: noise floor calibration failed (2412MHz)
[   38.712249] wlan0: authenticate with AP 00:1c:10:49:b5:43
[   38.714225] wlan0: authenticated
[   38.714231] wlan0: associate with AP 00:1c:10:49:b5:43
[   38.716250] wlan0: RX AssocResp from 00:1c:10:49:b5:43 (capab=0x411 status=0 aid=1)
[   38.716255] wlan0: associated
[   38.720504] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.915448] ath5k phy0: noise floor calibration failed (2412MHz)
[   39.311632] ath5k phy0: noise floor calibration timeout (2417MHz)
[   40.592793] padlock: VIA PadLock not detected.
[   49.272035] wlan0: no IPv6 routers present
[   70.027377] ath5k phy0: noise floor calibration timeout (2417MHz)
[  105.071796] wlan0: deauthenticating by local choice (reason=3)
[  105.141133] wlan0: disassociating by local choice (reason=3)
[  105.880420] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  106.039570] ath5k phy0: noise floor calibration failed (2417MHz)
[  106.437238] ath5k phy0: noise floor calibration timeout (2422MHz)
[  117.298960] wlan0: authenticate with AP 00:1c:10:49:b5:43
[  117.300467] wlan0: authenticated
[  117.300470] wlan0: associate with AP 00:1c:10:49:b5:43
[  117.302704] wlan0: RX AssocResp from 00:1c:10:49:b5:43 (capab=0x411 status=0 aid=1)
[  117.302708] wlan0: associated
[  117.303416] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  127.796119] wlan0: no IPv6 routers present
[  498.617068] CE: hpet increasing min_delta_ns to 15000 nsec
[  509.237761] wlan0: disassociating by local choice (reason=3)
[  509.292283] wlan0: deauthenticating by local choice (reason=3)
[  510.040568] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  521.469960] wlan0: authenticate with AP 00:1c:10:49:b5:43
[  521.471466] wlan0: authenticated
[  521.471470] wlan0: associate with AP 00:1c:10:49:b5:43
[  521.473795] wlan0: RX AssocResp from 00:1c:10:49:b5:43 (capab=0x411 status=0 aid=1)
[  521.473802] wlan0: associated
[  521.474875] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  531.800108] wlan0: no IPv6 routers present
[ 1601.249267] wlan0: deauthenticating by local choice (reason=3)
[ 1601.316076] wlan0: disassociating by local choice (reason=3)
[ 1602.041583] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1613.453193] wlan0: authenticate with AP 00:1c:10:49:b5:43
[ 1613.454700] wlan0: authenticated
[ 1613.454704] wlan0: associate with AP 00:1c:10:49:b5:43
[ 1613.457098] wlan0: RX AssocResp from 00:1c:10:49:b5:43 (capab=0x411 status=0 aid=1)
[ 1613.457109] wlan0: associated
[ 1613.457978] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1624.080096] wlan0: no IPv6 routers present
[ 1913.948141] ACPI: EC: missing confirmations, switch off interrupt mode.
[19866.299848] ath5k phy0: unsupported jumbo
[53345.766357] ath5k phy0: unsupported jumbo
[55648.146974] ath5k phy0: unsupported jumbo
[64209.123923] ath5k phy0: unsupported jumbo
[64629.957543] ath5k phy0: unsupported jumbo
[66185.468491] ath5k phy0: unsupported jumbo
[67063.110815] ath5k phy0: noise floor calibration timeout (2422MHz)
[67221.477714] ath5k phy0: unsupported jumbo
[71167.098159] ath5k phy0: unsupported jumbo
[72196.214838] ath5k phy0: unsupported jumbo
[73177.213715] ath5k phy0: unsupported jumbo
[79608.241279] wlan0: deauthenticating by local choice (reason=3)
[79608.306612] wlan0: disassociating by local choice (reason=3)
[79609.041570] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[79620.460165] wlan0: authenticate with AP 00:1c:10:49:b5:43
[79620.461661] wlan0: authenticated
[79620.461665] wlan0: associate with AP 00:1c:10:49:b5:43
[79620.463995] wlan0: RX AssocResp from 00:1c:10:49:b5:43 (capab=0x411 status=0 aid=1)
[79620.464033] wlan0: associated
[79620.465138] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[79630.636039] wlan0: no IPv6 routers present
[79691.270104] wlan0: deauthenticating by local choice (reason=3)
[79691.337720] wlan0: disassociating by local choice (reason=3)
[79692.041585] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

You'll notice from dmesg I'm using ath5k, notice the lines toward the end:

```
[ 1913.948141] ACPI: EC: missing confirmations, switch off interrupt mode.
[19866.299848] ath5k phy0: unsupported jumbo
[53345.766357] ath5k phy0: unsupported jumbo
[55648.146974] ath5k phy0: unsupported jumbo
[64209.123923] ath5k phy0: unsupported jumbo
[64629.957543] ath5k phy0: unsupported jumbo
[66185.468491] ath5k phy0: unsupported jumbo
[67063.110815] ath5k phy0: noise floor calibration timeout (2422MHz)
[67221.477714] ath5k phy0: unsupported jumbo
[71167.098159] ath5k phy0: unsupported jumbo
[72196.214838] ath5k phy0: unsupported jumbo
[73177.213715] ath5k phy0: unsupported jumbo
[79608.241279] wlan0: deauthenticating by local choice (reason=3)
[79608.306612] wlan0: disassociating by local choice (reason=3)
```

showkey reports 224 and 225 before AND after the rfkill.

---

### Post by raycosm on 2009-12-31
I'm using an Aspire 5570Z with an AR5007EG, and I blacklisted acer-wmi. I blacklisted both acer-wmi and acer_wmi because I didn't know which one to blacklist, was too lazy to test to see which one it was, and figured it didn't matter anyway if I just blacklisted both.

Anywho, my wireless doesn't seem to be disconnecting every time I hit a button to change my brightness. I do notice though that my screen brightness no longer changes when I plug or unplug my laptop (I'm using KDE 4.4 beta 2), but that was more of an annoyance than a feature to me anyway. Blacklisting it was a simple enough fix for me.

---

### Post by flavanoid on 2010-02-27
So just a little follow up here... I installed a new Mini PCI-E wireless card in my laptop, hoping to alleviate the issue (intel, can't think of the model right off hand).  This issue is still happening with the intel card as well.

These dmesg lines are present before and after card change:

```
[14526.211364] wlan1: deauthenticating by local choice (reason=3)
[14526.284663] wlan1: disassociating by local choice (reason=3)
```

---

### Post by Chojniczanin on 2010-03-16
Just solved on my Aspire 7540 by Acer.

You just need to get rid off the smartdimmer. Don't forget replacing crappy network-manager with wicd. It also causes disconnections. 

Use synaptics or just type in terminal:
```
sudo apt-get remove smartdimmer
sudo apt-get install wicd
```

Works for me :D

---

