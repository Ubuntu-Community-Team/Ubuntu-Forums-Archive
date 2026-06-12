---
title: "cannot get wireless to connect"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by lbdanes on 2010-09-14
I'm a first time user of ubuntu and I am having huge issues getting my wireless to work. I've tried using the troubleshooting guide, but it says that it's already installed and to go to windows wireless drivers to install the .inf file. Problem is.. I can't find the file anywhere.  When I type lspci into the terminal this is what it says: 03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Can anyone help walk me through getting this wireless to work please? I'm really confused! :confused:

---

### Post by vagrale13 on 2010-09-14
> **lbdanes said:**
> I'm a first time user of ubuntu and I am having huge issues getting my wireless to work. I've tried using the troubleshooting guide, but it says that it's already installed and to go to windows wireless drivers to install the .inf file. Problem is.. I can't find the file anywhere.  When I type lspci into the terminal this is what it says: 03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Can anyone help walk me through getting this wireless to work please? I'm really confused! :confused:
Look here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
and more info about your card and which driver support here [http://wireless.kernel.org/en/users/Drivers/b43#Known_PCI_devices](http://wireless.kernel.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by lbdanes on 2010-09-14
I followed the steps,but it still doesn't work. It says my card is supported and that the driver is active, but it will not connect to wifi. I have Wifi Radar on my laptop, but that doesn't work either and the in Windows Wireless Drivers is where it tells me to install a driver.....

---

### Post by vagrale13 on 2010-09-14
Post the output of command
```
iwconfig
sudo iwlist scan
lsmod
```

---

### Post by lbdanes on 2010-09-14
laura@laura-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

laura@laura-laptop:~$ sudo iwlist scan
[sudo] password for laura: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: E0:91:53:0C:31:44
                    ESSID:"107_Poplar"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-53 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: E0:91:53:0C:40:3E
                    ESSID:"mckee_wireless"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: E0:91:53:1E:01:ED
                    ESSID:"Durr Wireless"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 22:24:8C:19:A9:71
                    ESSID:"Williamsburg_Paint"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-71 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 05 - Address: E0:91:53:1E:17:EF
                    ESSID:"Dauphinee Wireless"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 00:24:01:75:F4:6B
                    ESSID:"bergerpl"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-92 dBm
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

laura@laura-laptop:~$ lsmod
Module                  Size  Used by
snd_hda_codec_conexant    22641  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
binfmt_misc             6587  1 
joydev                  8708  0 
ppdev                   5259  0 
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
nouveau               467048  2 
ttm                    49943  1 nouveau
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
drm_kms_helper         29297  1 nouveau
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     7596  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162377  4 nouveau,ttm,drm_kms_helper
psmouse                63245  0 
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959598  0 
k8temp                  3024  0 
serio_raw               3978  0 
agpgart                31724  2 ttm,drm
soundcore               6620  1 snd
lib80211                5046  2 lib80211_crypt_tkip,wl
i2c_algo_bit            5028  1 nouveau
i2c_nforce2             5199  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
video                  17375  0 
output                  1871  1 video
parport                32635  2 ppdev,lp
pata_amd                8766  1 
forcedeth              49556  0 
sata_nv                19440  2 


I have no idea what any of this means....:confused:

---

### Post by vagrale13 on 2010-09-14
All commands result is info about wireless connection and drivers used.

For connecting use [NetworkManager]("http://projects.gnome.org/NetworkManager/") from panel 

If you do this **b43/STA - Internet access** [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrid%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrid%20drivers) 
(**Step 1 - ****Step 2 - ****Step 3**)
and continues to have connection problem, give the output of
```
dmesg
```put that in [CODE][CODE] tags because it would be a large result.

---

### Post by bkratz on 2010-09-14
Which connection are you attempting to access?  I see three that are on channel 6 with just about the same strength. Is one of them yours? Can you set your A/P to a different channel?


Actually I see 5.

---

### Post by lbdanes on 2010-09-14
when i put demsg in code tags it says command not found. When I don't, this is what I get: 
[ 2579.904069] [drm] nouveau 0000:00:05.0: Evicting buffers...
[ 2579.919983] [drm] nouveau 0000:00:05.0: Idling channels...
[ 2579.920103] [drm] nouveau 0000:00:05.0: Suspending GPU objects...
[ 2580.067675] [drm] nouveau 0000:00:05.0: And we're gone!
[ 2580.067709] nouveau 0000:00:05.0: PCI INT A disabled
[ 2580.080116] nouveau 0000:00:05.0: power state changed by ACPI to D3
[ 2580.080128] PM: suspend of drv:nouveau dev:0000:00:05.0 complete after 176.060 msecs
[ 2580.080471] PM: suspend of devices complete after 1266.100 msecs
[ 2580.080474] PM: suspend devices took 1.268 seconds
[ 2580.112386] PM: late suspend of devices complete after 31.907 msecs
[ 2580.112547] ACPI: Preparing to enter system sleep state S3
[ 2580.112799] Disabling non-boot CPUs ...
[ 2580.112817] Back to C!
[ 2580.112817] ACPI: Waking up from system sleep state S3
[ 2581.249246] pci 0000:00:00.0: Found disabled HT MSI Mapping
[ 2581.249252] pci 0000:00:00.0: Enabling HT MSI Mapping
[ 2581.249361] pcieport 0000:00:02.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2581.249392] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2581.249409] pcieport 0000:00:03.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2581.249442] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2581.249600] pci 0000:00:0a.3: restoring config space at offset 0xf (was 0x1030200, writing 0x103020a)
[ 2581.249664] ohci_hcd 0000:00:0b.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
[ 2581.249698] ehci_hcd 0000:00:0b.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 2581.249754] sata_nv 0000:00:0e.0: restoring config space at offset 0x1 (was 0xb00005, writing 0xb00007)
[ 2581.249812] pci 0000:00:09.0: Found enabled HT MSI Mapping
[ 2581.249885] pci 0000:00:09.0: Found enabled HT MSI Mapping
[ 2581.249898] HDA Intel 0000:00:10.1: restoring config space at offset 0xf (was 0x5020200, writing 0x502020b)
[ 2581.249912] HDA Intel 0000:00:10.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 2581.249976] pci 0000:00:09.0: Found enabled HT MSI Mapping
[ 2581.250049] wl 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[ 2581.250064] wl 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xb8000000)
[ 2581.250069] wl 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2581.250076] wl 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 2581.250445] PM: early resume of devices complete after 1.368 msecs
[ 2581.648128] PM: resume of drv:battery dev:PNP0C0A:00 complete after 392.031 msecs
[ 2581.657607] [drm] nouveau 0000:00:05.0: We're back, enabling device...
[ 2581.657638] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2581.657667] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2581.657696] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2581.657724] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2581.657732] nouveau 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[ 2581.657737] nouveau 0000:00:05.0: setting latency timer to 64
[ 2581.657740] [drm] nouveau 0000:00:05.0: POSTing device...
[ 2581.657745] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 0 at offset 0xE225
[ 2581.657815] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 1 at offset 0xE364
[ 2581.657819] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 2 at offset 0xE365
[ 2581.657885] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 3 at offset 0xE4E7
[ 2581.657888] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001305 not verified ===
[ 2581.657892] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001401 not verified ===
[ 2581.657895] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001405 not verified ===
[ 2581.657898] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001409 not verified ===
[ 2581.657901] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x0000140D not verified ===
[ 2581.657913] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 4 at offset 0xE533
[ 2581.657917] [drm] nouveau 0000:00:05.0: Reinitialising engines...
[ 2581.657981] [drm] nouveau 0000:00:05.0: Restoring GPU objects...
[ 2581.687570] [drm] nouveau 0000:00:05.0: Restoring mode...
[ 2581.687599] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[ 2581.687604] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[ 2581.687623] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[ 2581.687626] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[ 2581.836056] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[ 2581.836059] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[ 2582.004851] [drm] nouveau 0000:00:05.0: Restoring CRTC_OWNER to 0.
[ 2582.013965] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[ 2582.013968] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on vga encoder (output 1)
[ 2582.013973] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[ 2582.034506] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[ 2582.034510] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[ 2582.034513] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[ 2582.488056] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[ 2582.488058] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[ 2582.640043] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[ 2582.640046] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[ 2582.640048] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[ 2583.360054] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[ 2583.369986] PM: resume of drv:nouveau dev:0000:00:05.0 complete after 1712.380 msecs
[ 2583.370013] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[ 2583.370020] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[ 2583.392040] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[ 2583.392045] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[ 2583.392059] pata_amd 0000:00:0d.0: setting latency timer to 64
[ 2583.393195] ata2: port disabled. ignoring.
[ 2583.393211] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[ 2583.393215] sata_nv 0000:00:0e.0: setting latency timer to 64
[ 2583.393344] pci 0000:00:10.0: setting latency timer to 64
[ 2583.393354] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[ 2583.393359] HDA Intel 0000:00:10.1: setting latency timer to 64
[ 2583.556343] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 2583.556347] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 2583.556377] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc700) ACPI=0x39f (120:600:0x12)
[ 2583.572286] ata1.00: configured for MWDMA2
[ 2583.860063] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2583.868212] ata3.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[ 2583.912470] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 519.078 msecs
[ 2583.912494] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[ 2583.912499] wl 0000:03:00.0: setting latency timer to 64
[ 2583.932616] ata3.00: configured for UDMA/133
[ 2583.944407] sd 2:0:0:0: [sda] Starting disk
[ 2583.953105] PM: resume of devices complete after 2702.616 msecs
[ 2583.953231] PM: resume devices took 2.704 seconds
[ 2583.953258] PM: Finishing wakeup.
[ 2583.953260] Restarting tasks ... done.
[ 2584.126565] ata4: SATA link down (SStatus 0 SControl 300)
[ 2585.310759] eth0: no link during initialization.
[ 2585.312495] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2585.467130] eth0: link up.
[ 2585.467441] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2596.112054] eth0: no IPv6 routers present
[ 2596.212057] eth1: no IPv6 routers present
[ 2665.300212] PM: Syncing filesystems ... done.
[ 2665.316038] PM: Preparing system for mem sleep
[ 2665.316042] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2665.317274] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 2665.317342] PM: Entering mem sleep
[ 2665.317357] Suspending console(s) (use no_console_suspend to debug)
[ 2665.317705] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 2665.454134] sd 2:0:0:0: [sda] Stopping disk
[ 2665.831942] PM: suspend of drv:sd dev:2:0:0:0 complete after 514.238 msecs
[ 2666.220795] PM: suspend of drv:psmouse dev:serio1 complete after 388.728 msecs
[ 2666.322096] wl 0000:03:00.0: PCI INT A disabled
[ 2666.352042] HDA Intel 0000:00:10.1: PCI INT B disabled
[ 2666.368107] sata_nv 0000:00:0e.0: PCI INT A disabled
[ 2666.384077] ata2: port disabled. ignoring.
[ 2666.400033] ehci_hcd 0000:00:0b.1: PCI INT B disabled
[ 2666.400043] ohci_hcd 0000:00:0b.0: PCI INT A disabled
[ 2666.400059] [drm] nouveau 0000:00:05.0: Evicting buffers...
[ 2666.400062] [drm] nouveau 0000:00:05.0: Idling channels...
[ 2666.400171] [drm] nouveau 0000:00:05.0: Suspending GPU objects...
[ 2666.548117] [drm] nouveau 0000:00:05.0: And we're gone!
[ 2666.548138] nouveau 0000:00:05.0: PCI INT A disabled
[ 2666.564106] nouveau 0000:00:05.0: power state changed by ACPI to D3
[ 2666.564117] PM: suspend of drv:nouveau dev:0000:00:05.0 complete after 164.057 msecs
[ 2666.564456] PM: suspend of devices complete after 1246.905 msecs
[ 2666.564460] PM: suspend devices took 1.248 seconds
[ 2666.596415] PM: late suspend of devices complete after 31.950 msecs
[ 2666.596582] ACPI: Preparing to enter system sleep state S3
[ 2666.596833] Disabling non-boot CPUs ...
[ 2666.596852] Back to C!
[ 2666.596852] ACPI: Waking up from system sleep state S3
[ 2666.596852] pci 0000:00:00.0: Found disabled HT MSI Mapping
[ 2666.596852] pci 0000:00:00.0: Enabling HT MSI Mapping
[ 2666.596852] pcieport 0000:00:02.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2666.596852] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2666.596852] pcieport 0000:00:03.0: restoring config space at offset 0x7 (was 0x1f1, writing 0x200001f1)
[ 2666.596852] pcieport 0000:00:03.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2666.596852] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2666.596852] pci 0000:00:0a.3: restoring config space at offset 0xf (was 0x1030200, writing 0x103020a)
[ 2666.596852] ohci_hcd 0000:00:0b.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
[ 2666.600055] ehci_hcd 0000:00:0b.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 2666.600136] sata_nv 0000:00:0e.0: restoring config space at offset 0x1 (was 0xb00005, writing 0xb00007)
[ 2666.600229] pci 0000:00:09.0: Found enabled HT MSI Mapping
[ 2666.600327] pci 0000:00:09.0: Found enabled HT MSI Mapping
[ 2666.600345] HDA Intel 0000:00:10.1: restoring config space at offset 0xf (was 0x5020200, writing 0x502020b)
[ 2666.600364] HDA Intel 0000:00:10.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 2666.600448] pci 0000:00:09.0: Found enabled HT MSI Mapping
[ 2666.600537] wl 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[ 2666.600554] wl 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xb8000000)
[ 2666.600560] wl 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2666.600566] wl 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 2666.601034] PM: early resume of devices complete after 1.784 msecs
[ 2667.000131] PM: resume of drv:battery dev:PNP0C0A:00 complete after 392.038 msecs
[ 2667.009806] [drm] nouveau 0000:00:05.0: We're back, enabling device...
[ 2667.009836] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2667.009866] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2667.009895] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2667.009923] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2667.009931] nouveau 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[ 2667.009936] nouveau 0000:00:05.0: setting latency timer to 64
[ 2667.009939] [drm] nouveau 0000:00:05.0: POSTing device...
[ 2667.009944] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 0 at offset 0xE225
[ 2667.010014] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 1 at offset 0xE364
[ 2667.010017] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 2 at offset 0xE365
[ 2667.010083] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 3 at offset 0xE4E7
[ 2667.010086] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001305 not verified ===
[ 2667.010090] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001401 not verified ===
[ 2667.010093] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001405 not verified ===
[ 2667.010096] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001409 not verified ===
[ 2667.010099] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x0000140D not verified ===
[ 2667.010111] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 4 at offset 0xE533
[ 2667.010115] [drm] nouveau 0000:00:05.0: Reinitialising engines...
[ 2667.010179] [drm] nouveau 0000:00:05.0: Restoring GPU objects...
[ 2667.039657] [drm] nouveau 0000:00:05.0: Restoring mode...
[ 2667.039664] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[ 2667.039668] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[ 2667.039687] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[ 2667.039690] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[ 2667.188047] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[ 2667.188051] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[ 2667.356837] [drm] nouveau 0000:00:05.0: Restoring CRTC_OWNER to 0.
[ 2667.365947] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[ 2667.365950] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on vga encoder (output 1)
[ 2667.365954] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[ 2667.386407] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[ 2667.386409] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[ 2667.386412] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[ 2667.840040] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[ 2667.840043] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[ 2667.992032] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[ 2667.992035] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[ 2667.992038] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[ 2668.712045] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[ 2668.721973] PM: resume of drv:nouveau dev:0000:00:05.0 complete after 1712.168 msecs
[ 2668.722000] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[ 2668.722005] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[ 2668.744035] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[ 2668.744039] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[ 2668.744053] pata_amd 0000:00:0d.0: setting latency timer to 64
[ 2668.745190] ata2: port disabled. ignoring.
[ 2668.745206] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[ 2668.745210] sata_nv 0000:00:0e.0: setting latency timer to 64
[ 2668.745339] pci 0000:00:10.0: setting latency timer to 64
[ 2668.745349] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[ 2668.745354] HDA Intel 0000:00:10.1: setting latency timer to 64
[ 2668.908336] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 2668.908340] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 2668.908370] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc700) ACPI=0x39f (120:600:0x12)
[ 2668.924290] ata1.00: configured for MWDMA2
[ 2669.212046] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2669.220209] ata3.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[ 2669.264466] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 519.079 msecs
[ 2669.264491] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[ 2669.264495] wl 0000:03:00.0: setting latency timer to 64
[ 2669.280620] ata3.00: configured for UDMA/133
[ 2669.295918] sd 2:0:0:0: [sda] Starting disk
[ 2669.311289] PM: resume of devices complete after 2710.201 msecs
[ 2669.311416] PM: resume devices took 2.708 seconds
[ 2669.311441] PM: Finishing wakeup.
[ 2669.311443] Restarting tasks ... done.
[ 2669.478715] ata4: SATA link down (SStatus 0 SControl 300)
[ 2669.783178] eth0: no link during initialization.
[ 2669.785243] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2670.869291] eth0: link up.
[ 2670.869655] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2680.556050] eth1: no IPv6 routers present
[ 2681.768046] eth0: no IPv6 routers present
[ 2693.332195] PM: Syncing filesystems ... done.
[ 2693.348050] PM: Preparing system for mem sleep
[ 2693.348055] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2693.349296] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 2693.349364] PM: Entering mem sleep
[ 2693.349379] Suspending console(s) (use no_console_suspend to debug)
[ 2693.349727] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 2693.449955] sd 2:0:0:0: [sda] Stopping disk
[ 2693.843989] PM: suspend of drv:sd dev:2:0:0:0 complete after 494.262 msecs
[ 2694.235109] PM: suspend of drv:psmouse dev:serio1 complete after 390.994 msecs
[ 2694.338514] wl 0000:03:00.0: PCI INT A disabled
[ 2694.368050] HDA Intel 0000:00:10.1: PCI INT B disabled
[ 2694.384123] sata_nv 0000:00:0e.0: PCI INT A disabled
[ 2694.400083] ata2: port disabled. ignoring.
[ 2694.416044] ehci_hcd 0000:00:0b.1: PCI INT B disabled
[ 2694.416054] ohci_hcd 0000:00:0b.0: PCI INT A disabled
[ 2694.416070] [drm] nouveau 0000:00:05.0: Evicting buffers...
[ 2694.416073] [drm] nouveau 0000:00:05.0: Idling channels...
[ 2694.416184] [drm] nouveau 0000:00:05.0: Suspending GPU objects...
[ 2694.564590] [drm] nouveau 0000:00:05.0: And we're gone!
[ 2694.564611] nouveau 0000:00:05.0: PCI INT A disabled
[ 2694.580119] nouveau 0000:00:05.0: power state changed by ACPI to D3
[ 2694.580129] PM: suspend of drv:nouveau dev:0000:00:05.0 complete after 164.058 msecs
[ 2694.580470] PM: suspend of devices complete after 1230.896 msecs
[ 2694.580473] PM: suspend devices took 1.232 seconds
[ 2694.612414] PM: late suspend of devices complete after 31.936 msecs
[ 2694.612579] ACPI: Preparing to enter system sleep state S3
[ 2694.612829] Disabling non-boot CPUs ...
[ 2694.612848] Back to C!
[ 2694.612848] ACPI: Waking up from system sleep state S3
[ 2694.612848] pci 0000:00:00.0: Found disabled HT MSI Mapping
[ 2694.612848] pci 0000:00:00.0: Enabling HT MSI Mapping
[ 2694.612848] pcieport 0000:00:02.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2694.612848] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2694.612848] pcieport 0000:00:03.0: restoring config space at offset 0x7 (was 0x1f1, writing 0x200001f1)
[ 2694.612848] pcieport 0000:00:03.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2694.612848] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2694.612848] pci 0000:00:0a.3: restoring config space at offset 0xf (was 0x1030200, writing 0x103020a)
[ 2694.612848] ohci_hcd 0000:00:0b.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb00003)
[ 2694.616053] ehci_hcd 0000:00:0b.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 2694.616133] sata_nv 0000:00:0e.0: restoring config space at offset 0x1 (was 0xb00005, writing 0xb00007)
[ 2694.616226] pci 0000:00:09.0: Found enabled HT MSI Mapping
[ 2694.616326] pci 0000:00:09.0: Found enabled HT MSI Mapping
[ 2694.616344] HDA Intel 0000:00:10.1: restoring config space at offset 0xf (was 0x5020200, writing 0x502020b)
[ 2694.616363] HDA Intel 0000:00:10.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 2694.616447] pci 0000:00:09.0: Found enabled HT MSI Mapping
[ 2694.616536] wl 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
[ 2694.616553] wl 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xb8000000)
[ 2694.616559] wl 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2694.616565] wl 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 2694.617035] PM: early resume of devices complete after 1.790 msecs
[ 2695.016128] PM: resume of drv:battery dev:PNP0C0A:00 complete after 392.032 msecs
[ 2695.025792] [drm] nouveau 0000:00:05.0: We're back, enabling device...
[ 2695.025823] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2695.025852] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2695.025881] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2695.025909] nouveau 0000:00:05.0: power state changed by ACPI to D0
[ 2695.025917] nouveau 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[ 2695.025922] nouveau 0000:00:05.0: setting latency timer to 64
[ 2695.025925] [drm] nouveau 0000:00:05.0: POSTing device...
[ 2695.025930] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 0 at offset 0xE225
[ 2695.026000] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 1 at offset 0xE364
[ 2695.026004] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 2 at offset 0xE365
[ 2695.026069] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 3 at offset 0xE4E7
[ 2695.026073] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001305 not verified ===
[ 2695.026076] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001401 not verified ===
[ 2695.026079] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001405 not verified ===
[ 2695.026083] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x00001409 not verified ===
[ 2695.026086] [drm] nouveau 0000:00:05.0: === C51 misaligned reg 0x0000140D not verified ===
[ 2695.026098] [drm] nouveau 0000:00:05.0: Parsing VBIOS init table 4 at offset 0xE533
[ 2695.026101] [drm] nouveau 0000:00:05.0: Reinitialising engines...
[ 2695.026165] [drm] nouveau 0000:00:05.0: Restoring GPU objects...
[ 2695.055654] [drm] nouveau 0000:00:05.0: Restoring mode...
[ 2695.055661] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[ 2695.055666] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[ 2695.055685] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[ 2695.055688] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[ 2695.204057] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[ 2695.204060] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[ 2695.372844] [drm] nouveau 0000:00:05.0: Restoring CRTC_OWNER to 0.
[ 2695.381958] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on lvds encoder (output 0)
[ 2695.381961] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on vga encoder (output 1)
[ 2695.381964] [drm] nouveau 0000:00:05.0: Setting dpms mode 3 on TV encoder (output 2)
[ 2695.402404] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[ 2695.402407] [drm] nouveau 0000:00:05.0: Calling LVDS script 6:
[ 2695.402410] [drm] nouveau 0000:00:05.0: 0xD3CD: Parsing digital output script table
[ 2695.856044] [drm] nouveau 0000:00:05.0: Calling LVDS script 2:
[ 2695.856047] [drm] nouveau 0000:00:05.0: 0xD432: Parsing digital output script table
[ 2696.008040] [drm] nouveau 0000:00:05.0: Setting dpms mode 0 on lvds encoder (output 0)
[ 2696.008043] [drm] nouveau 0000:00:05.0: Calling LVDS script 5:
[ 2696.008045] [drm] nouveau 0000:00:05.0: 0xD3B6: Parsing digital output script table
[ 2696.728043] [drm] nouveau 0000:00:05.0: Output LVDS-1 is running on CRTC 0 using output A
[ 2696.737975] PM: resume of drv:nouveau dev:0000:00:05.0 complete after 1712.184 msecs
[ 2696.738002] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[ 2696.738008] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[ 2696.760048] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[ 2696.760052] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[ 2696.760065] pata_amd 0000:00:0d.0: setting latency timer to 64
[ 2696.761211] ata2: port disabled. ignoring.
[ 2696.761226] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[ 2696.761230] sata_nv 0000:00:0e.0: setting latency timer to 64
[ 2696.761358] pci 0000:00:10.0: setting latency timer to 64
[ 2696.761368] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[ 2696.761373] HDA Intel 0000:00:10.1: setting latency timer to 64
[ 2696.924349] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 2696.924353] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 2696.924383] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc700) ACPI=0x39f (120:600:0x12)
[ 2696.940292] ata1.00: configured for MWDMA2
[ 2697.228068] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2697.236219] ata3.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[ 2697.280478] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 519.072 msecs
[ 2697.280503] wl 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, high) -> IRQ 19
[ 2697.280507] wl 0000:03:00.0: setting latency timer to 64
[ 2697.300608] ata3.00: configured for UDMA/133
[ 2697.311289] sd 2:0:0:0: [sda] Starting disk
[ 2697.323004] PM: resume of devices complete after 2705.915 msecs
[ 2697.323129] PM: resume devices took 2.704 seconds
[ 2697.323155] PM: Finishing wakeup.
[ 2697.323157] Restarting tasks ... done.
[ 2697.494584] ata4: SATA link down (SStatus 0 SControl 300)
[ 2697.659002] eth0: no link during initialization.
[ 2697.659446] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2698.852034] eth0: link up.
[ 2698.852406] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2708.456061] eth1: no IPv6 routers present
[ 2709.136027] eth0: no IPv6 routers present


