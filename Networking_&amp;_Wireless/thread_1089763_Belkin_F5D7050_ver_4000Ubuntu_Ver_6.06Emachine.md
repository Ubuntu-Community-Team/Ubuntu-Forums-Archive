---
title: "Belkin F5D7050 ver 4000/Ubuntu Ver 6.06/Emachine"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by AverellTorrent on 2009-03-07
I've been trying to follow the various tutorials on here about this card, but since the ndiswrapper site is apparently down, and the provided alternative isn't working, I've been having some difficulty.

I've been trying to stick to this tutorial mostly, since it doesn't require ndiswrapper.  I couldn't follow the link in there for the driver, but I found it somewhere else.  I think it's the right one, but I'm not sure.
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29")

Could somebody help me verify that the driver I have is the right one?  Or give me a link to the right driver that isn't a broken link?

---

### Post by AverellTorrent on 2009-03-07
1. **eric@eric-desktop:~$ lsusb**
```
Bus 005 Device 053: ID 050d:705c Belkin Components
```

2. **eric@eric-desktop:~$ ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:13:20:23:07:BA
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe23:7ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:262824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:383055106 (365.3 MiB)  TX bytes:8707664 (8.3 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:33374 (32.5 KiB)  TX bytes:33374 (32.5 KiB)
```

3. **eric@eric-desktop:~$ iwconfig**
```
lo        no wireless extensions.
sit0      no wireless extensions.
eth0      no wireless extensions.
```

4. **eric@eric-desktop:~$ lsmod**
```
Module                  Size  Used by
jfs                   195780  0
xfs                   589656  0
exportfs                6272  1 xfs
reiserfs              268016  0
ext2                   68360  0
hfs                    50052  0
hfsplus                79108  0
ntfs                  103536  0
acpi_sbs               19980  0
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
button                  6672  0
e100                   40580  0
mii                     5888  1 e100
nls_utf8                2176  1
vfat                   13440  1
fat                    53020  1 vfat
nls_cp437               5888  1
isofs                  37688  0
udf                    88452  0
ipv6                  265728  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
sg                     37920  0
sd_mod                 19984  2
dm_mod                 58936  1
af_packet              22920  2
md_mod                 72532  0
lp                     11844  0
usb_storage            74176  1
tsdev                   8000  0
snd_usb_audio          79296  0
snd_usb_lib            16640  1 snd_usb_audio
snd_rawmidi            25504  1 snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
usbhid                 39904  0
snd_hwdep               9376  1 snd_usb_audio
parport_pc             35780  1
usblp                  13056  0
parport                36296  3 ppdev,lp,parport_pc
snd_intel8x0           33692  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
pcspkr                  2180  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
snd                    55268  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
agpgart                34888  3 drm,intel_agp
soundcore              10208  1 snd
psmouse                36100  0
serio_raw               7300  0
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
floppy                 62148  0
rtc                    13492  0
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  8 usb_storage,snd_usb_audio,snd_usb_lib,usbhid,usblp,ehci_hcd,uhci_hcd
ata_piix               11012  0
libata                 78992  1 ata_piix
scsi_mod              139496  4 sg,sd_mod,usb_storage,libata
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
piix                   11012  1
generic                 5124  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  73
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

5. **eric@eric-desktop:~$ dmesg**
```
[17205818.408000] NET: Registered protocol family 10
[17205818.408000] lo: Disabled Privacy Extensions
[17205818.408000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17205818.408000] IPv6 over IPv4 tunneling driver
[17220411.056000] ACPI: PCI interrupt for device 0000:01:08.0 disabled
[17220413.260000] Stopping tasks: ==============================================================================|
[17220413.264000] Shrinking memory... done (0 pages freed)
[17220413.280000] snd-usb-audio 2-2.2:1.2: no suspend for driver snd-usb-audio?
[17220413.280000] snd-usb-audio 2-2.2:1.1: no suspend for driver snd-usb-audio?
[17220413.280000] snd-usb-audio 2-2.2:1.0: no suspend for driver snd-usb-audio?
[17220413.348000] usblp 1-1:1.1: no suspend for driver usblp?
[17220413.512000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[17220413.512000] ata_piix 0000:00:1f.2: suspend PCI device
[17220413.512000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[17220413.512000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[17220413.528000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[17220413.528000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[17220413.528000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[17220413.528000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[17220413.528000] ............................swsusp: Need to copy 89947 pages
[17220413.528000] swsusp: Restoring Highmem
[17718991.088000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17718991.088000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177
[17718991.088000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17718991.088000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[17718991.088000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17718991.088000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[17718991.088000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17718991.088000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 177
[17718991.088000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17718991.104000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[17718991.104000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[17718991.104000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17718991.104000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17718991.104000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17718991.104000] ata_piix 0000:00:1f.2: resume PCI device
[17718991.104000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 169
[17718991.104000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17718991.104000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[17718991.104000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17718991.456000] usblp 1-1:1.1: no resume for driver usblp?
[17718991.644000] snd-usb-audio 2-2.2:1.0: no resume for driver snd-usb-audio?
[17718991.644000] snd-usb-audio 2-2.2:1.1: no resume for driver snd-usb-audio?
[17718991.644000] snd-usb-audio 2-2.2:1.2: no resume for driver snd-usb-audio?
[17718991.808000] Restarting tasks... done
[17718992.300000] usb 5-2: new high speed USB device using ehci_hcd and address 40
[17718992.560000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17718992.560000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17718992.884000] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[17718992.884000] hdc: drive_cmd: error=0x04 { AbortedCommand }
[17718992.884000] ide: failed opcode was: 0xec
[17718993.172000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17718993.172000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17718993.172000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17718993.232000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17718993.236000] e100: Copyright(c) 1999-2005 Intel Corporation
[17718993.236000] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[17718993.256000] e100: eth0: e100_probe: addr 0xff8ff000, irq 209, MAC addr 00:13:20:23:07:BA
[17718993.360000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17718993.636000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17718993.636000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17718993.984000] ACPI: Power Button (FF) [PWRF]
[17718993.984000] ACPI: Sleep Button (CM) [SLPB]
[17718994.568000] usb 5-2: new high speed USB device using ehci_hcd and address 43
[17718994.828000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17718994.828000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17718995.048000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17718995.440000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17718995.440000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17718995.440000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17718996.332000] usb 5-2: new high speed USB device using ehci_hcd and address 46
[17718997.844000] usb 5-2: new high speed USB device using ehci_hcd and address 51
[17718999.860000] usb 5-2: new high speed USB device using ehci_hcd and address 58
[17719000.120000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719000.120000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719000.732000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719000.732000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719000.732000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17719001.196000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719001.196000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719004.144000] usb 5-2: new high speed USB device using ehci_hcd and address 69
[17719004.404000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719004.404000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719005.016000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719005.016000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719005.016000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17719006.664000] usb 5-2: new high speed USB device using ehci_hcd and address 75
[17719007.420000] usb 5-2: new high speed USB device using ehci_hcd and address 77
[17719007.680000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719007.680000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719008.932000] usb 5-2: new high speed USB device using ehci_hcd and address 80
[17719011.200000] usb 5-2: new high speed USB device using ehci_hcd and address 88
[17719011.460000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719011.460000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719012.964000] usb 5-2: new high speed USB device using ehci_hcd and address 92
[17719013.720000] usb 5-2: new high speed USB device using ehci_hcd and address 94
[17719015.484000] usb 5-2: new high speed USB device using ehci_hcd and address 100
[17719015.988000] usb 5-2: new high speed USB device using ehci_hcd and address 101
[17719016.492000] usb 5-2: new high speed USB device using ehci_hcd and address 102
[17719016.752000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719016.752000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719017.500000] usb 5-2: new high speed USB device using ehci_hcd and address 103
[17719020.272000] usb 5-2: new high speed USB device using ehci_hcd and address 113
[17719023.044000] usb 5-2: new high speed USB device using ehci_hcd and address 123
[17719023.304000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719023.304000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719024.052000] usb 5-2: new high speed USB device using ehci_hcd and address 124
[17719024.556000] usb 5-2: new high speed USB device using ehci_hcd and address 125
[17719025.312000] usb 5-2: new high speed USB device using ehci_hcd and address 127
[17719025.816000] usb 5-2: new high speed USB device using ehci_hcd and address 2
[17719028.336000] usb 5-2: new high speed USB device using ehci_hcd and address 12
[17719029.092000] usb 5-2: new high speed USB device using ehci_hcd and address 14
[17719029.848000] usb 5-2: new high speed USB device using ehci_hcd and address 16
[17719030.352000] usb 5-2: new high speed USB device using ehci_hcd and address 17
[17719031.360000] usb 5-2: new high speed USB device using ehci_hcd and address 20
[17719031.864000] usb 5-2: new high speed USB device using ehci_hcd and address 21
[17719032.124000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719032.124000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719033.628000] usb 5-2: new high speed USB device using ehci_hcd and address 25
[17719035.140000] usb 5-2: new high speed USB device using ehci_hcd and address 30
[17719035.896000] usb 5-2: new high speed USB device using ehci_hcd and address 32
[17719036.904000] usb 5-2: new high speed USB device using ehci_hcd and address 35
[17719037.164000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719037.164000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719037.912000] usb 5-2: new high speed USB device using ehci_hcd and address 36
[17719039.928000] usb 5-2: new high speed USB device using ehci_hcd and address 43
[17719041.440000] usb 5-2: new high speed USB device using ehci_hcd and address 48
[17719041.944000] usb 5-2: new high speed USB device using ehci_hcd and address 49
[17719042.952000] usb 5-2: new high speed USB device using ehci_hcd and address 52
[17719043.456000] usb 5-2: new high speed USB device using ehci_hcd and address 53
[17719044.212000] usb 5-2: new high speed USB device using ehci_hcd and address 55
[17719045.220000] usb 5-2: new high speed USB device using ehci_hcd and address 58
[17719046.228000] usb 5-2: new high speed USB device using ehci_hcd and address 61
[17719048.244000] usb 5-2: new high speed USB device using ehci_hcd and address 68
[17719050.008000] usb 5-2: new high speed USB device using ehci_hcd and address 74
[17719051.520000] usb 5-2: new high speed USB device using ehci_hcd and address 79
[17719052.276000] usb 5-2: new high speed USB device using ehci_hcd and address 81
[17719053.284000] usb 5-2: new high speed USB device using ehci_hcd and address 84
[17719053.544000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719053.544000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719055.048000] usb 5-2: new high speed USB device using ehci_hcd and address 88
[17719056.560000] usb 5-2: new high speed USB device using ehci_hcd and address 93
[17719057.820000] usb 5-2: new high speed USB device using ehci_hcd and address 97
[17719058.324000] usb 5-2: new high speed USB device using ehci_hcd and address 98
[17719059.584000] usb 5-2: new high speed USB device using ehci_hcd and address 102
[17719060.592000] usb 5-2: new high speed USB device using ehci_hcd and address 105
[17719061.348000] usb 5-2: new high speed USB device using ehci_hcd and address 107
[17719062.608000] usb 5-2: new high speed USB device using ehci_hcd and address 111
[17719063.112000] usb 5-2: new high speed USB device using ehci_hcd and address 112
[17719063.616000] usb 5-2: new high speed USB device using ehci_hcd and address 113
[17719063.876000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719063.876000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719064.876000] usb 5-2: new high speed USB device using ehci_hcd and address 115
[17719066.388000] usb 5-2: new high speed USB device using ehci_hcd and address 120
[17719068.656000] usb 5-2: new high speed USB device using ehci_hcd and address 2
[17719069.664000] usb 5-2: new high speed USB device using ehci_hcd and address 6
[17719069.924000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17719069.924000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17719071.176000] usb 5-2: new high speed USB device using ehci_hcd and address 9
[17719072.688000] usb 5-2: new high speed USB device using ehci_hcd and address 14
[17719073.948000] usb 5-2: new high speed USB device using ehci_hcd and address 18
[17719074.956000] usb 5-2: new high speed USB device using ehci_hcd and address 21
[17719637.152000] cdrom: hdc: mrw address space DMA selected
[17719637.232000] cdrom: hdc: mrw address space DMA selected
[17719637.284000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17719637.340000] ISO 9660 Extensions: RRIP_1991A
[17724247.440000] cdrom: hdc: mrw address space DMA selected
[17724247.492000] cdrom: hdc: mrw address space DMA selected
[17724247.536000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17724247.560000] ISOFS: changing to secondary root
[17732961.920000] usb 5-8: new high speed USB device using ehci_hcd and address 22
[17732962.064000] scsi3 : SCSI emulation for USB Mass Storage devices
[17732962.064000] usb-storage: device found at 22
[17732962.064000] usb-storage: waiting for device to settle before scanning
[17732967.064000]   Vendor: Memorex   Model: TD 2C             Rev: 1.04
[17732967.064000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17732967.552000] SCSI device sde: 1003520 512-byte hdwr sectors (514 MB)
[17732967.552000] sde: Write Protect is off
[17732967.552000] sde: Mode Sense: 23 00 00 00
[17732967.552000] sde: assuming drive cache: write through
[17732967.552000] SCSI device sde: 1003520 512-byte hdwr sectors (514 MB)
[17732967.556000] sde: Write Protect is off
[17732967.556000] sde: Mode Sense: 23 00 00 00
[17732967.556000] sde: assuming drive cache: write through
[17732967.556000]  sde: sde1
[17732967.556000] sd 3:0:0:0: Attached scsi removable disk sde
[17732967.556000] sd 3:0:0:0: Attached scsi generic sg4 type 0
[17732967.556000] usb-storage: device scan complete
[17732968.528000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17736362.420000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17736438.424000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17736438.424000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17736448.972000] eth0: no IPv6 routers present
[17737241.096000] cdrom: open failed.
[17737241.124000] cdrom: open failed.
[17737370.424000] e100: eth0: e100_watchdog: link down
[17737406.424000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17740854.068000] usb 5-2: USB disconnect, address 21
[17743202.304000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17743202.308000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17743202.308000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17744668.280000] ACPI: PCI interrupt for device 0000:01:08.0 disabled
[17744670.980000] Stopping tasks: ============================================================================================|
[17744670.980000] Shrinking memory... done (141262 pages freed)
[17744671.352000] snd-usb-audio 2-2.2:1.2: no suspend for driver snd-usb-audio?
[17744671.352000] snd-usb-audio 2-2.2:1.1: no suspend for driver snd-usb-audio?
[17744671.352000] snd-usb-audio 2-2.2:1.0: no suspend for driver snd-usb-audio?
[17744671.416000] usblp 1-1:1.1: no suspend for driver usblp?
[17744671.616000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[17744671.616000] ata_piix 0000:00:1f.2: suspend PCI device
[17744671.616000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[17744671.616000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[17744671.632000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[17744671.632000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[17744671.632000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[17744671.632000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[17744671.632000] ............................swsusp: Need to copy 101116 pages
[17744671.632000] swsusp: Restoring Highmem
[17955005.892000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 177
[17955005.892000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 177
[17955005.892000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17955005.892000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 185
[17955005.892000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17955005.892000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 169
[17955005.892000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17955005.892000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 177
[17955005.892000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17955005.908000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[17955005.908000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[17955005.908000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17955005.908000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17955005.908000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 169
[17955005.908000] ata_piix 0000:00:1f.2: resume PCI device
[17955005.908000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 169
[17955005.908000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17955005.908000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 201
[17955005.908000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17955006.260000] usblp 1-1:1.1: no resume for driver usblp?
[17955006.448000] snd-usb-audio 2-2.2:1.0: no resume for driver snd-usb-audio?
[17955006.448000] snd-usb-audio 2-2.2:1.1: no resume for driver snd-usb-audio?
[17955006.448000] snd-usb-audio 2-2.2:1.2: no resume for driver snd-usb-audio?
[17955006.612000] Restarting tasks...<6>usb 5-3: USB disconnect, address 4
[17955006.624000] sde : READ CAPACITY failed.
[17955006.624000] sde : status=0, message=00, host=7, driver=00
[17955006.624000] sde : sense not available.
[17955006.624000] sde: Write Protect is off
[17955006.624000] sde: Mode Sense: 00 00 00 00
[17955006.624000] sde: assuming drive cache: write through
[17955006.636000]  done
[17955006.640000] sde : READ CAPACITY failed.
[17955006.640000] sde : status=0, message=00, host=7, driver=00
[17955006.640000] sde : sense not available.
[17955006.640000] sde: Write Protect is off
[17955006.640000] sde: Mode Sense: 00 00 00 00
[17955006.640000] sde: assuming drive cache: write through
[17955006.724000] usb 5-3: new high speed USB device using ehci_hcd and address 23
[17955006.860000] usb 5-8: USB disconnect, address 22
[17955006.976000] usb 5-8: new high speed USB device using ehci_hcd and address 24
[17955007.120000] scsi4 : SCSI emulation for USB Mass Storage devices
[17955007.120000] usb-storage: device found at 24
[17955007.120000] usb-storage: waiting for device to settle before scanning
[17955008.800000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17955008.808000] e100: Copyright(c) 1999-2005 Intel Corporation
[17955008.808000] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 209
[17955008.872000] e100: eth0: e100_probe: addr 0xff8ff000, irq 209, MAC addr 00:13:20:23:07:BA
[17955009.852000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17955011.204000] ACPI: Power Button (FF) [PWRF]
[17955011.204000] ACPI: Sleep Button (CM) [SLPB]
[17955012.120000]   Vendor: Memorex   Model: TD 2C             Rev: 1.04
[17955012.120000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17955012.120000] SCSI device sde: 1003520 512-byte hdwr sectors (514 MB)
[17955012.120000] sde: Write Protect is off
[17955012.120000] sde: Mode Sense: 23 00 00 00
[17955012.120000] sde: assuming drive cache: write through
[17955012.128000] SCSI device sde: 1003520 512-byte hdwr sectors (514 MB)
[17955012.132000] sde: Write Protect is off
[17955012.136000] sde: Mode Sense: 23 00 00 00
[17955012.136000] sde: assuming drive cache: write through
[17955012.136000]  sde: sde1
[17955012.140000] sd 4:0:0:0: Attached scsi removable disk sde
[17955012.140000] sd 4:0:0:0: Attached scsi generic sg4 type 0
[17955012.140000] usb-storage: device scan complete
[17955012.596000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17955013.332000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17955501.856000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17955501.856000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17955512.640000] eth0: no IPv6 routers present
[17956945.236000] usb 5-2: new high speed USB device using ehci_hcd and address 28
[17956945.740000] usb 5-2: new high speed USB device using ehci_hcd and address 29
[17956946.748000] usb 5-2: new high speed USB device using ehci_hcd and address 32
[17956947.008000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956947.008000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956949.016000] usb 5-2: new high speed USB device using ehci_hcd and address 38
[17956949.520000] usb 5-2: new high speed USB device using ehci_hcd and address 39
[17956950.276000] usb 5-2: new high speed USB device using ehci_hcd and address 41
[17956951.856000] e100: eth0: e100_watchdog: link down
[17956952.040000] usb 5-2: new high speed USB device using ehci_hcd and address 47
[17956952.544000] usb 5-2: new high speed USB device using ehci_hcd and address 48
[17956953.552000] usb 5-2: new high speed USB device using ehci_hcd and address 51
[17956953.812000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956953.812000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956955.820000] usb 5-2: new high speed USB device using ehci_hcd and address 57
[17956958.340000] usb 5-2: new high speed USB device using ehci_hcd and address 66
[17956961.364000] usb 5-2: new high speed USB device using ehci_hcd and address 77
[17956962.120000] usb 5-2: new high speed USB device using ehci_hcd and address 79
[17956964.388000] usb 5-2: new high speed USB device using ehci_hcd and address 87
[17956964.892000] usb 5-2: new high speed USB device using ehci_hcd and address 88
[17956966.404000] usb 5-2: new high speed USB device using ehci_hcd and address 93
[17956966.664000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956966.664000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956967.664000] usb 5-2: new high speed USB device using ehci_hcd and address 95
[17956968.672000] usb 5-2: new high speed USB device using ehci_hcd and address 98
[17956969.680000] usb 5-2: new high speed USB device using ehci_hcd and address 101
[17956969.940000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956969.940000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956970.552000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956970.552000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956970.552000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17956971.016000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956971.016000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956971.424000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17956971.480000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956971.480000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956972.452000] usb 5-2: new high speed USB device using ehci_hcd and address 105
[17956973.208000] usb 5-2: new high speed USB device using ehci_hcd and address 107
[17956973.712000] usb 5-2: new high speed USB device using ehci_hcd and address 108
[17956974.216000] usb 5-2: new high speed USB device using ehci_hcd and address 109
[17956974.476000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956974.476000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956975.224000] usb 5-2: new high speed USB device using ehci_hcd and address 110
[17956975.484000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956975.484000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956976.232000] usb 5-2: new high speed USB device using ehci_hcd and address 111
[17956976.988000] usb 5-2: new high speed USB device using ehci_hcd and address 113
[17956977.492000] usb 5-2: new high speed USB device using ehci_hcd and address 114
[17956978.248000] usb 5-2: new high speed USB device using ehci_hcd and address 116
[17956978.752000] usb 5-2: new high speed USB device using ehci_hcd and address 117
[17956979.012000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956979.012000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956979.760000] usb 5-2: new high speed USB device using ehci_hcd and address 118
[17956980.768000] usb 5-2: new high speed USB device using ehci_hcd and address 121
[17956981.272000] usb 5-2: new high speed USB device using ehci_hcd and address 122
[17956982.280000] usb 5-2: new high speed USB device using ehci_hcd and address 125
[17956983.792000] usb 5-2: new high speed USB device using ehci_hcd and address 4
[17956984.296000] usb 5-2: new high speed USB device using ehci_hcd and address 5
[17956985.052000] usb 5-2: new high speed USB device using ehci_hcd and address 7
[17956985.312000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956985.312000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956986.060000] usb 5-2: new high speed USB device using ehci_hcd and address 8
[17956987.824000] usb 5-2: new high speed USB device using ehci_hcd and address 14
[17956988.084000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956988.084000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956990.848000] usb 5-2: new high speed USB device using ehci_hcd and address 25
[17956991.604000] usb 5-2: new high speed USB device using ehci_hcd and address 27
[17956991.864000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956991.864000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956992.476000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956992.476000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956992.476000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17956993.368000] usb 5-2: new high speed USB device using ehci_hcd and address 30
[17956993.872000] usb 5-2: new high speed USB device using ehci_hcd and address 31
[17956994.376000] usb 5-2: new high speed USB device using ehci_hcd and address 32
[17956995.636000] usb 5-2: new high speed USB device using ehci_hcd and address 36
[17956995.896000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956995.896000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956996.644000] usb 5-2: new high speed USB device using ehci_hcd and address 37
[17956996.904000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17956996.904000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17956999.416000] usb 5-2: new high speed USB device using ehci_hcd and address 45
[17957001.180000] usb 5-2: new high speed USB device using ehci_hcd and address 51
[17957001.440000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957001.440000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957002.692000] usb 5-2: new high speed USB device using ehci_hcd and address 54
[17957003.196000] usb 5-2: new high speed USB device using ehci_hcd and address 55
[17957003.952000] usb 5-2: new high speed USB device using ehci_hcd and address 57
[17957005.464000] usb 5-2: new high speed USB device using ehci_hcd and address 62
[17957006.220000] usb 5-2: new high speed USB device using ehci_hcd and address 64
[17957008.740000] usb 5-2: new high speed USB device using ehci_hcd and address 73
[17957009.496000] usb 5-2: new high speed USB device using ehci_hcd and address 75
[17957010.252000] usb 5-2: new high speed USB device using ehci_hcd and address 77
[17957010.512000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957010.512000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957011.260000] usb 5-2: new high speed USB device using ehci_hcd and address 78
[17957012.016000] usb 5-2: new high speed USB device using ehci_hcd and address 80
[17957013.024000] usb 5-2: new high speed USB device using ehci_hcd and address 83
[17957013.284000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957013.284000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957013.896000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957013.896000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957013.896000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17957015.040000] usb 5-2: new high speed USB device using ehci_hcd and address 87
[17957015.300000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957015.300000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957016.048000] usb 5-2: new high speed USB device using ehci_hcd and address 88
[17957019.576000] usb 5-2: new high speed USB device using ehci_hcd and address 101
[17957019.836000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957019.836000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957020.584000] usb 5-2: new high speed USB device using ehci_hcd and address 102
[17957021.340000] usb 5-2: new high speed USB device using ehci_hcd and address 104
[17957022.852000] usb 5-2: new high speed USB device using ehci_hcd and address 109
[17957023.608000] usb 5-2: new high speed USB device using ehci_hcd and address 111
[17957023.868000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957023.868000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957024.480000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957024.480000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957024.480000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17957025.876000] usb 5-2: new high speed USB device using ehci_hcd and address 116
[17957028.648000] usb 5-2: new high speed USB device using ehci_hcd and address 126
[17957029.856000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17957030.160000] usb 5-2: new high speed USB device using ehci_hcd and address 5
[17957031.168000] usb 5-2: new high speed USB device using ehci_hcd and address 8
[17957032.680000] usb 5-2: new high speed USB device using ehci_hcd and address 13
[17957032.940000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957032.940000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957033.688000] usb 5-2: new high speed USB device using ehci_hcd and address 14
[17957034.444000] usb 5-2: new high speed USB device using ehci_hcd and address 16
[17957034.948000] usb 5-2: new high speed USB device using ehci_hcd and address 17
[17957035.704000] usb 5-2: new high speed USB device using ehci_hcd and address 19
[17957035.964000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957035.964000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957036.712000] usb 5-2: new high speed USB device using ehci_hcd and address 20
[17957037.972000] usb 5-2: new high speed USB device using ehci_hcd and address 26
[17957038.476000] usb 5-2: new high speed USB device using ehci_hcd and address 27
[17957038.736000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957038.736000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957039.484000] usb 5-2: new high speed USB device using ehci_hcd and address 28
[17957039.988000] usb 5-2: new high speed USB device using ehci_hcd and address 29
[17957040.744000] usb 5-2: new high speed USB device using ehci_hcd and address 31
[17957041.004000] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[17957041.004000] hub 5-0:1.0: hub_port_status failed (err = -32)
[17957042.256000] usb 5-2: new high speed USB device using ehci_hcd and address 34
[17957043.768000] usb 5-2: new high speed USB device using ehci_hcd and address 39
[17957044.776000] usb 5-2: new high speed USB device using ehci_hcd and address 42
[17957045.280000] usb 5-2: new high speed USB device using ehci_hcd and address 43
[17957046.036000] usb 5-2: new high speed USB device using ehci_hcd and address 45
[17957047.548000] usb 5-2: new high speed USB device using ehci_hcd and address 50
[17957048.420000] hub 5-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[17957048.532000] usb 5-2: new high speed USB device using ehci_hcd and address 51
[17957049.312000] usb 5-2: new high speed USB device using ehci_hcd and address 53
[17963643.820000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17963644.336000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17963644.336000] SGI XFS Quota Management subsystem
[17963644.460000] JFS: nTxBlock = 7961, nTxLock = 63692
[17966857.168000] hdc: tray open
[17966857.168000] end_request: I/O error, dev hdc, sector 0
[17966857.168000] Buffer I/O error on device hdc, logical block 0
[17966857.168000] hdc: tray open
[17966857.168000] end_request: I/O error, dev hdc, sector 4
[17966857.168000] Buffer I/O error on device hdc, logical block 1
[17966857.172000] hdc: tray open
[17966857.172000] end_request: I/O error, dev hdc, sector 8
[17966857.172000] Buffer I/O error on device hdc, logical block 2
[17966857.172000] hdc: tray open
[17966857.172000] end_request: I/O error, dev hdc, sector 12
[17966857.172000] Buffer I/O error on device hdc, logical block 3
[17966857.172000] hdc: tray open
[17966857.172000] end_request: I/O error, dev hdc, sector 16
[17966857.172000] Buffer I/O error on device hdc, logical block 4
[17966857.176000] hdc: tray open
[17966857.176000] end_request: I/O error, dev hdc, sector 20
[17966857.176000] Buffer I/O error on device hdc, logical block 5
[17966857.176000] hdc: tray open
[17966857.176000] end_request: I/O error, dev hdc, sector 24
[17966857.176000] Buffer I/O error on device hdc, logical block 6
[17966857.176000] hdc: tray open
[17966857.176000] end_request: I/O error, dev hdc, sector 28
[17966857.176000] Buffer I/O error on device hdc, logical block 7
[17966857.180000] hdc: tray open
[17966857.180000] end_request: I/O error, dev hdc, sector 32
[17966857.180000] Buffer I/O error on device hdc, logical block 8
[17966857.180000] hdc: tray open
[17966857.180000] end_request: I/O error, dev hdc, sector 36
[17966857.180000] Buffer I/O error on device hdc, logical block 9
[17966857.180000] hdc: tray open
[17966857.180000] end_request: I/O error, dev hdc, sector 40
[17966857.180000] hdc: tray open
[17966857.180000] end_request: I/O error, dev hdc, sector 44
[17966857.184000] hdc: tray open
[17966857.184000] end_request: I/O error, dev hdc, sector 48
[17966857.184000] hdc: tray open
[17966857.184000] end_request: I/O error, dev hdc, sector 52
[17966857.184000] hdc: tray open
[17966857.184000] end_request: I/O error, dev hdc, sector 56
[17966857.188000] hdc: tray open
[17966857.188000] end_request: I/O error, dev hdc, sector 60
[17966857.188000] hdc: tray open
[17966857.188000] end_request: I/O error, dev hdc, sector 0
[17966857.188000] hdc: tray open
[17966857.188000] end_request: I/O error, dev hdc, sector 4
[17966857.192000] hdc: tray open
[17966857.192000] end_request: I/O error, dev hdc, sector 0
[17966857.192000] hdc: tray open
[17966857.192000] end_request: I/O error, dev hdc, sector 4
[17966857.192000] hdc: tray open
[17966857.192000] end_request: I/O error, dev hdc, sector 0
[17966857.196000] hdc: tray open
[17966857.196000] end_request: I/O error, dev hdc, sector 4
[17966926.028000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17966936.748000] eth0: no IPv6 routers present

```

6. **eric@eric-desktop:~$ sudo lshw -C network**
```
  *-network
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 02
       serial: 00:13:20:23:07:ba
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=full firmware=N/A ip=192.168.1.3 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:ff8ff000-ff8fffff ioport:bc00-bc3f irq:209
```

7. **eric@eric-desktop:~$ iwlist scan**
```
lo        Interface doesn't support scanning.
sit0      Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
```

8. **eric@eric-desktop:~$ lsb_release -d**
```
Description:    Ubuntu 6.06.2 LTS
```

9. **eric@eric-desktop:~$ uname -mr**
```
2.6.15-26-386 i686
```

10. **eric@eric-desktop:~$ sudo /etc/init.d/networking restart**
```
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:13:20:23:07:ba
Sending on   LPF/eth0/00:13:20:23:07:ba
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:13:20:23:07:ba
Sending on   LPF/eth0/00:13:20:23:07:ba
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 40396 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

---

