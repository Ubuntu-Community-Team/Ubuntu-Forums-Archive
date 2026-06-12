---
title: "MSI Wind Nettop 100/ Ubuntu 10.04/ Intel Corporation PRO/Wireless 3945ABG PLEASE HELP"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by plinx on 2010-05-16
I am a very new ubuntu user.  I built a barebones pc ([SIZE=1][COLOR=Black]MSI Wind Nettop 100 Intel 1.6GHz Atom 330 (dual core) on board Intel  945GC Intel GMA 950 Mini / Booksize Barebone System                     [/COLOR][/SIZE]), installed Ubuntu 10.04, everything works well, except I do not know how to get wireless to work, says device is not ready.  I've tried using some of the guides available but I'm kinda confused.  It seems ubuntu is reading my card, and I think my driver is fine.  If anyone could direct me on what to do I would deeply appreciate it.  Here's the info suggested in the guide for such posts:

**2) lspci**
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

**3) iwconfig wlan0**
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 

**4) lsmod**
zace@zace-desktop:~$ lsmod 
Module                  Size  Used by 
binfmt_misc             6587  1 
ppdev                   5259  0 
nls_iso8859_1           3249  2 
nls_cp437               4919  2 
vfat                    8901  2 
fat                    47767  1 vfat 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
vga16fb                11385  0 
vgastate                8961  1 vga16fb 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               5412  1 snd_hda_codec 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
arc4                    1153  2 
snd_timer              19098  2 snd_pcm,snd_seq 
i915                  282354  2 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
iwl3945                68727  0 
drm_kms_helper         29297  1 i915 
iwlcore               105922  1 iwl3945 
usbhid                 36110  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
drm                   162471  3 i915,drm_kms_helper 
i2c_algo_bit            5028  1 i915 
mac80211              204922  2 iwl3945,iwlcore 
soundcore               6620  1 snd 
led_class               2864  2 iwl3945,iwlcore 
psmouse                63245  0 
video                  17375  1 i915 
hid                    67032  1 usbhid 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
output                  1871  1 video 
cfg80211              126485  3 iwl3945,iwlcore,mac80211 
intel_agp              24177  2 i915 
agpgart                31724  2 drm,intel_agp 
lp                      7028  0 
parport                32635  2 ppdev,lp 
usb_storage            39425  1 
r8169                  33884  0 
mii                     4381  1 r8169 

