---
title: "eth0 disappears completely until reboot"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by chaosdx on 2006-02-23
Hello,
I have a clean install of UBB 5.10 (reinstalled clean several times, actually, on a dual-boot box with WinXP), aDSL ethernet-interface modem (Huawei MT800), on-board network controller (NVIDIA nForce2), and I seem to be having the following trouble(s):

My modem is remotely configured not to break connection, my isp forces it no more often than once a day, i don't have to touch it at all, it's working under windows just fine and the PC sees itself as connected to a local network with a static IP, normally (i entered it on UBB installation).

After I boot under Ubuntu, the eth0 is initialized ok, time is syncronized, etc, I'm able to use the connection for a few (about 5) minutes normally BUT then it just disappears altogether, be it in the middle of apt-get, or an IRC chat (no matter what is the load, i mean). I can't ifup/ifdown eth0, because it says to the effect of "No such interface", doesn't list it in ifconfig's *all* interfaces (just lo and sit0, afair), when i try to enter GUI network management there is no eth0 or any other eth listed. At all. (there is another trouble that GUI sudo for no program will accept my root pass, but it's impossible to work with GUI for now anyway - see below - so i stick to console).

I've checked the configuration file, it is totally normal both comparatively to the other such conf files and according to the man, "auto eth0", etc. I didn't change anything.

When I reboot, the connection is okay again, for another ~5min.

PS. I'm a n00b and I'm fairly desperate, because I need to figure out a way to compile/install Nvidia drivers, (640*480 resolution and no sound is killing me), thus d/ling tools for compilation the drivers say I need, and the connection fails berofe apt-get can finish updating anything :( 

Thank you in advance.

---

### Post by jamesr on 2006-02-24
I know that you said that 
> doesn't list it in ifconfig's all interfaces 
but 
sudo ifconfig -a while working
sudo ifconfig -a after failure
 
sudo dhclient
and list messages
and then check 
sudo ifconfig -a again

---

### Post by chaosdx on 2006-02-24
working:
```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:40:59:3A  
          inet addr:192.168.1.83  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe40:593a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:895164 (874.1 KiB)  TX bytes:148413 (144.9 KiB)
          Interrupt:22 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1219 (1.1 KiB)  TX bytes:1219 (1.1 KiB)

sit0      Link encap:IPv6-in-IPv4  
          inet6 addr: ::192.168.1.83/96 Scope:Compat
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:23 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

dhclient

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth0/00:00:00:40:59:3a
Sending on   LPF/eth0/00:00:00:40:59:3a
Sending on   Socket/fallback
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
immediately after that - failed:

```
 ifconfig -a
lo        Link encap:Local Loopback  
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8863 (8.6 KiB)  TX bytes:8863 (8.6 KiB)

sit0      Link encap:IPv6-in-IPv4  
          inet6 addr: ::192.168.1.83/96 Scope:Compat
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:23 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

dhclient

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
naturally,
```

ifup eth0
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.

ifdown eth0
ifdown: interface eth0 not configured

```

---

### Post by jamesr on 2006-02-24
Noted your reply I going to try and  find my notes on disabling ipv6.
 ALso before and after
lspci
lsmod

In your dhclient output, it shows that it is not even trying eth0

Do you know what driver is being loaded, should able to find the information in dmesg.

---

### Post by chaosdx on 2006-02-27
lspci -v
```

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Memory at e8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [40] AGP version 2.0
	Capabilities: [60] #08 [2001]

0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [48] #08 [01e1]

0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at e400 [size=32]
	Capabilities: [44] Power Management version 2

0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at ee002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at ee003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at ee004000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] #0a [2080]
	Capabilities: [80] Power Management version 2

0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at ee001000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e000 [size=8]
	Capabilities: [44] Power Management version 2

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
	Subsystem: nVidia Corporation: Unknown device 4144
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at d000 [size=256]
	I/O ports at d400 [size=128]
	Memory at ee005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32

0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: nVidia Corporation: Unknown device 05b2
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at f000 [size=16]
	Capabilities: [44] Power Management version 2

0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: ec000000-edffffff
	Prefetchable memory behind bridge: e0000000-e7ffffff

0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3) (prog-if 00 [VGA])
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
	Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Memory at e4000000 (32-bit, prefetchable) [size=512K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 2.0


```

lspci -v after

```

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Memory at e8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [40] AGP version 2.0
	Capabilities: [60] #08 [2001]

0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c17
	Flags: 66MHz, fast devsel

0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [48] #08 [01e1]

0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at e400 [size=32]
	Capabilities: [44] Power Management version 2

0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at ee002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at ee003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at ee004000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] #0a [2080]
	Capabilities: [80] Power Management version 2

0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: 66MHz, fast devsel, IRQ 22
	Memory at ee001000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e000 [size=8]
	Capabilities: [44] Power Management version 2

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
	Subsystem: nVidia Corporation: Unknown device 4144
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at d000 [size=256]
	I/O ports at d400 [size=128]
	Memory at ee005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32

0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: nVidia Corporation: Unknown device 05b2
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at f000 [size=16]
	Capabilities: [44] Power Management version 2

0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: ec000000-edffffff
	Prefetchable memory behind bridge: e0000000-e7ffffff

0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3) (prog-if 00 [VGA])
	Subsystem: nVidia Corporation: Unknown device 0c11
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
	Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Memory at e4000000 (32-bit, prefetchable) [size=512K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 2.0


```

lsmod before
```

Module                  Size  Used by
rfcomm                 38748  0 
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
cpufreq_userspace       4380  0 
cpufreq_stats           5316  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1792  0 
cpufreq_ondemand        6108  0 
cpufreq_conservative     7012  0 
video                  15812  0 
tc1100_wmi              6788  0 
sony_acpi               5388  0 
pcc_acpi               11200  0 
hotkey                  9380  0 
dev_acpi               11268  0 
i2c_acpi_ec             5568  0 
button                  6544  0 
battery                 9412  0 
container               4480  0 
ac                      4804  0 
ipv6                  252544  6 
pcspkr                  3460  0 
rtc                    12408  0 
shpchp                 97252  0 
pci_hotplug            27636  1 shpchp
snd_intel8x0           33344  1 
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0 
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
i2c_core               21328  2 i2c_acpi_ec,i2c_nforce2
nvidia_agp              8412  1 
agpgart                34888  1 nvidia_agp
dm_mod                 58044  1 
tsdev                   7872  0 
evdev                   9728  0 
psmouse                30212  0 
mousedev               11680  1 
parport_pc             35460  1 
lp                     12420  0 
parport                36104  2 parport_pc,lp
md                     45648  0 
ext3                  137352  1 
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0 
processor              22908  1 thermal
fan                     4548  0 
forcedeth              21568  0 
ehci_hcd               34312  0 
ohci_hcd               20740  0 
usbcore               118396  3 ehci_hcd,ohci_hcd
ide_cd                 41732  0 
cdrom                  39904  1 ide_cd
ide_disk               18560  4 
ide_generic             1472  0 
sata_nv                 9412  0 
libata                 54020  1 sata_nv
scsi_mod              135944  1 libata
amd74xx                14044  1 
ide_core              139028  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   27248  358 
vesafb                  8088  0 
capability              4808  0 
commoncap               6912  1 capability
vga16fb                12680  1 
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72 
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon

```

lsmod after

```

Module                  Size  Used by
rfcomm                 38748  0 
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
cpufreq_userspace       4380  0 
cpufreq_stats           5316  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1792  0 
cpufreq_ondemand        6108  0 
cpufreq_conservative     7012  0 
video                  15812  0 
tc1100_wmi              6788  0 
sony_acpi               5388  0 
pcc_acpi               11200  0 
hotkey                  9380  0 
dev_acpi               11268  0 
i2c_acpi_ec             5568  0 
button                  6544  0 
battery                 9412  0 
container               4480  0 
ac                      4804  0 
ipv6                  252544  6 
pcspkr                  3460  0 
rtc                    12408  0 
shpchp                 97252  0 
pci_hotplug            27636  1 shpchp
snd_intel8x0           33344  1 
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0 
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm
i2c_nforce2             6784  0 
i2c_core               21328  2 i2c_acpi_ec,i2c_nforce2
nvidia_agp              8412  1 
agpgart                34888  1 nvidia_agp
dm_mod                 58044  1 
tsdev                   7872  0 
evdev                   9728  0 
psmouse                30212  0 
mousedev               11680  1 
parport_pc             35460  1 
lp                     12420  0 
parport                36104  2 parport_pc,lp
md                     45648  0 
ext3                  137352  1 
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0 
processor              22908  1 thermal
fan                     4548  0 
ehci_hcd               34312  0 
ohci_hcd               20740  0 
usbcore               118396  3 ehci_hcd,ohci_hcd
ide_cd                 41732  0 
cdrom                  39904  1 ide_cd
ide_disk               18560  4 
ide_generic             1472  0 
sata_nv                 9412  0 
libata                 54020  1 sata_nv
scsi_mod              135944  1 libata
amd74xx                14044  1 
ide_core              139028  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   27248  362 
vesafb                  8088  0 
capability              4808  0 
commoncap               6912  1 capability
vga16fb                12680  1 
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72 
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon


```

im not sure what in dmesg..
```


[4294677.681000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.

```

---

### Post by claes on 2006-02-27
When the network fail try to: sudo modprobe forcedeth 
And try if sudo ifup eth0 works then.

If that's the case then the kernel module aka driver is unload from the kernel by some reason. Not sure how to fix that. 

Claes

---

### Post by chaosdx on 2006-02-27
[QUOTE=claes]When the network fail try to: sudo modprobe forcedeth 
And try if sudo ifup eth0 works then.

If that's the case then the kernel module aka driver is unload from the kernel by some reason. Not sure how to fix that. 

Claes[/QUOTE]

yes, modprobe helped.. no idea either, very frustrating :evil:

---

### Post by jamesr on 2006-02-27
The answer was given in dmesg output , that idicated that the driver was called forcedeth.c

> forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.41.

And that Claes asked to you to do 
```
sudo modprobe forcedeth
```
and this loads the module
then
```
sudo ifup eth0
```
then activates eth0
another way would be ```
sudo dhclient 
``` and that get a lease as well. 

As to why the module is being removed, I, like claes, am not sure. My only thoughts currently if the module was unstable. It would be probably good to borrow an old nic and try that with and without disabling the on-board nic.
The module is part of the nvidia set whether the new set includes a new nic driver I am not sure.

---

