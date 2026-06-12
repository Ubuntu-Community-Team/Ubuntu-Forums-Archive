---
title: "network-manager gone!!!"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by jonathandines on 2011-03-06
I do not have access in my laptop with ubuntu 10.10 maverick 64bit installed.
I deleted network manager when trying to set up a static I.P follow 
the guid on this page []("http://%3Ca%20href=%22http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-add%22%20target=%22_blank%22%3Ewww.liberiangeek.net/2010/09/setup-permanent-static-ip-add%3C/a%3E")[www.liberiangeek.net/2010/09/setup-permanent-static-ip-add]("http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-add")

I've googled around. The methods suggested to solve it have not been useful in my case.

I tried to the method by a user on this forum

> **lswb said:**
> Method 1) Start synaptic, click on  Settings/repositories follow instructions to install from live CD. After  installation click "reload" in synaptic and install upgrades if  applicable.

Method 2, if you have a wired ethernet connection, interface name is  eth0, using dhcp, which is the most common scenario, open a terminal and  type these commands:

sudo ifconfig eth0 up
sudo dhclient eth0

If you have wireless it's a little more complicated, but if you have an  unsecured network (no WEP or WPA) and your wireless interface name is  say eth1, and your wifi network essid (name) is "mynetwork" it wo
uld be something like this:

sudo ifconfig eth1 down
sudo iwconfig eth1 mode managed essid "mynetwork"
sudo ifconfig eth1 up
sudo dhclient eth1

It was unsuccessful. Please if some one can help me I'd be forever greatfull

---

### Post by taylorchase on 2011-03-06
Did you delete the network manager or did you just remove the applet from the panel? You can always add it back to the panel by right-clicking the panel-->Add to Panel...-->Notification Area

---

### Post by jonathandines on 2011-03-06
I used this command in terminal

sudo apt-get purge network-manager network-manager-gnome

I did the 2nd method of the guide to set up a static i.p according to that website. 
The link is in thread post.

---

### Post by runeh76 on 2011-03-06
OMG! Static IP  lol!!

Install ur network-manager back.

---

### Post by gnusci on 2011-03-06
please read this post first and then post back....

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

BTW: Do you really have static IP?

---

### Post by jonathandines on 2011-03-06
> **gnusci said:**
> please read this post first and then post back....

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

BTW: Do you really have static IP?

I don't have a static IP. I wanted to set one up some i can samba to my nintendo wii.

heres more info. quite long

 COMPAQ Presario CQ56-106SA