As for which driver I'm trying to connect to, i don't know what one to use or how to change it. The enable wireless is checked but nothing shows up in wifi radar or windows wireless.....

---

### Post by bkratz on 2010-09-14
Sorry if not clear--which is your connection? As an example

ESSID:"107_Poplar"
Mode:Managed
Frequency:2.437 GHz (Channel 6)

Poplar is the name of one connection--Is that yours? or is it McKee_Wireless or one of the others?  If you A/P is one of those on channel 6, you have a lot of interfering signals.

---

### Post by lbdanes on 2010-09-14
107 is neighbors i would assume and have no idea about mckee wireless.

---

### Post by bkratz on 2010-09-14
But is one of the ones that is on channel 6 the one you are trying to access?

---

### Post by lbdanes on 2010-09-14
I don't about channel 6... it all started because i wanted to access wifi @ work thru at&t. I just have no idea about which one I'm supposed to use... How do I clear the interfering signals?

---

### Post by bkratz on 2010-09-14
> **lbdanes said:**
> I don't about channel 6... it all started because i wanted to access wifi @ work thru at&t. I just have no idea about which one I'm supposed to use... How do I clear the interfering signals?

Which one is yours? Which one do you have a password for? If it is one that is not on channel 6, you should not have a problem. If yours is one on channel 6 I would suggest moving the channel to an unused channel on the A/P (router).

---

### Post by lbdanes on 2010-09-14
I don't have a password, I'm trying to make the wifi work....so that I can hook up at work to free wifi. i don't have a router in my home, in order to get internet at home I hook up the ethernet cable.

---

### Post by k3jsparks on 2010-09-14
I have the same problem with my wireless router. the command sudo iwlist scan says that the lo and eth0 interfaces do not support scanning. For wlan0 it says, "Interface does not support scanning: network is down"

the network is fine, I am watching NetFlix on it as I type this, going through the router to a Wii.

Any ideas?

---

### Post by bkratz on 2010-09-15
@lbdanes since your iwlist scan shows that you can use wireless and you have the correct driver loaded--I think I would try it at some other "free" location ( like some gas stations or restaurants) where the interference would be lessened-just to check. Since you don't have your own A/P the only one that you would be able to access at your present location would be the unencrypted one ( your neighbors--ESSID:"107_Poplar") since it is not encrypted "open" (Encryption keyoff). Unfortunately that is one of the ones that is on channel 6.  You could look through this and see if you can find anything useful.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)



@k3jsparks
Your problem is not the same--I would suggest that you start a new thread with your symptoms. The OP's information says that he does see the networks with sudo iwlist scan.

---