**5)lsmod**
v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1d.0-2/input1 
[    7.771802] usbcore: registered new interface driver usbhid 
[    7.771813] usbhid: v2.6:USB HID core driver 
[    7.830828] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks 
[    7.830841] iwl3945: Copyright(c) 2003-2009 Intel Corporation 
[    7.831015] iwl3945 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    7.831042] iwl3945 0000:02:00.0: setting latency timer to 64 
[    7.899325] iwl3945 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels 
[    7.899337] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG 
[    7.899472]   alloc irq_desc for 29 on node -1 
[    7.899480]   alloc kstat_irqs on node -1 
[    7.899529] iwl3945 0000:02:00.0: irq 29 for MSI/MSI-X 
[    7.900751] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    7.900770] i915 0000:00:02.0: setting latency timer to 64 
[    7.904715] iwl3945 0000:02:00.0: Hardware error detected.  Restarting. 
[    7.922312] [drm] set up 7M of stolen space 
[    7.925115] [drm] initialized overlay support 
[    7.944443] phy0: Selected rate control algorithm 'iwl-3945-rs' 
[    8.095559] fb0: inteldrmfb frame buffer device 
[    8.095567] registered panic notifier 
[    8.095592] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
[    8.145754] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    8.145949] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[    8.150754] vga16fb: initializing 
[    8.150762] vga16fb: mapped to 0xc00a0000 
[    8.150770] vga16fb: not registering due to another framebuffer present 
[    8.297998] Console: switching to colour frame buffer device 180x56 
[    8.824047] type=1505 audit(1273999065.920:5):  operation="profile_load" pid=759 name="/usr/share/gdm/guest-session/Xsession" 
[    8.831936] type=1505 audit(1273999065.928:6):  operation="profile_replace" pid=760 name="/sbin/dhclient3" 
[    8.832982] type=1505 audit(1273999065.932:7):  operation="profile_replace" pid=760 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[    8.833459] type=1505 audit(1273999065.932:8):  operation="profile_replace" pid=760 name="/usr/lib/connman/scripts/dhclient-script" 
[    8.841135] r8169: eth0: link down 
[    8.841807] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[    8.858309] type=1505 audit(1273999065.956:9):  operation="profile_load" pid=761 name="/usr/bin/evince" 
[    8.868528] type=1505 audit(1273999065.964:10):  operation="profile_load" pid=761 name="/usr/bin/evince-previewer" 
[    8.875293] type=1505 audit(1273999065.972:11):  operation="profile_load" pid=761 name="/usr/bin/evince-thumbnailer" 
[    8.879519] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-2.ucode 
[    8.903320] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9 
[    8.910243] iwl3945 0000:02:00.0: Hardware error detected.  Restarting. 
[    8.934347] iwl3945 0000:02:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a1, s/b 0xf802020 
[    9.240514] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x020c0000 
[    9.240533] hda_codec: ALC888: BIOS auto-probing. 
[    9.242170] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6 
[    9.276818] ppdev: user-space parallel port driver 
[   10.932034] iwl3945 0000:02:00.0: Wait for START_ALIVE timeout after 2000ms. 
[   10.968841] iwl3945 0000:02:00.0: Hardware error detected.  Restarting. 
[   10.992919] iwl3945 0000:02:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a1, s/b 0xf802020 
[   12.992030] iwl3945 0000:02:00.0: Wait for START_ALIVE timeout after 2000ms. 
[  330.091323] iwl3945 0000:02:00.0: Hardware error detected.  Restarting. 
[  330.115325] iwl3945 0000:02:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a1, s/b 0xf802020 
[  332.112044] iwl3945 0000:02:00.0: Wait for START_ALIVE timeout after 2000ms. 
[  797.761304] iwl3945 0000:02:00.0: Hardware error detected.  Restarting. 
[  797.785425] iwl3945 0000:02:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a1, s/b 0xf802020 
[  799.784036] iwl3945 0000:02:00.0: Wait for START_ALIVE timeout after 2000ms. 
[ 1846.840067] usb 1-5: USB disconnect, address 4 
[ 2746.328931] PM: Marking nosave pages: 0000000000002000 - 0000000000006000 
[ 2746.328940] PM: Marking nosave pages: 000000000009f000 - 0000000000100000 
[ 2746.328948] PM: Basic memory bitmaps created 
[ 2746.328952] PM: Syncing filesystems ... done. 
[ 2746.464539] Freezing user space processes ... (elapsed 0.00 seconds) done. 
[ 2746.466181] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done. 
[ 2746.466453] PM: Preallocating image memory... done (allocated 380710 pages) 
[ 2747.218986] PM: Allocated 1522840 kbytes in 0.75 seconds (2030.45 MB/s) 
[ 2747.218992] Suspending console(s) (use no_console_suspend to debug) 
[ 2747.283891] sd 2:0:0:0: [sda] Synchronizing SCSI cache 
[ 2747.292988] ACPI handle has no context! 
[ 2747.308224] ata_piix 0000:00:1f.2: PCI INT B disabled 
[ 2747.308384] ata_piix 0000:00:1f.1: PCI INT A disabled 
[ 2747.412097] HDA Intel 0000:00:1b.0: PCI INT A disabled 
[ 2747.412142] ACPI handle has no context! 
[ 2747.428029] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 119.602 msecs 
[ 2747.447344] PM: freeze of devices complete after 228.043 msecs 
[ 2747.447939] PM: late freeze of devices complete after 0.586 msecs 
[ 2747.448077] ACPI: Preparing to enter system sleep state S4 
[ 2747.448582] PM: Saving platform NVS memory 
[ 2747.476024] Disabling non-boot CPUs ... 
[ 2747.476066] CPU0 attaching NULL sched-domain. 
[ 2747.476072] CPU1 attaching NULL sched-domain. 
[ 2747.476077] CPU2 attaching NULL sched-domain. 
[ 2747.476081] CPU3 attaching NULL sched-domain. 
[ 2747.540026] CPU0 attaching NULL sched-domain. 
[ 2747.543465] CPU 1 is now offline 
[ 2747.546812] CPU 2 is now offline 
[ 2747.548949] Breaking affinity for irq 23 
[ 2747.550137] CPU 3 is now offline 
[ 2747.550143] SMP alternatives: switching to UP code 
[ 2747.556265] Extended CMOS year: 2000 
[ 2747.556346] PM: Creating hibernation image: 
[ 2747.560019] PM: Need to copy 93979 pages 
[ 2747.560019] PM: Normal pages needed: 40940 + 1024, available pages: 186250 
[ 2747.560019] PM: Restoring platform NVS memory 
[ 2747.560019] CPU0: Thermal monitoring enabled (TM2) 
[ 2747.560019] Extended CMOS year: 2000 
[ 2747.560019] Enabling non-boot CPUs ... 
[ 2747.560019] SMP alternatives: switching to SMP code 
[ 2747.562041] Booting processor 1 APIC 0x2 ip 0x6000 
[ 2747.543679] Initializing CPU#1 
[ 2747.543679] CPU: L1 I cache: 32K, L1 D cache: 24K 
[ 2747.543679] CPU: L2 cache: 512K 
[ 2747.543679] CPU: Physical Processor ID: 0 
[ 2747.543679] CPU: Processor Core ID: 1 
[ 2747.543679] CPU1: Thermal monitoring enabled (TM2) 
[ 2747.652126] CPU1: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02 
[ 2747.652292] CPU0 attaching NULL sched-domain. 
[ 2747.680038] CPU0 attaching sched-domain: 
[ 2747.680045]  domain 0: span 0-1 level CPU 
[ 2747.680050]   groups: 0 1 
[ 2747.680059] CPU1 attaching sched-domain: 
[ 2747.680064]  domain 0: span 0-1 level CPU 
[ 2747.680068]   groups: 1 0 
[ 2747.684034] CPU1 is up 
[ 2747.684762] Booting processor 2 APIC 0x1 ip 0x6000 
[ 2747.547054] Initializing CPU#2 
[ 2747.547054] CPU: L1 I cache: 32K, L1 D cache: 24K 
[ 2747.547054] CPU: L2 cache: 512K 
[ 2747.547054] CPU: Physical Processor ID: 0 
[ 2747.547054] CPU: Processor Core ID: 0 
[ 2747.547054] CPU2: Thermal monitoring enabled (TM2) 
[ 2747.772084] CPU2: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02 
[ 2747.772245] CPU0 attaching NULL sched-domain. 
[ 2747.772252] CPU1 attaching NULL sched-domain. 
[ 2747.824034] CPU0 attaching sched-domain: 
[ 2747.824041]  domain 0: span 0,2 level SIBLING 
[ 2747.824047]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589) 
[ 2747.824058]   domain 1: span 0,2 level MC 
[ 2747.824062]    groups: 0,2 (cpu_power = 1178) 
[ 2747.824070]    domain 2: span 0-2 level CPU 
[ 2747.824075]     groups: 0,2 (cpu_power = 1178) 1 
[ 2747.824085] CPU1 attaching sched-domain: 
[ 2747.824089]  domain 0: span 0-2 level CPU 
[ 2747.824094]   groups: 1 0,2 (cpu_power = 1178) 
[ 2747.824104] CPU2 attaching sched-domain: 
[ 2747.824108]  domain 0: span 0,2 level SIBLING 
[ 2747.824113]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589) 
[ 2747.824123]   domain 1: span 0,2 level MC 
[ 2747.824127]    groups: 0,2 (cpu_power = 1178) 
[ 2747.824135]    domain 2: span 0-2 level CPU 
[ 2747.824139]     groups: 0,2 (cpu_power = 1178) 1 
[ 2747.825239] CPU2 is up 
[ 2747.826034] Booting processor 3 APIC 0x3 ip 0x6000 
[ 2747.555447] Initializing CPU#3 
[ 2747.555447] CPU: L1 I cache: 32K, L1 D cache: 24K 
[ 2747.555447] CPU: L2 cache: 512K 
[ 2747.555447] CPU: Physical Processor ID: 0 
[ 2747.555447] CPU: Processor Core ID: 1 
[ 2747.555447] CPU3: Thermal monitoring enabled (TM2) 
[ 2747.916115] CPU3: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02 
[ 2747.916302] CPU0 attaching NULL sched-domain. 
[ 2747.916311] CPU1 attaching NULL sched-domain. 
[ 2747.916317] CPU2 attaching NULL sched-domain. 
[ 2747.964035] CPU0 attaching sched-domain: 
[ 2747.964042]  domain 0: span 0,2 level SIBLING 
[ 2747.964047]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589) 
[ 2747.964058]   domain 1: span 0,2 level MC 
[ 2747.964063]    groups: 0,2 (cpu_power = 1178) 
[ 2747.964071]    domain 2: span 0-3 level CPU 
[ 2747.964075]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178) 
[ 2747.964087] CPU1 attaching sched-domain: 
[ 2747.964092]  domain 0: span 1,3 level SIBLING 
[ 2747.964097]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589) 
[ 2747.964107]   domain 1: span 1,3 level MC 
[ 2747.964111]    groups: 1,3 (cpu_power = 1178) 
[ 2747.964119]    domain 2: span 0-3 level CPU 
[ 2747.964123]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178) 
[ 2747.964136] CPU2 attaching sched-domain: 
[ 2747.964140]  domain 0: span 0,2 level SIBLING 
[ 2747.964145]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589) 
[ 2747.964155]   domain 1: span 0,2 level MC 
[ 2747.964159]    groups: 0,2 (cpu_power = 1178) 
[ 2747.964167]    domain 2: span 0-3 level CPU 
[ 2747.964171]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178) 
[ 2747.964183] CPU3 attaching sched-domain: 
[ 2747.964187]  domain 0: span 1,3 level SIBLING 
[ 2747.964192]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589) 
[ 2747.964202]   domain 1: span 1,3 level MC 
[ 2747.964206]    groups: 1,3 (cpu_power = 1178) 
[ 2747.964214]    domain 2: span 0-3 level CPU 
[ 2747.964218]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178) 
[ 2747.965881] CPU3 is up 
[ 2747.967673] ACPI: Waking up from system sleep state S4 
[ 2747.968320] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002) 
[ 2747.968771] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2880001, writing 0x2880005) 
[ 2747.968805] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00001, writing 0x2b00005) 
[ 2747.969062] iwl3945 0000:02:00.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100406) 
[ 2747.969384] PM: early restore of devices complete after 1.199 msecs 
[ 2748.048795] i915 0000:00:02.0: setting latency timer to 64 
[ 2748.168176] PM: restore of drv:i915 dev:0000:00:02.0 complete after 119.390 msecs 
[ 2748.168200] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[ 2748.168210] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[ 2748.168255] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[ 2748.168292] usb usb2: root hub lost power or was reset 
[ 2748.168332] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[ 2748.168367] usb usb3: root hub lost power or was reset 
[ 2748.168388] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[ 2748.168423] usb usb4: root hub lost power or was reset 
[ 2748.168445] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
[ 2748.168479] usb usb5: root hub lost power or was reset 
[ 2748.168501] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[ 2748.168508] usb usb1: root hub lost power or was reset 
[ 2748.172389] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[ 2748.172405] pci 0000:00:1e.0: setting latency timer to 64 
[ 2748.172424] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[ 2748.172431] ata_piix 0000:00:1f.1: setting latency timer to 64 
[ 2748.177509] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[ 2748.177518] ata_piix 0000:00:1f.2: setting latency timer to 64 
[ 2748.342954] ata4.01: NODEV after polling detection 
[ 2748.348444] ata4.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out 
[ 2748.348452] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out 
[ 2748.348461] ata4.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out 
[ 2748.348667] ata3.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out 
[ 2748.348675] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out 
[ 2748.349039] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded 
[ 2748.349047] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out 
[ 2748.364314] ata4.00: configured for UDMA/100 
[ 2748.373157] ata3.00: configured for UDMA/133 
[ 2748.389152] ata3.00: configured for UDMA/133 
[ 2748.389159] ata3: EH complete 
[ 2748.444058] PM: restore of drv:usb dev:usb1 complete after 258.237 msecs 
[ 2748.692028] PM: restore of drv:usb dev:usb2 complete after 247.952 msecs 
[ 2748.705175] sd 2:0:0:0: [sda] Starting disk 
[ 2748.972026] usb 2-1: reset low speed USB device using uhci_hcd and address 2 
[ 2749.279086] PM: restore of drv:usb dev:2-1 complete after 564.130 msecs 
[ 2749.536025] usb 2-2: reset low speed USB device using uhci_hcd and address 3 
[ 2749.848106] PM: restore of drv:usb dev:2-2 complete after 569.004 msecs 
[ 2749.848314] PM: restore of devices complete after 1802.612 msecs 
[ 2749.848626] PM: Image restored successfully. 
[ 2749.848631] Restarting tasks ... done. 
[ 2749.876206] PM: Basic memory bitmaps freed 
[ 2751.126120] r8169: eth0: link down 
[ 2751.126711] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[ 2751.144329] iwl3945 0000:02:00.0: Hardware error detected.  Restarting. 
[ 2751.148339] iwl3945 0000:02:00.0: Hardware error detected.  Restarting. 
[ 2751.172350] iwl3945 0000:02:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a1, s/b 0xf802020 
[ 2753.172035] iwl3945 0000:02:00.0: Wait for START_ALIVE timeout after 2000ms. 
[ 2753.179996] iwl3945 0000:02:00.0: Hardware error detected.  Restarting. 
[ 2753.204011] iwl3945 0000:02:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xa5a5a5a1, s/b 0xf802020 
[ 2755.200060] iwl3945 0000:02:00.0: Wait for START_ALIVE timeout after 2000ms. 
[ 2770.480030] usb 1-5: new high speed USB device using ehci_hcd and address 5 
[ 2770.786331] usb 1-5: configuration #1 chosen from 1 choice 
[ 2770.786884] scsi5 : SCSI emulation for USB Mass Storage devices 
[ 2770.787203] usb-storage: device found at 5 
[ 2770.787210] usb-storage: waiting for device to settle before scanning 
[ 2775.784272] usb-storage: device scan complete 
[ 2775.956859] scsi 5:0:0:0: Direct-Access     JetFlash TS2GJFV30        8.07 PQ: 0 ANSI: 2 
[ 2775.958404] sd 5:0:0:0: Attached scsi generic sg2 type 0 
[ 2775.959686] sd 5:0:0:0: [sdb] 4014078 512-byte logical blocks: (2.05 GB/1.91 GiB) 
[ 2775.960227] sd 5:0:0:0: [sdb] Write Protect is off 
[ 2775.960238] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00 
[ 2775.960246] sd 5:0:0:0: [sdb] Assuming drive cache: write through 
[ 2775.963361] sd 5:0:0:0: [sdb] Assuming drive cache: write through 
[ 2775.963386]  sdb: sdb1 
[ 2775.966710] sd 5:0:0:0: [sdb] Assuming drive cache: write through 
[ 2775.966727] sd 5:0:0:0: [sdb] Attached SCSI removable disk 
[B]
6) sudo lshw -C network[/B]
 *-network DISABLED 
       description: Wireless interface 
       product: PRO/Wireless 3945ABG [Golan] Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 02 
       serial: 00:13:02:46:f3:fb 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg 
       resources: irq:29 memory:febff000-febfffff 
**7) iwlist scan**
wlan0     Failed to read scan data : Network is down 

**8)lsb_release -d**
Description:    Ubuntu 10.04 LTS

**9) uname -mr**
2.6.32-21-generic i686

**10)sudo /etc/init.d/networking restart**
* Reconfiguring network interfaces...                                   [ OK ] 

THANKS FOR ANY HELP
-Colin

---