```
jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

 jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05c8:0213 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:54:32:d1  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:190880 (190.8 KB)  TX bytes:190880 (190.8 KB)

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ iwconfig wlan0
wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4657  0 
nls_cp437               6375  0 
vfat                   10954  0 
fat                    56244  1 vfat
usb_storage            50436  0 
nls_utf8                1453  1 
isofs                  34218  1 
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
vboxnetadp              5764  0 
vboxnetflt             19131  0 
vboxdrv              1817384  2 vboxnetadp,vboxnetflt
joydev                 11395  0 
snd_hda_codec_realtek   300173  1 
snd_hda_intel          26147  2 
snd_hda_codec         100951  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
i915                  334721  4 
uvcvideo               62379  0 
snd_seq_midi            5932  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
snd_rawmidi            22207  1 snd_seq_midi
v4l2_compat_ioctl32    12614  1 videodev
drm_kms_helper         32836  1 i915
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
r8192se_pci           512896  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  6467  0 
drm                   206198  4 i915,drm_kms_helper
psmouse                62080  0 
cfg80211              170485  1 r8192se_pci
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            6208  1 i915
serio_raw               4910  0 
video                  22176  1 i915
intel_agp              32334  2 i915
output                  2527  1 video
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22210  3 
libahci                26148  1 ahci
r8169                  42254  0 
mii                     5261  1 r8169


[    0.258379] AppArmor: AppArmor Filesystem Enabled
[    0.258401] pnp: PnP ACPI init
[    0.258422] ACPI: bus type pnp registered
[    0.261041] pnp: PnP ACPI: found 10 devices
[    0.261044] ACPI: ACPI bus type pnp unregistered
[    0.261056] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.261062] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.261065] system 00:02: [io  0x0600-0x060f] has been reserved
[    0.261067] system 00:02: [io  0x0610] has been reserved
[    0.261070] system 00:02: [io  0x0800-0x080f] has been reserved
[    0.261072] system 00:02: [io  0x0810-0x0817] has been reserved
[    0.261074] system 00:02: [io  0x0820-0x0823] has been reserved
[    0.261077] system 00:02: [io  0x0400-0x047f] has been reserved
[    0.261079] system 00:02: [io  0x0500-0x053f] has been reserved
[    0.261081] system 00:02: [io  0x0380-0x0387] has been reserved
[    0.261084] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.261087] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.261089] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.261092] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.261094] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.261100] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.261103] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.261105] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.261108] system 00:02: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.261110] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.266905] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.266939] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.266942] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.266947] pci 0000:00:1c.0:   bridge window [mem 0xd3500000-0xd44fffff]
[    0.266952] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.266961] pci 0000:03:00.0: BAR 6: assigned [mem 0xd1420000-0xd142ffff pref]
[    0.266963] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.266966] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.266971] pci 0000:00:1c.1:   bridge window [mem 0xd2500000-0xd34fffff]
[    0.266975] pci 0000:00:1c.1:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.266981] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.266983] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.266988] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.266991] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.267007]   alloc irq_desc for 17 on node -1
[    0.267009]   alloc kstat_irqs on node -1
[    0.267015] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.267019] pci 0000:00:1c.0: setting latency timer to 64
[    0.267027]   alloc irq_desc for 16 on node -1
[    0.267029]   alloc kstat_irqs on node -1
[    0.267032] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.267036] pci 0000:00:1c.1: setting latency timer to 64
[    0.267042] pci 0000:00:1e.0: setting latency timer to 64
[    0.267047] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.267049] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.267051] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.267053] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.267055] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.267057] pci_bus 0000:02: resource 1 [mem 0xd3500000-0xd44fffff]
[    0.267059] pci_bus 0000:02: resource 2 [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.267061] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.267063] pci_bus 0000:03: resource 1 [mem 0xd2500000-0xd34fffff]
[    0.267065] pci_bus 0000:03: resource 2 [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.267067] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.267069] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.267071] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.267073] pci_bus 0000:04: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.267105] NET: Registered protocol family 2
[    0.267234] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.268386] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.273219] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.273804] TCP: Hash tables configured (established 524288 bind 65536)
[    0.273807] TCP reno registered
[    0.273828] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.273871] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.274039] NET: Registered protocol family 1
[    0.274060] pci 0000:00:02.0: Boot video device
[    0.310002] PCI: CLS 64 bytes, default 64
[    0.310084] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.310086] Simple Boot Flag at 0x44 set to 0x1
[    0.310219] Scanning for low memory corruption every 60 seconds
[    0.310367] audit: initializing netlink socket (disabled)
[    0.310378] type=2000 audit(1299444481.299:1): initialized
[    0.323954] Trying to unpack rootfs image as initramfs...
[    0.340434] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.350183] VFS: Disk quotas dquot_6.5.2
[    0.350269] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.350787] fuse init (API version 7.14)
[    0.350864] msgmni has been set to 5873
[    0.563463] Freeing initrd memory: 10756k freed
[    0.570650] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.570654] io scheduler noop registered
[    0.570655] io scheduler deadline registered
[    0.570687] io scheduler cfq registered (default)
[    0.570779] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.570820]   alloc irq_desc for 40 on node -1
[    0.570822]   alloc kstat_irqs on node -1
[    0.570834] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.570923] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.570961]   alloc irq_desc for 41 on node -1
[    0.570962]   alloc kstat_irqs on node -1
[    0.570970] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.571062] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.571083] Firmware did not grant requested _OSC control
[    0.571092] Firmware did not grant requested _OSC control
[    0.571112] Firmware did not grant requested _OSC control
[    0.571121] Firmware did not grant requested _OSC control
[    0.571127] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.571191] intel_idle: MWAIT substates: 0x2220
[    0.571193] intel_idle: does not run on family 6 model 23
[    0.572433] ACPI: AC Adapter [ACAD] (off-line)
[    0.572513] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.572518] ACPI: Power Button [PWRB]
[    0.572555] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.572981] ACPI: Lid Switch [LID0]
[    0.573029] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.573032] ACPI: Power Button [PWRF]
[    0.573412] ACPI: acpi_idle registered with cpuidle
[    0.573648] Monitor-Mwait will be used to enter C-1 state
[    0.573671] Monitor-Mwait will be used to enter C-2 state
[    0.573689] Monitor-Mwait will be used to enter C-3 state
[    0.573694] Marking TSC unstable due to TSC halts in idle
[    0.574028] Switching to clocksource hpet
[    0.579048] [Firmware Bug]: Invalid critical threshold (0)
[    0.580757] thermal LNXTHERM:01: registered as thermal_zone0
[    0.580764] ACPI: Thermal Zone [TZ01] (23 C)
[    0.580858] ERST: Table is not found!
[    0.581522] Linux agpgart interface v0.103
[    0.581540] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.583836] brd: module loaded
[    0.584397] loop: module loaded
[    0.584797] Fixed MDIO Bus: probed
[    0.584822] PPP generic driver version 2.4.2
[    0.584854] tun: Universal TUN/TAP device driver, 1.6
[    0.584856] tun: (C) 1999-2004 Max Krasnyansky <[EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL]>
[    0.584924] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.584947]   alloc irq_desc for 19 on node -1
[    0.584949]   alloc kstat_irqs on node -1
[    0.584956] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.584975] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.584979] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.585016] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.585050] ehci_hcd 0000:00:1a.7: debug port 1
[    0.588945] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.588961] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd4505c00
[    0.610013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.610120] hub 1-0:1.0: USB hub found
[    0.610125] hub 1-0:1.0: 4 ports detected
[    0.610182]   alloc irq_desc for 20 on node -1
[    0.610184]   alloc kstat_irqs on node -1
[    0.610189] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.610204] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.610207] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.610241] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.610268] ehci_hcd 0000:00:1d.7: debug port 1
[    0.614153] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.614166] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd4505800
[    0.630017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.630111] hub 2-0:1.0: USB hub found
[    0.630115] hub 2-0:1.0: 8 ports detected
[    0.630177] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.630188] uhci_hcd: USB Universal Host Controller Interface driver
[    0.630244] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.630251] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.630254] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.630286] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.630320] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000040e0
[    0.630419] hub 3-0:1.0: USB hub found
[    0.630423] hub 3-0:1.0: 2 ports detected
[    0.630472]   alloc irq_desc for 21 on node -1
[    0.630474]   alloc kstat_irqs on node -1
[    0.630478] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.630484] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.630487] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.630514] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.630546] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000040c0
[    0.630644] hub 4-0:1.0: USB hub found
[    0.630648] hub 4-0:1.0: 2 ports detected
[    0.630693] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.630699] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.630703] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.630732] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.630761] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000040a0
[    0.630859] hub 5-0:1.0: USB hub found
[    0.630863] hub 5-0:1.0: 2 ports detected
[    0.630908] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.630914] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.630917] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.630960] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.630985] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004080
[    0.631079] hub 6-0:1.0: USB hub found
[    0.631082] hub 6-0:1.0: 2 ports detected
[    0.631131] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.631136] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.631140] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.631169] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.631193] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00004060
[    0.631290] hub 7-0:1.0: USB hub found
[    0.631294] hub 7-0:1.0: 2 ports detected
[    0.631343]   alloc irq_desc for 18 on node -1
[    0.631345]   alloc kstat_irqs on node -1
[    0.631349] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.631354] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.631358] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.631384] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.631417] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00004040
[    0.631513] hub 8-0:1.0: USB hub found
[    0.631517] hub 8-0:1.0: 2 ports detected
[    0.631611] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    0.646046] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.646054] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.646147] mice: PS/2 mouse device common for all mice
[    0.647619] rtc_cmos 00:04: RTC can wake from S4
[    0.647654] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.647681] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.647771] device-mapper: uevent: version 1.0.3
[    0.647844] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.647885] device-mapper: multipath: version 1.1.1 loaded
[    0.647887] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.648023] cpuidle: using governor ladder
[    0.648062] cpuidle: using governor menu
[    0.648275] TCP cubic registered
[    0.648379] NET: Registered protocol family 10
[    0.648667] lo: Disabled Privacy Extensions
[    0.648812] NET: Registered protocol family 17
[    0.648928] PM: Resume from disk failed.
[    0.648941] registered taskstats version 1
[    0.649231]   Magic number: 3:341:851
[    0.649333] rtc_cmos 00:04: setting system clock to 2011-03-06 20:48:02 UTC (1299444482)
[    0.649336] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.649337] EDD information not available.
[    0.649423] Freeing unused kernel memory: 912k freed
[    0.649685] Write protecting the kernel read-only data: 10240k
[    0.649851] Freeing unused kernel memory: 408k freed
[    0.650610] Freeing unused kernel memory: 1644k freed
[    0.655735] ACPI: Battery Slot [BAT0] (battery present)
[    0.668548] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.672588] udev[66]: starting version 163
[    0.745183] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.745208] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.745247] r8169 0000:03:00.0: setting latency timer to 64
[    0.745295]   alloc irq_desc for 42 on node -1
[    0.745296]   alloc kstat_irqs on node -1
[    0.745311] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    0.745690] r8169 0000:03:00.0: eth0: RTL8102e at 0xffffc9000067e000, 60:eb:69:54:32:d1, XID 04e00000 IRQ 42
[    0.807892] ahci 0000:00:1f.2: version 3.0
[    0.807912] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.807951]   alloc irq_desc for 43 on node -1
[    0.807953]   alloc kstat_irqs on node -1
[    0.807964] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    0.808009] ahci: SSS flag set, parallel bus scan disabled
[    0.808041] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.808045] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
[    0.808050] ahci 0000:00:1f.2: setting latency timer to 64
[    0.940095] scsi0 : ahci
[    0.940262] scsi1 : ahci
[    0.940360] scsi2 : ahci
[    0.940449] scsi3 : ahci
[    0.940536] scsi4 : ahci
[    0.940623] scsi5 : ahci
[    0.940817] ata1: SATA max UDMA/133 abar m2048@0xd4505000 port 0xd4505100 irq 43
[    0.940821] ata2: SATA max UDMA/133 abar m2048@0xd4505000 port 0xd4505180 irq 43
[    0.940823] ata3: DUMMY
[    0.940824] ata4: DUMMY
[    0.940826] ata5: SATA max UDMA/133 abar m2048@0xd4505000 port 0xd4505300 irq 43
[    0.940829] ata6: SATA max UDMA/133 abar m2048@0xd4505000 port 0xd4505380 irq 43
[    0.950039] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.490034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.495801] ata1.00: ATA-8: SAMSUNG HM321HI, 2AJ10001, max UDMA/133
[    1.495804] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.501572] ata1.00: configured for UDMA/133
[    1.520121] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM321HI  2AJ1 PQ: 0 ANSI: 5
[    1.520254] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.520456] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.520504] sd 0:0:0:0: [sda] Write Protect is off
[    1.520507] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.520527] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.520901]  sda: sda1 sda2 < sda5 >
[    1.564639] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.470048] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.489207] ata2.00: ATAPI: hp      DVD RW AD-7586H, KH04, max UDMA/100
[    2.531920] ata2.00: configured for UDMA/100
[    2.629689] scsi 1:0:0:0: CD-ROM            hp       DVD RW AD-7586H  KH04 PQ: 0 ANSI: 5
[    2.781372] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.781375] Uniform CD-ROM driver Revision: 3.20
[    2.781467] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.781519] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.130053] ata5: SATA link down (SStatus 0 SControl 300)
[    3.500049] ata6: SATA link down (SStatus 0 SControl 300)
[    3.880009] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.236465] udev[357]: starting version 163
[   15.295355] Adding 8847356k swap on /dev/sda5.  Priority:-1 extents:1 across:8847356k 
[   15.328228] lp: driver loaded but no devices found
[   15.392466] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[   15.393219] agpgart-intel 0000:00:00.0: detected 65532K stolen memory, trimming to 32768K
[   15.654657] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   15.785960] cfg80211: Calling CRDA to update world regulatory domain
[   15.897935] input: HP WMI hotkeys as /devices/virtual/input/input4
[   15.905306] type=1400 audit(1299444497.745:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=647 comm="apparmor_parser"
[   15.905954] type=1400 audit(1299444497.745:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=647 comm="apparmor_parser"
[   15.906305] type=1400 audit(1299444497.745:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=647 comm="apparmor_parser"
[   15.929002] cfg80211: World regulatory domain updated:
[   15.929005]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.929008]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.929011]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.929013]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.929016]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.929018]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.933762] rtllib_crypt: registered algorithm 'NULL'
[   15.933766] rtllib_crypt: registered algorithm 'TKIP'
[   15.933767] rtllib_crypt: registered algorithm 'CCMP'
[   15.933769] rtllib_crypt: registered algorithm 'WEP'
[   15.933770] 
[   15.933771] Linux kernel driver for RTL8192 based WLAN cards
[   15.933772] Copyright (c) 2007-2008, Realsil Wlan Driver
[   15.933812] rtl819xSE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.933819] rtl819xSE 0000:02:00.0: setting latency timer to 64
[   15.936683] type=1400 audit(1299444497.775:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=669 comm="apparmor_parser"
[   15.937332] type=1400 audit(1299444497.775:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=669 comm="apparmor_parser"
[   15.937686] type=1400 audit(1299444497.775:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=669 comm="apparmor_parser"
[   15.955726] Memory mapped space start: 0xd3500000 
[   15.956350] GetPciBusInfo(): Find Device(10EC:8171)  bus=2 dev=0, func=0
[   15.957232] GetPciBridegInfo : Find Device(8086:2940)  bus=0 dev=28, func=0
[   15.957233] Pci Bridge Vendor is found index: 0
[   15.957235] Pci Bridge Vendor is 8086
[   15.977945] =========>dm_InitRateAdaptiveMask: bUseRAMask=0
[   16.018382] rtl8192: wireless switch is off
[   16.038476] [drm] Initialized drm 1.1.0 20060810
[   16.153729] Linux video capture interface: v2.00
[   16.175147] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.176677] r8169 0000:03:00.0: eth0: link down
[   16.177142] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.184414] uvcvideo: Found UVC 1.00 device HP Webcam-101 (05c8:0213)
[   16.193946] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.193951] i915 0000:00:02.0: setting latency timer to 64
[   16.203817] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input5
[   16.203866] usbcore: registered new interface driver uvcvideo
[   16.203868] USB Video Class driver (v0.1.0)
[   16.289024] [drm] detected 63M stolen memory, trimming to 32M
[   16.299089]   alloc irq_desc for 44 on node -1
[   16.299093]   alloc kstat_irqs on node -1
[   16.299103] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   16.299114] [drm] set up 32M of stolen space
[   16.299252] [drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
[   16.299301] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000
[   16.482325] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.880461] Skipping EDID probe due to cached edid
[   17.224266] Console: switching to colour frame buffer device 170x48
[   17.226950] fb0: inteldrmfb frame buffer device
[   17.226951] drm: registered panic notifier
[   17.245694] Slow work thread pool: Starting up
[   17.266110] Slow work thread pool: Ready
[   17.278224] ACPI Error (dswload-0802): [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS
[   17.278231] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20100428/psloop-231)
[   17.278235] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.OVGA.DD03.GBQC] (Node ffff8800b7e3fbc0), AE_ALREADY_EXISTS
[   17.278248] ACPI: Marking method GBQC as Serialized because of AE_ALREADY_EXISTS error
[   17.278284] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.OVGA.DD03._BQC] (Node ffff8800b7e3fba0), AE_ALREADY_EXISTS
[   17.278295] ACPI: Marking method _BQC as Serialized because of AE_ALREADY_EXISTS error
[   17.278336] ACPI Warning: Evaluating _BQC failed (20100428/video-651)
[   17.293726] acpi device:02: registered as cooling_device1
[   17.295097] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   17.295250] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   17.295902] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.295947]   alloc irq_desc for 22 on node -1
[   17.295950]   alloc kstat_irqs on node -1
[   17.295959] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.296012]   alloc irq_desc for 45 on node -1
[   17.296014]   alloc kstat_irqs on node -1
[   17.296024] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.296052] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.351711] type=1400 audit(1299444499.195:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=941 comm="apparmor_parser"
[   17.362509] Skipping EDID probe due to cached edid
[   17.371574] type=1400 audit(1299444499.215:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=945 comm="apparmor_parser"
[   17.372225] type=1400 audit(1299444499.215:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=945 comm="apparmor_parser"
[   17.372584] type=1400 audit(1299444499.215:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=945 comm="apparmor_parser"
[   17.449646] hda_codec: ALC259: BIOS auto-probing.
[   17.534264] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xe40000/0xa0400
[   17.614499] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   17.870155] Skipping EDID probe due to cached edid
[   17.920117] Skipping EDID probe due to cached edid
[   18.041768] vboxdrv: Found 1 processor cores.
[   18.042577] VBoxDrv: dbg - g_abExecMemory=ffffffffa031b5e0
[   18.043511] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   18.043514] vboxdrv: Successfully loaded version 4.0.4 (interface 0x00160000).
[   18.970963] Skipping EDID probe due to cached edid
[   19.030047] Skipping EDID probe due to cached edid
[   19.080035] Skipping EDID probe due to cached edid
[   19.130219] Skipping EDID probe due to cached edid
[   20.420112] Skipping EDID probe due to cached edid
[   21.390043] Skipping EDID probe due to cached edid
[   22.866378] audit_printk_skb: 18 callbacks suppressed
[   22.866381] type=1400 audit(1299444504.705:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1539 comm="apparmor_parser"
[   22.867179] type=1400 audit(1299444504.705:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1539 comm="apparmor_parser"
[   23.017630] ppdev: user-space parallel port driver
[   25.590063] Skipping EDID probe due to cached edid
[   25.746256] ISO 9660 Extensions: Microsoft Joliet Level 3
[   25.797951] ISO 9660 Extensions: RRIP_1991A
[   25.807785] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  120.352915] HP WMI: Unknown key pressed - 3
[  121.090277] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  121.135368] ===>rtllib_wx_set_power(): power disable
[  121.200076] ata1: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
[  121.200080] ata1: irq_stat 0x00400000, PHY RDY changed
[  121.200084] ata1: SError: { PHYRdyChg CommWake }
[  121.200089] ata1: hard resetting link
[  122.150064] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  122.162735] ata1.00: configured for UDMA/133
[  122.162741] ata1: EH complete
[  669.853203] r8169 0000:03:00.0: eth0: link down
[  669.853966] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  767.645219] r8169 0000:03:00.0: eth0: link down
[  767.645977] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1403.390081] Skipping EDID probe due to cached edid
[ 1565.780059] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 1568.185439] Initializing USB Mass Storage driver...
[ 1568.185554] scsi6 : usb-storage 1-3:1.0
[ 1568.185689] usbcore: registered new interface driver usb-storage
[ 1568.185691] USB Mass Storage support registered.
[ 1569.181571] scsi 6:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[ 1569.183740] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1569.189153] sd 6:0:0:0: [sdb] 3915776 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 1569.190320] sd 6:0:0:0: [sdb] Write Protect is off
[ 1569.190324] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1569.190327] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1569.195166] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1569.195172]  sdb: sdb1
[ 1569.198159] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1569.198164] sd 6:0:0:0: [sdb] Attached SCSI removable disk

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ sudo lshw -C network
[sudo] password for jonathan: 
  *-network DISABLED      
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:45:99:2e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=0 latency=0 link=no multicast=yes wireless=802.11bg
       resources: irq:16 ioport:3000(size=256) memory:d3500000-d3503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:54:32:d1
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.0.13 latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

vboxnet0  Interface doesn't support scanning.

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ lsb_release -d
Description:    Ubuntu 10.10

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ uname -mr
2.6.35-27-generic x86_64

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...      


jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

 jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05c8:0213 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:54:32:d1  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:190880 (190.8 KB)  TX bytes:190880 (190.8 KB)

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ iwconfig wlan0
wlan0     802.11bg  Nickname:"rtl8191SEVA2"
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4657  0 
nls_cp437               6375  0 
vfat                   10954  0 
fat                    56244  1 vfat
usb_storage            50436  0 
nls_utf8                1453  1 
isofs                  34218  1 
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
vboxnetadp              5764  0 
vboxnetflt             19131  0 
vboxdrv              1817384  2 vboxnetadp,vboxnetflt
joydev                 11395  0 
snd_hda_codec_realtek   300173  1 
snd_hda_intel          26147  2 
snd_hda_codec         100951  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
i915                  334721  4 
uvcvideo               62379  0 
snd_seq_midi            5932  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
snd_rawmidi            22207  1 snd_seq_midi
v4l2_compat_ioctl32    12614  1 videodev
drm_kms_helper         32836  1 i915
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
r8192se_pci           512896  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  6467  0 
drm                   206198  4 i915,drm_kms_helper
psmouse                62080  0 
cfg80211              170485  1 r8192se_pci
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            6208  1 i915
serio_raw               4910  0 
video                  22176  1 i915
intel_agp              32334  2 i915
output                  2527  1 video
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22210  3 
libahci                26148  1 ahci
r8169                  42254  0 
mii                     5261  1 r8169


[    0.258379] AppArmor: AppArmor Filesystem Enabled
[    0.258401] pnp: PnP ACPI init
[    0.258422] ACPI: bus type pnp registered
[    0.261041] pnp: PnP ACPI: found 10 devices
[    0.261044] ACPI: ACPI bus type pnp unregistered
[    0.261056] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.261062] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.261065] system 00:02: [io  0x0600-0x060f] has been reserved
[    0.261067] system 00:02: [io  0x0610] has been reserved
[    0.261070] system 00:02: [io  0x0800-0x080f] has been reserved
[    0.261072] system 00:02: [io  0x0810-0x0817] has been reserved
[    0.261074] system 00:02: [io  0x0820-0x0823] has been reserved
[    0.261077] system 00:02: [io  0x0400-0x047f] has been reserved
[    0.261079] system 00:02: [io  0x0500-0x053f] has been reserved
[    0.261081] system 00:02: [io  0x0380-0x0387] has been reserved
[    0.261084] system 00:02: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.261087] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.261089] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.261092] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.261094] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.261100] system 00:02: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.261103] system 00:02: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.261105] system 00:02: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.261108] system 00:02: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.261110] system 00:02: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.266905] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.266939] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.266942] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.266947] pci 0000:00:1c.0:   bridge window [mem 0xd3500000-0xd44fffff]
[    0.266952] pci 0000:00:1c.0:   bridge window [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.266961] pci 0000:03:00.0: BAR 6: assigned [mem 0xd1420000-0xd142ffff pref]
[    0.266963] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.266966] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.266971] pci 0000:00:1c.1:   bridge window [mem 0xd2500000-0xd34fffff]
[    0.266975] pci 0000:00:1c.1:   bridge window [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.266981] pci 0000:00:1e.0: PCI bridge to [bus 04-04]
[    0.266983] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.266988] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.266991] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.267007]   alloc irq_desc for 17 on node -1
[    0.267009]   alloc kstat_irqs on node -1
[    0.267015] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.267019] pci 0000:00:1c.0: setting latency timer to 64
[    0.267027]   alloc irq_desc for 16 on node -1
[    0.267029]   alloc kstat_irqs on node -1
[    0.267032] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.267036] pci 0000:00:1c.1: setting latency timer to 64
[    0.267042] pci 0000:00:1e.0: setting latency timer to 64
[    0.267047] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.267049] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.267051] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.267053] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.267055] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.267057] pci_bus 0000:02: resource 1 [mem 0xd3500000-0xd44fffff]
[    0.267059] pci_bus 0000:02: resource 2 [mem 0xd0400000-0xd13fffff 64bit pref]
[    0.267061] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.267063] pci_bus 0000:03: resource 1 [mem 0xd2500000-0xd34fffff]
[    0.267065] pci_bus 0000:03: resource 2 [mem 0xd1400000-0xd23fffff 64bit pref]
[    0.267067] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.267069] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.267071] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.267073] pci_bus 0000:04: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.267105] NET: Registered protocol family 2
[    0.267234] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.268386] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.273219] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.273804] TCP: Hash tables configured (established 524288 bind 65536)
[    0.273807] TCP reno registered
[    0.273828] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.273871] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.274039] NET: Registered protocol family 1
[    0.274060] pci 0000:00:02.0: Boot video device
[    0.310002] PCI: CLS 64 bytes, default 64
[    0.310084] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.310086] Simple Boot Flag at 0x44 set to 0x1
[    0.310219] Scanning for low memory corruption every 60 seconds
[    0.310367] audit: initializing netlink socket (disabled)
[    0.310378] type=2000 audit(1299444481.299:1): initialized
[    0.323954] Trying to unpack rootfs image as initramfs...
[    0.340434] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.350183] VFS: Disk quotas dquot_6.5.2
[    0.350269] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.350787] fuse init (API version 7.14)
[    0.350864] msgmni has been set to 5873
[    0.563463] Freeing initrd memory: 10756k freed
[    0.570650] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.570654] io scheduler noop registered
[    0.570655] io scheduler deadline registered
[    0.570687] io scheduler cfq registered (default)
[    0.570779] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.570820]   alloc irq_desc for 40 on node -1
[    0.570822]   alloc kstat_irqs on node -1
[    0.570834] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.570923] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.570961]   alloc irq_desc for 41 on node -1
[    0.570962]   alloc kstat_irqs on node -1
[    0.570970] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.571062] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.571083] Firmware did not grant requested _OSC control
[    0.571092] Firmware did not grant requested _OSC control
[    0.571112] Firmware did not grant requested _OSC control
[    0.571121] Firmware did not grant requested _OSC control
[    0.571127] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.571191] intel_idle: MWAIT substates: 0x2220
[    0.571193] intel_idle: does not run on family 6 model 23
[    0.572433] ACPI: AC Adapter [ACAD] (off-line)
[    0.572513] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.572518] ACPI: Power Button [PWRB]
[    0.572555] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.572981] ACPI: Lid Switch [LID0]
[    0.573029] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.573032] ACPI: Power Button [PWRF]
[    0.573412] ACPI: acpi_idle registered with cpuidle
[    0.573648] Monitor-Mwait will be used to enter C-1 state
[    0.573671] Monitor-Mwait will be used to enter C-2 state
[    0.573689] Monitor-Mwait will be used to enter C-3 state
[    0.573694] Marking TSC unstable due to TSC halts in idle
[    0.574028] Switching to clocksource hpet
[    0.579048] [Firmware Bug]: Invalid critical threshold (0)
[    0.580757] thermal LNXTHERM:01: registered as thermal_zone0
[    0.580764] ACPI: Thermal Zone [TZ01] (23 C)
[    0.580858] ERST: Table is not found!
[    0.581522] Linux agpgart interface v0.103
[    0.581540] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.583836] brd: module loaded
[    0.584397] loop: module loaded
[    0.584797] Fixed MDIO Bus: probed
[    0.584822] PPP generic driver version 2.4.2
[    0.584854] tun: Universal TUN/TAP device driver, 1.6
[    0.584856] tun: (C) 1999-2004 Max Krasnyansky <[EMAIL="maxk@qualcomm.com"]maxk@qualcomm.com[/EMAIL]>
[    0.584924] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.584947]   alloc irq_desc for 19 on node -1
[    0.584949]   alloc kstat_irqs on node -1
[    0.584956] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.584975] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.584979] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.585016] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.585050] ehci_hcd 0000:00:1a.7: debug port 1
[    0.588945] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.588961] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd4505c00
[    0.610013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.610120] hub 1-0:1.0: USB hub found
[    0.610125] hub 1-0:1.0: 4 ports detected
[    0.610182]   alloc irq_desc for 20 on node -1
[    0.610184]   alloc kstat_irqs on node -1
[    0.610189] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.610204] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.610207] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.610241] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.610268] ehci_hcd 0000:00:1d.7: debug port 1
[    0.614153] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.614166] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd4505800
[    0.630017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.630111] hub 2-0:1.0: USB hub found
[    0.630115] hub 2-0:1.0: 8 ports detected
[    0.630177] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.630188] uhci_hcd: USB Universal Host Controller Interface driver
[    0.630244] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.630251] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.630254] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.630286] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.630320] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000040e0
[    0.630419] hub 3-0:1.0: USB hub found
[    0.630423] hub 3-0:1.0: 2 ports detected
[    0.630472]   alloc irq_desc for 21 on node -1
[    0.630474]   alloc kstat_irqs on node -1
[    0.630478] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.630484] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.630487] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.630514] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.630546] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000040c0
[    0.630644] hub 4-0:1.0: USB hub found
[    0.630648] hub 4-0:1.0: 2 ports detected
[    0.630693] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.630699] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.630703] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.630732] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.630761] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000040a0
[    0.630859] hub 5-0:1.0: USB hub found
[    0.630863] hub 5-0:1.0: 2 ports detected
[    0.630908] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.630914] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.630917] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.630960] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.630985] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00004080
[    0.631079] hub 6-0:1.0: USB hub found
[    0.631082] hub 6-0:1.0: 2 ports detected
[    0.631131] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.631136] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.631140] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.631169] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.631193] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00004060
[    0.631290] hub 7-0:1.0: USB hub found
[    0.631294] hub 7-0:1.0: 2 ports detected
[    0.631343]   alloc irq_desc for 18 on node -1
[    0.631345]   alloc kstat_irqs on node -1
[    0.631349] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.631354] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.631358] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.631384] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.631417] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00004040
[    0.631513] hub 8-0:1.0: USB hub found
[    0.631517] hub 8-0:1.0: 2 ports detected
[    0.631611] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    0.646046] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.646054] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.646147] mice: PS/2 mouse device common for all mice
[    0.647619] rtc_cmos 00:04: RTC can wake from S4
[    0.647654] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.647681] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.647771] device-mapper: uevent: version 1.0.3
[    0.647844] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.647885] device-mapper: multipath: version 1.1.1 loaded
[    0.647887] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.648023] cpuidle: using governor ladder
[    0.648062] cpuidle: using governor menu
[    0.648275] TCP cubic registered
[    0.648379] NET: Registered protocol family 10
[    0.648667] lo: Disabled Privacy Extensions
[    0.648812] NET: Registered protocol family 17
[    0.648928] PM: Resume from disk failed.
[    0.648941] registered taskstats version 1
[    0.649231]   Magic number: 3:341:851
[    0.649333] rtc_cmos 00:04: setting system clock to 2011-03-06 20:48:02 UTC (1299444482)
[    0.649336] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.649337] EDD information not available.
[    0.649423] Freeing unused kernel memory: 912k freed
[    0.649685] Write protecting the kernel read-only data: 10240k
[    0.649851] Freeing unused kernel memory: 408k freed
[    0.650610] Freeing unused kernel memory: 1644k freed
[    0.655735] ACPI: Battery Slot [BAT0] (battery present)
[    0.668548] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.672588] udev[66]: starting version 163
[    0.745183] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.745208] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.745247] r8169 0000:03:00.0: setting latency timer to 64
[    0.745295]   alloc irq_desc for 42 on node -1
[    0.745296]   alloc kstat_irqs on node -1
[    0.745311] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    0.745690] r8169 0000:03:00.0: eth0: RTL8102e at 0xffffc9000067e000, 60:eb:69:54:32:d1, XID 04e00000 IRQ 42
[    0.807892] ahci 0000:00:1f.2: version 3.0
[    0.807912] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.807951]   alloc irq_desc for 43 on node -1
[    0.807953]   alloc kstat_irqs on node -1
[    0.807964] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    0.808009] ahci: SSS flag set, parallel bus scan disabled
[    0.808041] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.808045] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
[    0.808050] ahci 0000:00:1f.2: setting latency timer to 64
[    0.940095] scsi0 : ahci
[    0.940262] scsi1 : ahci
[    0.940360] scsi2 : ahci
[    0.940449] scsi3 : ahci
[    0.940536] scsi4 : ahci
[    0.940623] scsi5 : ahci
[    0.940817] ata1: SATA max UDMA/133 abar m2048@0xd4505000 port 0xd4505100 irq 43
[    0.940821] ata2: SATA max UDMA/133 abar m2048@0xd4505000 port 0xd4505180 irq 43
[    0.940823] ata3: DUMMY
[    0.940824] ata4: DUMMY
[    0.940826] ata5: SATA max UDMA/133 abar m2048@0xd4505000 port 0xd4505300 irq 43
[    0.940829] ata6: SATA max UDMA/133 abar m2048@0xd4505000 port 0xd4505380 irq 43
[    0.950039] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.490034] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.495801] ata1.00: ATA-8: SAMSUNG HM321HI, 2AJ10001, max UDMA/133
[    1.495804] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.501572] ata1.00: configured for UDMA/133
[    1.520121] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM321HI  2AJ1 PQ: 0 ANSI: 5
[    1.520254] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.520456] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.520504] sd 0:0:0:0: [sda] Write Protect is off
[    1.520507] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.520527] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.520901]  sda: sda1 sda2 < sda5 >
[    1.564639] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.470048] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.489207] ata2.00: ATAPI: hp      DVD RW AD-7586H, KH04, max UDMA/100
[    2.531920] ata2.00: configured for UDMA/100
[    2.629689] scsi 1:0:0:0: CD-ROM            hp       DVD RW AD-7586H  KH04 PQ: 0 ANSI: 5
[    2.781372] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.781375] Uniform CD-ROM driver Revision: 3.20
[    2.781467] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.781519] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.130053] ata5: SATA link down (SStatus 0 SControl 300)
[    3.500049] ata6: SATA link down (SStatus 0 SControl 300)
[    3.880009] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.236465] udev[357]: starting version 163
[   15.295355] Adding 8847356k swap on /dev/sda5.  Priority:-1 extents:1 across:8847356k 
[   15.328228] lp: driver loaded but no devices found
[   15.392466] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
[   15.393219] agpgart-intel 0000:00:00.0: detected 65532K stolen memory, trimming to 32768K
[   15.654657] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   15.785960] cfg80211: Calling CRDA to update world regulatory domain
[   15.897935] input: HP WMI hotkeys as /devices/virtual/input/input4
[   15.905306] type=1400 audit(1299444497.745:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=647 comm="apparmor_parser"
[   15.905954] type=1400 audit(1299444497.745:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=647 comm="apparmor_parser"
[   15.906305] type=1400 audit(1299444497.745:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=647 comm="apparmor_parser"
[   15.929002] cfg80211: World regulatory domain updated:
[   15.929005]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.929008]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.929011]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.929013]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.929016]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.929018]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.933762] rtllib_crypt: registered algorithm 'NULL'
[   15.933766] rtllib_crypt: registered algorithm 'TKIP'
[   15.933767] rtllib_crypt: registered algorithm 'CCMP'
[   15.933769] rtllib_crypt: registered algorithm 'WEP'
[   15.933770] 
[   15.933771] Linux kernel driver for RTL8192 based WLAN cards
[   15.933772] Copyright (c) 2007-2008, Realsil Wlan Driver
[   15.933812] rtl819xSE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.933819] rtl819xSE 0000:02:00.0: setting latency timer to 64
[   15.936683] type=1400 audit(1299444497.775:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=669 comm="apparmor_parser"
[   15.937332] type=1400 audit(1299444497.775:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=669 comm="apparmor_parser"
[   15.937686] type=1400 audit(1299444497.775:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=669 comm="apparmor_parser"
[   15.955726] Memory mapped space start: 0xd3500000 
[   15.956350] GetPciBusInfo(): Find Device(10EC:8171)  bus=2 dev=0, func=0
[   15.957232] GetPciBridegInfo : Find Device(8086:2940)  bus=0 dev=28, func=0
[   15.957233] Pci Bridge Vendor is found index: 0
[   15.957235] Pci Bridge Vendor is 8086
[   15.977945] =========>dm_InitRateAdaptiveMask: bUseRAMask=0
[   16.018382] rtl8192: wireless switch is off
[   16.038476] [drm] Initialized drm 1.1.0 20060810
[   16.153729] Linux video capture interface: v2.00
[   16.175147] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.176677] r8169 0000:03:00.0: eth0: link down
[   16.177142] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.184414] uvcvideo: Found UVC 1.00 device HP Webcam-101 (05c8:0213)
[   16.193946] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.193951] i915 0000:00:02.0: setting latency timer to 64
[   16.203817] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input5
[   16.203866] usbcore: registered new interface driver uvcvideo
[   16.203868] USB Video Class driver (v0.1.0)
[   16.289024] [drm] detected 63M stolen memory, trimming to 32M
[   16.299089]   alloc irq_desc for 44 on node -1
[   16.299093]   alloc kstat_irqs on node -1
[   16.299103] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   16.299114] [drm] set up 32M of stolen space
[   16.299252] [drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
[   16.299301] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000
[   16.482325] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.880461] Skipping EDID probe due to cached edid
[   17.224266] Console: switching to colour frame buffer device 170x48
[   17.226950] fb0: inteldrmfb frame buffer device
[   17.226951] drm: registered panic notifier
[   17.245694] Slow work thread pool: Starting up
[   17.266110] Slow work thread pool: Ready
[   17.278224] ACPI Error (dswload-0802): [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS
[   17.278231] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20100428/psloop-231)
[   17.278235] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.OVGA.DD03.GBQC] (Node ffff8800b7e3fbc0), AE_ALREADY_EXISTS
[   17.278248] ACPI: Marking method GBQC as Serialized because of AE_ALREADY_EXISTS error
[   17.278284] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.OVGA.DD03._BQC] (Node ffff8800b7e3fba0), AE_ALREADY_EXISTS
[   17.278295] ACPI: Marking method _BQC as Serialized because of AE_ALREADY_EXISTS error
[   17.278336] ACPI Warning: Evaluating _BQC failed (20100428/video-651)
[   17.293726] acpi device:02: registered as cooling_device1
[   17.295097] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   17.295250] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   17.295902] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.295947]   alloc irq_desc for 22 on node -1
[   17.295950]   alloc kstat_irqs on node -1
[   17.295959] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.296012]   alloc irq_desc for 45 on node -1
[   17.296014]   alloc kstat_irqs on node -1
[   17.296024] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.296052] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.351711] type=1400 audit(1299444499.195:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=941 comm="apparmor_parser"
[   17.362509] Skipping EDID probe due to cached edid
[   17.371574] type=1400 audit(1299444499.215:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=945 comm="apparmor_parser"
[   17.372225] type=1400 audit(1299444499.215:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=945 comm="apparmor_parser"
[   17.372584] type=1400 audit(1299444499.215:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=945 comm="apparmor_parser"
[   17.449646] hda_codec: ALC259: BIOS auto-probing.
[   17.534264] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xe40000/0xa0400
[   17.614499] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   17.870155] Skipping EDID probe due to cached edid
[   17.920117] Skipping EDID probe due to cached edid
[   18.041768] vboxdrv: Found 1 processor cores.
[   18.042577] VBoxDrv: dbg - g_abExecMemory=ffffffffa031b5e0
[   18.043511] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   18.043514] vboxdrv: Successfully loaded version 4.0.4 (interface 0x00160000).
[   18.970963] Skipping EDID probe due to cached edid
[   19.030047] Skipping EDID probe due to cached edid
[   19.080035] Skipping EDID probe due to cached edid
[   19.130219] Skipping EDID probe due to cached edid
[   20.420112] Skipping EDID probe due to cached edid
[   21.390043] Skipping EDID probe due to cached edid
[   22.866378] audit_printk_skb: 18 callbacks suppressed
[   22.866381] type=1400 audit(1299444504.705:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1539 comm="apparmor_parser"
[   22.867179] type=1400 audit(1299444504.705:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1539 comm="apparmor_parser"
[   23.017630] ppdev: user-space parallel port driver
[   25.590063] Skipping EDID probe due to cached edid
[   25.746256] ISO 9660 Extensions: Microsoft Joliet Level 3
[   25.797951] ISO 9660 Extensions: RRIP_1991A
[   25.807785] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  120.352915] HP WMI: Unknown key pressed - 3
[  121.090277] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  121.135368] ===>rtllib_wx_set_power(): power disable
[  121.200076] ata1: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
[  121.200080] ata1: irq_stat 0x00400000, PHY RDY changed
[  121.200084] ata1: SError: { PHYRdyChg CommWake }
[  121.200089] ata1: hard resetting link
[  122.150064] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  122.162735] ata1.00: configured for UDMA/133
[  122.162741] ata1: EH complete
[  669.853203] r8169 0000:03:00.0: eth0: link down
[  669.853966] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  767.645219] r8169 0000:03:00.0: eth0: link down
[  767.645977] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1403.390081] Skipping EDID probe due to cached edid
[ 1565.780059] usb 1-3: new high speed USB device using ehci_hcd and address 2
[ 1568.185439] Initializing USB Mass Storage driver...
[ 1568.185554] scsi6 : usb-storage 1-3:1.0
[ 1568.185689] usbcore: registered new interface driver usb-storage
[ 1568.185691] USB Mass Storage support registered.
[ 1569.181571] scsi 6:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
[ 1569.183740] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1569.189153] sd 6:0:0:0: [sdb] 3915776 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 1569.190320] sd 6:0:0:0: [sdb] Write Protect is off
[ 1569.190324] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1569.190327] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1569.195166] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1569.195172]  sdb: sdb1
[ 1569.198159] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1569.198164] sd 6:0:0:0: [sdb] Attached SCSI removable disk

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ sudo lshw -C network
[sudo] password for jonathan: 
  *-network DISABLED      
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 1c:65:9d:45:99:2e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=0 latency=0 link=no multicast=yes wireless=802.11bg
       resources: irq:16 ioport:3000(size=256) memory:d3500000-d3503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:54:32:d1
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.0.13 latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

vboxnet0  Interface doesn't support scanning.

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ lsb_release -d
Description:    Ubuntu 10.10

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ uname -mr
2.6.35-27-generic x86_64

jonathan@jonathan-Presario-CQ56-Notebook-PC:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
```

---

### Post by jonathandines on 2011-03-07
bump

---

