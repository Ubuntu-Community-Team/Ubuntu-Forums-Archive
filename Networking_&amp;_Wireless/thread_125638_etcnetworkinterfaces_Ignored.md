---
title: "/etc/network/interfaces Ignored"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by cheuschober on 2006-02-04
Hi-

Having a doozy of a time getting my pci Atheros5212 card up and working.

Installed ubuntu (this time ubuntu chose 386 as the default kernel) and the wireless enabled by the restricted-modules madwifi worked out of the box through the first or second restart then stopped working properly. Tried madwifi-ng as per the how-to (you'll find several posts of mine in [there]("http://www.ubuntuforums.org/showthread.php?t=105437").

It worked for a short period, then stopped. I tried a fresh install of ubuntu again, 386 kernel again, this time the boxed madwifi driver didn't work and after the setpci trick found in the madwifi documentation I was able to get madwifi-ng up and running until I had to restart once and after that no amount of tweeking seemed to get it up including uninstallation and reinstallation of the driver.

Did a fresh installation of ubuntu again, this time for some strange reason or another the 686 kernel was chosen by the system as the default kernel. Wireless worked out of the box again though the system wasn't using my /etc/network/interfaces file to configure any network settings and instead has relied upon manual entry of ifconfig and iwconfig statements. After manually entering these statements and then disabling ipv6 (my router does not like ipv6 and reacts rather negatively to it) I was able to get access for all of about and hour and a half. I actually never left the computer when it most recently stopped working -- I was browsing the web perfectly fine and had just started GAIM when gaim refused to connect. All further traffic ceased included http and the only working pings were those directly to my interfaces or to my router. Pings sent to other computers on my network or outside (such as to yahoo.com) were unreachable. At time I was referring to my wireless interface as ath0.

I removed the linux restricted modules and went through the careful installation of madwifi-ng certain of specifying the gcc-3.4 compiler and using the setpci trick as set forth in the madwifi-ng documentation. The driver (which I've uninstalled and reinstalled several times) does not attach immediately or even after /etc/init.d/networking restart -- it only attaches after a full restart. I do have a wifi0 interface after this but nothing works as it should. I have tried many different attacks on this but nothing to this point has worked.

One 'mistake' of note is that no matter what driver seems to be installed or whatever is defined in ///interfaces the system seems bent upon having an ath0 interface. The only exception to this is when there is no driver installed at all. I attempted trouble shooting this with every combination of map, auto, ath0, wifi0, and alias settings possible. In fact, when I comment out every interface but the loopback and eth0 (my wired interface) it /still/ creates an ath0 interface on startup but leaves it totally unconfigured with little more than a hardware address. When I have established my ath0 interface in ///interfaces it ignores any of the information found therein and again establishes an unconfigured 'blank' interface.

Using wlanconfig I /can/ destroy this interface and choose to recreate it if I so desire but ANY interface created via wlanconfig (or any other function for that matter) ignores /etc/network/interfaces. If I manually configure a newly created interfaces I can pass it the necessary arguments (for the most part) to set essid's, addresses (I use static), keys, etc and after said configuration I can begin communicating with my router again via pings (or via the router interface in a browser) but again I can't travel outside of a direct call to the router. It sounds like a DNS issue and the DNS nameserver should be my router as is specified in resolv.conf but it looks like this is also being ignored by the system and I don't know of a way to manually set it via if/iwconfig to test if communication is possible beyond that.

Below is the output of several functions if it helps. Please note that this is not the only incarnation of /etc/network/interfaces I've been working with and I know some pieces are non-traditional and / or incorrect, right now I'm trying anything -- it has changed about once every 10 minutes 4 hours for the last week (how much time I've had to devote to this). I'd love your input of course but I really don't think this is related to that file specifically -- there's probably not a combination I haven't already tried.

Many thanks for any advice / assistance.

~Chad

Current incarnation of /etc/network/interfaces (X omits personal data)
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
#	map wifi0
#	map edgec0

#The wireless wrapper
#iface wifi0 inet dhcp
#auto wifi0

#The wireless interface
iface edgec0 inet static
	pre-up wlanconfig edgec0 create wlandev wifi0 wlanmode sta
	address 192.168.221.XXX
	netmask 255.255.255.0
	network 192.168.221.0
	gateway 192.168.221.1
	dns-nameservers 192.168.221.1
	wireless-essid XXXX
	wireless-mode managed
	wireless-key restricted [1] XXXXXXXXXXXXXX
	wireless-rate 54M
	wireless-channel 8
	wireless-ap: 00:04:E2:D6:DF:E6
auto edgec0

# The wired interface
iface eth0 inet static
	address 192.168.221.XXX
	netmask 255.255.255.0
	network 192.168.221.0
	broadcast 192.168.221.255
	gateway 192.168.221.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.221.1

```

Current /etc/resolv.conf
```

nameserver 192.168.221.1

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:23612  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig -a
```

ath0      Link encap:Ethernet  HWaddr 00:90:96:84:45:44
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:08:0D:EE:84:D0
          inet addr:192.168.221.XXX  Bcast:192.168.221.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1456825 (1.3 MiB)  TX bytes:224425 (219.1 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8477447 (8.0 MiB)  TX bytes:8477447 (8.0 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-90-96-84-45-44-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23631 errors:0 dropped:0 overruns:0 frame:18675
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:1834960 (1.7 MiB)  TX bytes:0 (0.0 b)
          Interrupt:22 Memory:f8bc0000-f8bd0000

```

lshw -C Network (ifup does not bring wifi0 up but doesn't error either)
```

 *-network:0 DISABLED
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@01:05.0
       logical name: wifi0
       version: 01
       serial: 00:90:96:84:45:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (Atheros/multi-bss) multicast=yes wireless=IEEE 802.11b
       resources: iomemory:cfff0000-cfffffff irq:22
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:ee:84:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=full firmware=N/A ip=192.168.221.101 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:cffef000-cffeffff ioport:cf40-cf7f irq:20

```

lspci -vvx -s 01:05.0
```

0000:01:05.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Askey Computer Corp.: Unknown device 7058
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at cfff0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>
00: 8c 16 13 00 06 00 90 02 01 00 00 02 08 a8 00 00
10: 00 00 ff cf 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 01 50 00 00 4f 14 58 70
30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 0a 1c

```

dmesg (partial)
```

...
[4294699.149000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
[4294699.149000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294699.149000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294699.959000] intel8x0_measure_ac97_clock: measured 49363 usecs
[4294699.959000] intel8x0: clocking to 48000
[4294700.596000] ath_hal: module license 'Proprietary' taints kernel.
[4294700.601000] ath_hal: 0.9.16.13 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413, DFS)
[4294700.627000] wlan: 0.8.4.2 (Atheros/multi-bss)
[4294700.639000] ath_rate_sample: 1.2
[4294700.648000] ath_pci: 0.9.4.5 (Atheros/multi-bss)
[4294700.653000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294700.934000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294700.934000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294700.934000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[4294700.934000] wifi0: mac 5.6 phy 4.1 radio 1.7
[4294700.934000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[4294700.934000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[4294700.934000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[4294700.934000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[4294700.934000] wifi0: Use hw queue 8 for CAB traffic
[4294700.934000] wifi0: Use hw queue 9 for beacons
[4294700.952000] wifi0: Atheros 5212: mem=0xcfff0000, irq=22
[4294701.239000] Linux Kernel Card Services
[4294701.239000]   options:  [pci] [cardbus] [pm]
[4294701.257000] PCI: Enabling device 0000:01:0b.0 (0000 -> 0002)
[4294701.257000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294701.257000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
[4294701.377000] Yenta: ISA IRQ mask 0x04b8, PCI irq 18
[4294701.377000] Socket status: 30000007
[4294702.773000] input: PC Speaker
[4294702.914000] Real Time Clock Driver v1.12
[4294703.825000] NET: Registered protocol family 17
[4294771.741000] ACPI: AC Adapter [ADP1] (on-line)
[4294771.788000] ACPI: Battery Slot [BAT1] (battery present)
[4294771.810000] ACPI: Power Button (FF) [PWRF]
[4294771.810000] ACPI: Lid Switch [LID]
[4294771.810000] ACPI: Power Button (CM) [PWRB]
[4294771.947000] ibm_acpi: ec object not found
[4294772.050000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[4294772.050000] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[4294772.071000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[4294772.071000] toshiba_acpi: ktoshkeyd will check 2 times per second
[4294772.071000] toshiba_acpi: Dropped 0 keys from the queue on startup
[4294772.094000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[4294779.114000] [drm] Initialized drm 1.0.0 20040925
[4294779.121000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294779.131000] [drm] Initialized i915 1.2.0 20040405 on minor 0: Intel Corporation 82852/855GM Integrated Graphics Device
[4294779.131000] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
[4294779.133000] [drm] Initialized i915 1.2.0 20040405 on minor 1: Intel Corporation 82852/855GM Integrated Graphics Device (#2)
[4294779.134000] mtrr: base(0xd8020000) is not aligned on a size(0x300000) boundary
[4294781.046000] apm: BIOS not found.
[4294781.672000] cs: IO port probe 0x100-0x4ff: excluding 0x1e0-0x1e7 0x4d0-0x4d7
[4294781.673000] cs: IO port probe 0xc00-0xcf7: clean.
[4294781.674000] cs: IO port probe 0xa00-0xaff: clean.
[4294782.527000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[4294783.480000] Bluetooth: Core ver 2.7
[4294783.481000] NET: Registered protocol family 31
[4294783.481000] Bluetooth: HCI device and connection manager initialized
[4294783.481000] Bluetooth: HCI socket layer initialized
[4294783.605000] Bluetooth: L2CAP ver 2.7
[4294783.605000] Bluetooth: L2CAP socket layer initialized
[4294783.634000] Bluetooth: RFCOMM ver 1.5
[4294783.634000] Bluetooth: RFCOMM socket layer initialized
[4294783.634000] Bluetooth: RFCOMM TTY layer initialized
[4295218.971000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4295279.465000] hdc: drive_cmd: status=0xd0 { Busy }
[4295279.465000] ide: failed opcode was: 0xa1
[4295279.548000] SCSI subsystem initialized
...

```

---

### Post by hajk on 2006-02-04
Boy, you've done a lot of work... reinstalling Ubuntu a few times, installing all sorts of wrappers, and what not. You seem to have unbounded energy, yet you've not been effective... 

A simple question: with not just install the madwifi driver from the linux-restricted-modules package for your kernel, do "sudo modprobe madwifi" if needed, followed by letting System/Administration/Networking do its thing: highlight ath0 interface, hit Properties: select the network to join DHCP and hit OK, then hit activate, and watch the connection being made... No need to mess with /etc/network/interfaces yourself, is there?

That's the way I did it on my computer, works like a charm....

---

### Post by cheuschober on 2006-02-04
Actually yes, yes I have tried that minus DHCP because my network is not and cannot be a DHCP network. Not only would it make file and printer sharing as well as access control considerably more difficult to administer by a power of 20 but my router is notorius for seriously screwing up DHCP and the only way to ensure consistent operation is through Static IP. The networking gui doesn't really resolve any of this, such as the need for setting a SUBORDINATE_BUS. I should also note that whether or not you go through the networking gui or you go through gedit you are still 'messing' with /etc/network/interfaces

I wish it was that simple but I've noted above that the 'boxed' madwifi driver (as in the one that comes as part of linux-restricted-modules) doesn't work most of the time or in the few occasions it has worked it's eventually stopped working. At the very least madwifi-ng is slightly more consistent in its behaviour even if it works just about as often.

Any other thoughts from anyone who might have a clue as to what's going on or how to better diagnose the problem are greatly appreciated.

~Chad

---

### Post by Lambert on 2006-02-05
Little tired, (long day) want to come back to this and help you and I will.

One thing to note now though.

When the how to was written for -ng, the wlanconfig ath0 create.... pre-up command was necessary to get an interface on boot. The driver has since been updated and automatically creates the interface with out that stanza (I believe through udev) so you can remove that from the interface file. So this is why no matter what you do you get the ath0 interface.

I don't run breezy (testing dapper) so I only played with breezy for a few minutes, but I noticed with that pre-up stanza I couldn't get an active interface on boot. I was also getting an ath2 interface which I couldn't do anything with. So for now try removing that stanza.

---

### Post by cheuschober on 2006-02-06
Thanks a great deal Lambert.

Interesting bit on the auto-ath0, though I must admit it seems somewhat antithetical to what I thought -ng's biggest selling point was: a robust method for the management and creation of virtual interfaces. Not that it is your's or anyone else's bag, it just makes me curious -- one would imagine that part of the great flexibility of -ng is having a virtually unlimited array of virtual devices available that could then be paired with auto-configuration scripts to utilize the correct devices in the correct physical environment. If ath0 is always created then the user has to go to the trouble of possibly destroying it or taking it down quite regularly -- bringing up an ath0 interface, running a script to decide which interface to bring up, bringing up the correct interface, taking down the ath0 interface -- two of those steps could be omitted. Just a little odd to me.

More odd, and more pertinent, however, is the curiousness of 'ath0'. Strangely enough in my many edits of the interfaces file I changed edgec0 (and all references to it) to ath0 just to see if it would 'bite' that stanza and configure itself properly since the driver seems bent upon having ath0. No luck whatsoever -- it'll bring up ath0 but won't configure. I'm relatively sure I commented out the pre-up line at one point or another but not a 100%. When I get home this evening I'll give it a go.

Best regards,
~Chad

---

### Post by cheuschober on 2006-02-06
Good stuff Lambert!

I took the pre-up line out of the wireless stanza and renamed the device to ath0. Initially I brought it up with 'iwconfig ath0 up' and was treated to the same behaviour as before but after bringing the interface down again I tried an 'ifup' statement and it worked and configured itself on the network -- very very curious but it's at least working!

I'd like to know if there's a way to disable the auto-creation of the ath0 interface and how one might automate the creation and activation of another interface. Let's say I /did/ want to use edgec0 as a default interface... do we have a workaround?

~Chad

---

### Post by SickTwist on 2006-02-07
[QUOTE=cheuschober]Good stuff Lambert!

I took the pre-up line out of the wireless stanza and renamed the device to ath0. Initially I brought it up with 'iwconfig ath0 up' and was treated to the same behaviour as before but after bringing the interface down again I tried an 'ifup' statement and it worked and configured itself on the network -- very very curious but it's at least working!

I'd like to know if there's a way to disable the auto-creation of the ath0 interface and how one might automate the creation and activation of another interface. Let's say I /did/ want to use edgec0 as a default interface... do we have a workaround?

~Chad[/QUOTE]

The automatic creation of the default interface can be disabled by passing a parameter to the madwifi kernel module (ath_pci). Add this line to /etc/modules:

ath_pci autocreate=none

For more details about the driver, run "modinfo ath_pci" without quotes.

The interface prefix ("ath" by default) can be whatever you want it to be. This can be changed manually with the wlanconfig command (see "man wlanconfig"). If you downloaded the madwifi-ng source, look at madwifi-ng/docs/users-guide.pdf for more information.

On a final note, /etc/network/interfaces is only used by ifup and ifdown. It is not used by ifconfig or iwconfig. I've been running Breezy for about a week on an IBM T41 Thinkpad with an Atheros AR5212 chipset. Ifup and ifdown didn't seem to be working correctly for me and I also had some noticable lag when running iwlist to scan for access points. I ended up installing the latest madwifi-ng snapshot and that seemed to run *much* better than the default Breezy madwifi modules in the linux-restricted-modules package. I have still avoided using ifup/ifdown and I disabled ifup from trying to start my wireless adapter at boot (remove "auto ath0" from /etc/network/interfaces).

I installed [NetworkManager]("http://www.gnome.org/projects/NetworkManager/") (the "network-manager" package is in Universe) to handle configuring the wireless interface. You need to add "nm-applet" to Startup Programs under System-->Preferences-->Sessions in order for it to run automatically when you log in. Or just start it manually by pressing ALT+F2 and typing "nm-applet" (without quotes). I think NetworkManager relies on the wireless network using DHCP, though. Good luck with it and let me know if you need more help.

---

### Post by Ms. Phitt on 2006-02-19
If I understand your issue correctly, this may be helpful. One thing I've noticed pretty consistently, regardless whether I'm using Madwifi or not, is the fact that when both eth0 and my wireless adapter are up, they seem to conflict with each other and cause not just DNS issues, but routing issues in general. A ping to the router will give replies, and a ping to yahoo.com will give an unknown host error. But it's not just a DNS issue because if I ping an IP like 4.2.2.1 (happens to be a Verizon DNS server), it also gets an unknown host error. No DNS involved there. I've resolved it by either taking down the adapter I'm not using, for example: ```
ifconfig ath0 down
``` or taking both of them down and bringing only one back up: ```
ifconfig eth0 down 
ifconfig ath0 down 
ifup eth0
``` I usually use my wireless more than ethernet. For a more permanent solution, I go into the Network Settings and set the wireless to "start at boot" and the ethernet to "start manually." Then I generally get the wireless with proper routing to the web and it pulls DNS information automatically as it should. You can set eth0 to start at boot and ath0 to start manually too, if you prefer.

Hope this helps!

---

