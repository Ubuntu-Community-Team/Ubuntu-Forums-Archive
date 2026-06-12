---
title: "Broadcom Wireless Card"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by bridabom73 on 2010-07-03
I know everyone has this problem and I read so many topics about it and nothing worked. My Broadcom Wireless network card doesn't work, just like everyone else's. I've been using a Belkin Wireless USB adapter to access the internet, but then the other day when I was watching a YouTube video, the video stopped loading and my network was disconnected. I look through the list of networks available and see that my network is listed twice. So then I look at the orange light on the front of my computer, and it's blue. So my Broadcom card somehow started working, so I stopped using the Belkin adapter. But then I had to restart my computer, and when it restarted, the Broadcom card stopped working. It hasn't worked since then, and in the Hardware Drivers, the drivers are installed correctly. I don't know what's wrong, and I couldn't find anything with this exact problem. Thanks for your help in advance.

---

### Post by Metaljaz on 2010-07-03
If this is a laptop double check to make sure you didn't accidentally turn off the wireless. Usually a Function key like F2 or something. 
If that is not the case tell us what version of Ubuntu you are running and the results of the following command (run the command from the terminal window):

lspci

look for the line that resembles this one and post it here:
08:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)

I have a dell laptop with a broadcom chipset (as you can see) and it works like a charm.

---

### Post by bridabom73 on 2010-07-03
Sorry I forgot to tell you. I'm using Ubuntu 10.04.

```
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
```

I have a Compaq Presario F500, so it might be different.

---

### Post by Metaljaz on 2010-07-03
Try resetting your router by unplugging it, waiting about 30 secs and plugging it back in. Restart the computer and see if it now finds your router and connects.

---

### Post by bridabom73 on 2010-07-03
I've tried that before, but I don't think it'll work because the wireless card isn't even on. The light on the computer stay orange no matter what position the switch is in. I've tried reconstructing what happened the day that it worked, but I can't get the light to turn blue again.

---

### Post by roosh on 2010-07-03
How long ago was this? Also could you post the output of ```
lsmod
```

---

### Post by bridabom73 on 2010-07-03
```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxnetadp              5171  0 
vboxnetflt             15064  0 
vboxdrv              1792472  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    28841  1 
arc4                    1473  2 
joydev                 11072  0 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
zd1211rw               48591  0 
mac80211              238448  1 zd1211rw
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    71106  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              148546  2 zd1211rw,mac80211
nvidia              10832442  45 
psmouse                64576  0 
serio_raw               4918  0 
k8temp                  3912  0 
vga16fb                12757  1 
i2c_nforce2             6099  0 
vgastate                9857  1 vga16fb
edac_core              45423  0 
edac_mce_amd            9278  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
ndiswrapper           244768  0 
lib80211_crypt_tkip     8676  0 
lib80211                6151  1 lib80211_crypt_tkip
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
sata_nv                23778  2 
pata_amd               11962  0 
forcedeth              55592  0
```

How long ago did it work? I think it was two days ago.

---

### Post by roosh on 2010-07-03
After some googling, I found this page here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

It seems that you can activate a proprietary driver by simply going to: System / Administration / Hardware Drivers

See if that works.

---

### Post by bridabom73 on 2010-07-03
Unfortunately, that was already activated, and while I was waiting to see if you responded, I deactivated it, restarted, activated it, and restarted again, and it still doesn't work.

---

### Post by roosh on 2010-07-03
Take a look at the link in my previous post.
Under "Installing BCM43xx drivers" it seems there is an automated installer if you have the right PCI device. In a terminal type: ```
lspci -vnn | grep 14e4
``` and click enter post the output.

---

### Post by bridabom73 on 2010-07-03
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
```

EDIT: I just read that link now and did what it said and it works now. :D Thanks for your help. I'm going to restart now and hope that it still works.

EDIT 2: Okay, so I restarted and it didn't work, but I ran the "sudo modprobe wl" command again and then it started working again. I put that in the System > Preferences > Startup Applications list, but it didn't work when I restarted my computer again. Is there any way to get that command to run automatically when I start my computer, or do I have to manually run it every time I boot up?

---

### Post by roosh on 2010-07-03
No problem :)
If it works, I would disable the proprietary hardware driver that you said didn't work before.
Also, if it works, please add [solved] to the header of this thread.

---

### Post by bridabom73 on 2010-07-03
Bump. I'm not sure if you saw my edit on my last post. I didn't see your post until after I had edited it.

---

### Post by roosh on 2010-07-03
Ok so go to Computer --> filesystem --> etc and look for a file either called modules or modules.conf
Remember which one is there. Now, open a terminal and type:
```
sudo gedit /etc/modules
```
or ```
sudo gedit /etc/modules.conf
``` depending on which you have. Then a text editor will pop up and display some text. At the end of the file, add the name of the module, for you add: ```
wl
``` Then save. Reboot to see if it works.

---

### Post by bridabom73 on 2010-07-03
I already had "wl" in /etc/modules. I changed it to modules.conf to see if it would change anything, but it still doesn't load automatically.

---

### Post by roosh on 2010-07-03
Hmm that's interesting. Maybe it just takes time for your card to load? When you boot up, before typing sudo modprobe wl, type in lsmod in the terminal. Then do the same after typing sudo modprobe wl. Post the outputs of both lsmod's here.

---

### Post by bridabom73 on 2010-07-03
```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
vboxnetadp              5171  0 
vboxnetflt             15064  0 
vboxdrv              1792472  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    28841  1 
joydev                 11072  0 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     8676  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    71106  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64576  0 
nvidia              10832442  41 
serio_raw               4918  0 
vga16fb                12757  1 
i2c_nforce2             6099  0 
vgastate                9857  1 vga16fb
k8temp                  3912  0 
lib80211                6151  1 lib80211_crypt_tkip
edac_core              45423  0 
edac_mce_amd            9278  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
forcedeth              55592  0 
pata_amd               11962  0 
sata_nv                23778  2
```
```
Module                  Size  Used by
wl                   1964968  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
vboxnetadp              5171  0 
vboxnetflt             15064  0 
vboxdrv              1792472  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    28841  1 
joydev                 11072  0 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     8676  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    71106  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64576  0 
nvidia              10832442  41 
serio_raw               4918  0 
vga16fb                12757  1 
i2c_nforce2             6099  0 
vgastate                9857  1 vga16fb
k8temp                  3912  0 
lib80211                6151  2 wl,lib80211_crypt_tkip
edac_core              45423  0 
edac_mce_amd            9278  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
forcedeth              55592  0 
pata_amd               11962  0 
sata_nv                23778  2
```

---

### Post by roosh on 2010-07-03
Ok, it doesn't seem to be loading at boot
do:
```
dmesg >> ~/Desktop/dmesglog
```
On your desktop, a file called dmesglog will be created. Paste its contents here.

---

### Post by bridabom73 on 2010-07-03
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-23-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=567e224b-f984-4a70-9ab4-e38df8563294 ro vga=799 quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037f00000 (usable)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000037f15000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037f15000 - 0000000037f80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x37f00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000037f00000 (usable)
[    0.000000]  modified: 0000000037f00000 - 0000000037f15000 (ACPI data)
[    0.000000]  modified: 0000000037f15000 - 0000000037f80000 (ACPI NVS)
[    0.000000]  modified: 0000000037f80000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037f00000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0037e00000 page 2M
[    0.000000]  0037e00000 - 0037f00000 page 4k
[    0.000000] kernel direct mapping tables up to 37f00000 @ 8000-b000
[    0.000000] RAMDISK: 2978d000 - 29f7fc62
[    0.000000] ACPI: RSDP 00000000000f8930 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 0000000037f0c037 00040 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 0000000037f14b58 00074 (v01 HP     MCP51M   06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT 0000000037f0c077 08AE1 (v01 HP       MCP51M 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 0000000037f15fc0 00040
[    0.000000] ACPI: SSDT 0000000037f14bcc 001C4 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: MCFG 0000000037f14d90 0003C (v01 HP       MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 0000000037f14dcc 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 0000000037f14e04 0005E (v01 HP     ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 0000000037f14e62 00028 (v01     HP $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 0000000037f14e8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000037f00000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000037f00000
[    0.000000]   NODE_DATA [0000000000009000 - 000000000000dfff]
[    0.000000]   bootmap [000000000000e000 -  0000000000014fdf] pages 7
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0037f00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a2de64]    TEXT DATA BSS ==> [0001000000 - 0001a2de64]
[    0.000000]   #3 [002978d000 - 0029f7fc62]          RAMDISK ==> [002978d000 - 0029f7fc62]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [0001a2e000 - 0001a2e164]              BRK ==> [0001a2e000 - 0001a2e164]
[    0.000000]   #6 [0000008000 - 0000009000]          PGTABLE ==> [0000008000 - 0000009000]
[    0.000000] found SMP MP-table at [ffff8800000f8960] f8960
[    0.000000]  [ffffea0000000000-ffffea0000dfffff] PMD -> [ffff880002000000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00037f00
[    0.000000] On node 0 totalpages: 229016
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3834 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3077 pages used for memmap
[    0.000000]   DMA32 zone: 221947 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 225781
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=567e224b-f984-4a70-9ab4-e38df8563294 ro vga=799 quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 7d60000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 882772k/916480k available (5419k kernel code, 416k absent, 33292k reserved, 2974k data, 880k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 9175040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1707.902 MHz processor.
[    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3415.80 BogoMIPS (lpj=17079020)
[    0.010041] Security Framework initialized
[    0.010064] AppArmor: AppArmor initialized
[    0.010201] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.011084] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.011513] Mount-cache hash table entries: 256
[    0.011686] Initializing cgroup subsys ns
[    0.011690] Initializing cgroup subsys cpuacct
[    0.011696] Initializing cgroup subsys memory
[    0.011706] Initializing cgroup subsys devices
[    0.011709] Initializing cgroup subsys freezer
[    0.011712] Initializing cgroup subsys net_cls
[    0.011736] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.011739] CPU: L2 Cache: 256K (64 bytes/line)
[    0.011742] CPU 0/0x0 -> Node 0
[    0.011745] tseg: 0037f80000
[    0.011747] CPU: Physical Processor ID: 0
[    0.011749] CPU: Processor Core ID: 0
[    0.011753] mce: CPU supports 5 MCE banks
[    0.011765] using C1E aware idle routine
[    0.011767] Performance Events: AMD PMU driver.
[    0.011773] ... version:                0
[    0.011775] ... bit width:              48
[    0.011777] ... generic registers:      4
[    0.011779] ... value mask:             0000ffffffffffff
[    0.011782] ... max period:             00007fffffffffff
[    0.011784] ... fixed-purpose events:   0
[    0.011786] ... event mask:             000000000000000f
[    0.013797] ACPI: Core revision 20090903
[    0.030010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030017] ftrace: allocating 22524 entries in 89 pages
[    0.038389] Setting APIC routing to flat
[    0.038932] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.139528] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 stepping 01
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] System has AMD C1E enabled
[    0.020000] Switch to broadcast mode on CPU1
[    0.290122] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 stepping 01
[    0.290145] Brought up 2 CPUs
[    0.290149] Total of 2 processors activated (6831.37 BogoMIPS).
[    0.290377] CPU0 attaching sched-domain:
[    0.290381]  domain 0: span 0-1 level MC
[    0.290384]   groups: 0 1
[    0.290391] CPU1 attaching sched-domain:
[    0.290393]  domain 0: span 0-1 level MC
[    0.290396]   groups: 1 0
[    0.290508] Switch to broadcast mode on CPU0
[    0.290508] devtmpfs: initialized
[    0.290508] regulator: core version 0.5
[    0.290508] Time: 20:02:25  Date: 07/03/10
[    0.290508] NET: Registered protocol family 16
[    0.290508] Trying to unpack rootfs image as initramfs...
[    0.290508] node 0 link 0: io port [1000, fffff]
[    0.290508] TOM: 0000000040000000 aka 1024M
[    0.290508] node 0 link 0: mmio [e0000000, efffffff]
[    0.290508] node 0 link 0: mmio [a0000, bffff]
[    0.290508] node 0 link 0: mmio [40000000, fe0bffff]
[    0.290508] bus: [00,ff] on node 0 link 0
[    0.290508] bus: 00 index 0 io port: [0, ffff]
[    0.290508] bus: 00 index 1 mmio: [40000000, fcffffffff]
[    0.290508] bus: 00 index 2 mmio: [a0000, bffff]
[    0.290508] ACPI: bus type pci registered
[    0.290508] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6
[    0.290508] PCI: MCFG area at e0000000 reserved in E820
[    0.290650] PCI: Using MMCONFIG at e0000000 - e06fffff
[    0.290653] PCI: Using configuration type 1 for base access
[    0.300173] bio: create slab <bio-0> at 0
[    0.300999] ACPI: EC: Look up EC in DSDT
[    0.304484] ACPI: BIOS _OSI(Linux) query ignored
[    0.304920] ACPI: Interpreter enabled
[    0.304928] ACPI: (supports S0 S3 S4 S5)
[    0.304954] ACPI: Using IOAPIC for interrupt routing
[    0.312281] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.312620] ACPI: No dock devices found.
[    0.312796] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.313099] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313103] pci 0000:00:02.0: PME# disabled
[    0.313146] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313149] pci 0000:00:03.0: PME# disabled
[    0.313173] pci 0000:00:05.0: reg 10 32bit mmio: [0xb2000000-0xb2ffffff]
[    0.313179] pci 0000:00:05.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.313185] pci 0000:00:05.0: reg 1c 64bit mmio: [0xb1000000-0xb1ffffff]
[    0.313191] pci 0000:00:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.313381] pci 0000:00:0a.0: reg 10 io port: [0x1d00-0x1d7f]
[    0.313446] pci 0000:00:0a.1: reg 20 io port: [0x3040-0x307f]
[    0.313452] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.313478] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.313484] pci 0000:00:0a.1: PME# disabled
[    0.313519] pci 0000:00:0a.3: reg 10 32bit mmio: [0xb0040000-0xb007ffff]
[    0.313614] pci 0000:00:0b.0: reg 10 32bit mmio: [0xb0004000-0xb0004fff]
[    0.313644] pci 0000:00:0b.0: supports D1 D2
[    0.313647] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313651] pci 0000:00:0b.0: PME# disabled
[    0.313680] pci 0000:00:0b.1: reg 10 32bit mmio: [0xb0005000-0xb00050ff]
[    0.313713] pci 0000:00:0b.1: supports D1 D2
[    0.313715] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313719] pci 0000:00:0b.1: PME# disabled
[    0.313764] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.313811] pci 0000:00:0e.0: reg 10 io port: [0x30c0-0x30c7]
[    0.313817] pci 0000:00:0e.0: reg 14 io port: [0x30b4-0x30b7]
[    0.313822] pci 0000:00:0e.0: reg 18 io port: [0x30b8-0x30bf]
[    0.313828] pci 0000:00:0e.0: reg 1c io port: [0x30b0-0x30b3]
[    0.313833] pci 0000:00:0e.0: reg 20 io port: [0x3090-0x309f]
[    0.313839] pci 0000:00:0e.0: reg 24 32bit mmio: [0xb0006000-0xb0006fff]
[    0.313938] pci 0000:00:10.1: reg 10 32bit mmio: [0xb0000000-0xb0003fff]
[    0.313974] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.313978] pci 0000:00:10.1: PME# disabled
[    0.314016] pci 0000:00:14.0: reg 10 32bit mmio: [0xb0008000-0xb0008fff]
[    0.314021] pci 0000:00:14.0: reg 14 io port: [0x30e0-0x30e7]
[    0.314046] pci 0000:00:14.0: supports D1 D2
[    0.314048] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.314052] pci 0000:00:14.0: PME# disabled
[    0.314191] pci 0000:00:02.0: bridge io port: [0x4000-0x4fff]
[    0.314194] pci 0000:00:02.0: bridge 32bit mmio: [0xb4000000-0xb7ffffff]
[    0.314199] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xd01fffff]
[    0.314241] pci 0000:03:00.0: reg 10 64bit mmio: [0xb8000000-0xb8003fff]
[    0.314287] pci 0000:03:00.0: supports D1 D2
[    0.314341] pci 0000:00:03.0: bridge 32bit mmio: [0xb8000000-0xbbffffff]
[    0.314382] pci 0000:00:10.0: transparent bridge
[    0.314399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.314520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.314569] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.314611] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.356596] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.356830] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15)
[    0.357060] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.357291] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.357521] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.357751] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.357983] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.358213] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.358456] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.358688] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.358919] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.359152] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.359402] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.359648] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.359897] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.360165] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.360413] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.360675] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.360924] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.361075] vgaarb: device added: PCI:0000:00:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.361093] vgaarb: loaded
[    0.361232] SCSI subsystem initialized
[    0.361367] libata version 3.00 loaded.
[    0.361464] usbcore: registered new interface driver usbfs
[    0.361480] usbcore: registered new interface driver hub
[    0.361516] usbcore: registered new device driver usb
[    0.361775] ACPI: WMI: Mapper loaded
[    0.361778] PCI: Using ACPI for IRQ routing
[    0.361995] NetLabel: Initializing
[    0.361997] NetLabel:  domain hash size = 128
[    0.361999] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.362018] NetLabel:  unlabeled traffic allowed by default
[    0.362082] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.362089] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.380050] Switching to clocksource hpet
[    0.382453] AppArmor: AppArmor Filesystem Enabled
[    0.382483] pnp: PnP ACPI init
[    0.382505] ACPI: bus type pnp registered
[    0.385612] pnp: PnP ACPI: found 13 devices
[    0.385615] ACPI: ACPI bus type pnp unregistered
[    0.385631] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.385639] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.385643] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.385647] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.385651] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.385658] system 00:03: iomem range 0xe0000000-0xefffffff has been reserved
[    0.385666] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.385669] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.385673] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.385676] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.385680] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.385683] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.385687] system 00:04: ioport range 0x2000-0x203f has been reserved
[    0.385694] system 00:05: ioport range 0x360-0x361 has been reserved
[    0.385698] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.385701] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.390523] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.390527] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.390531] pci 0000:00:02.0:   MEM window: 0xb4000000-0xb7ffffff
[    0.390535] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000d01fffff
[    0.390540] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.390542] pci 0000:00:03.0:   IO window: disabled
[    0.390546] pci 0000:00:03.0:   MEM window: 0xb8000000-0xbbffffff
[    0.390549] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.390553] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.390555] pci 0000:00:10.0:   IO window: disabled
[    0.390559] pci 0000:00:10.0:   MEM window: disabled
[    0.390562] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.390575] pci 0000:00:02.0: setting latency timer to 64
[    0.390581] pci 0000:00:03.0: setting latency timer to 64
[    0.390587] pci 0000:00:10.0: setting latency timer to 64
[    0.390592] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.390596] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.390599] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]
[    0.390602] pci_bus 0000:01: resource 1 mem: [0xb4000000-0xb7ffffff]
[    0.390606] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd01fffff]
[    0.390609] pci_bus 0000:03: resource 1 mem: [0xb8000000-0xbbffffff]
[    0.390613] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.390616] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.390663] NET: Registered protocol family 2
[    0.390816] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.391550] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.393297] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.394103] TCP: Hash tables configured (established 131072 bind 65536)
[    0.394107] TCP reno registered
[    0.394228] NET: Registered protocol family 1
[    0.394262] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    0.394268] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.394312] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.394338] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.394346] pci 0000:00:05.0: Boot video device
[    0.596813] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.596870] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.596928] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.597137] Simple Boot Flag at 0x36 set to 0x1
[    0.597360] Scanning for low memory corruption every 60 seconds
[    0.597542] audit: initializing netlink socket (disabled)
[    0.597556] type=2000 audit(1278187344.596:1): initialized
[    0.608655] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.610837] VFS: Disk quotas dquot_6.5.2
[    0.610932] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.611885] fuse init (API version 7.13)
[    0.612014] msgmni has been set to 1724
[    0.612364] alg: No test for stdrng (krng)
[    0.612472] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.612476] io scheduler noop registered
[    0.612478] io scheduler anticipatory registered
[    0.612480] io scheduler deadline registered
[    0.612534] io scheduler cfq registered (default)
[    0.612764]   alloc irq_desc for 24 on node 0
[    0.612766]   alloc kstat_irqs on node 0
[    0.612776] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.612783] pcieport 0000:00:02.0: setting latency timer to 64
[    0.612917]   alloc irq_desc for 25 on node 0
[    0.612919]   alloc kstat_irqs on node 0
[    0.612925] pcieport 0000:00:03.0: irq 25 for MSI/MSI-X
[    0.612930] pcieport 0000:00:03.0: setting latency timer to 64
[    0.613005] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.613042] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.613647] ACPI: AC Adapter [ACAD] (on-line)
[    0.613763] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.613768] ACPI: Power Button [PWRB]
[    0.613828] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.613831] ACPI: Sleep Button [SLPB]
[    0.613890] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.614167] ACPI: Lid Switch [LID]
[    0.614252] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.614255] ACPI: Power Button [PWRF]
[    0.614600] ACPI: processor limited to max C-state 1
[    0.614640] processor LNXCPU:00: registered as cooling_device0
[    0.614692] processor LNXCPU:01: registered as cooling_device1
[    0.618456] thermal LNXTHERM:01: registered as thermal_zone0
[    0.618467] ACPI: Thermal Zone [THRM] (72 C)
[    0.620601] Linux agpgart interface v0.103
[    0.620654] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.622190] brd: module loaded
[    0.622784] loop: module loaded
[    0.622917] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.623321] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.623409] pata_acpi 0000:00:0e.0: enabling device (0005 -> 0007)
[    0.623942] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    0.623948]   alloc irq_desc for 23 on node 0
[    0.623950]   alloc kstat_irqs on node 0
[    0.623965] pata_acpi 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    0.623999] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.624011] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.624530] Fixed MDIO Bus: probed
[    0.624571] PPP generic driver version 2.4.2
[    0.624641] tun: Universal TUN/TAP device driver, 1.6
[    0.624644] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.624771] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.625284] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.625290]   alloc irq_desc for 22 on node 0
[    0.625292]   alloc kstat_irqs on node 0
[    0.625304] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    0.625325] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.625329] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.625398] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.625432] ehci_hcd 0000:00:0b.1: debug port 1
[    0.625443] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.625475] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xb0005000
[    0.650042] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.650153] usb usb1: configuration #1 chosen from 1 choice
[    0.650187] hub 1-0:1.0: USB hub found
[    0.650197] hub 1-0:1.0: 8 ports detected
[    0.650294] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.650803] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[    0.650809]   alloc irq_desc for 21 on node 0
[    0.650811]   alloc kstat_irqs on node 0
[    0.650823] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 21 (level, high) -> IRQ 21
[    0.650850] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.650854] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.650936] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.650977] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xb0004000
[    0.712144] usb usb2: configuration #1 chosen from 1 choice
[    0.712177] hub 2-0:1.0: USB hub found
[    0.712189] hub 2-0:1.0: 8 ports detected
[    0.712285] uhci_hcd: USB Universal Host Controller Interface driver
[    0.712387] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.723750] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.723759] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.723925] mice: PS/2 mouse device common for all mice
[    0.724539] rtc_cmos 00:09: RTC can wake from S4
[    0.724616] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.724657] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.724839] device-mapper: uevent: version 1.0.3
[    0.725008] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.725116] device-mapper: multipath: version 1.1.0 loaded
[    0.725119] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.725354] cpuidle: using governor ladder
[    0.725356] cpuidle: using governor menu
[    0.725814] TCP cubic registered
[    0.725988] NET: Registered protocol family 10
[    0.726578] lo: Disabled Privacy Extensions
[    0.726926] NET: Registered protocol family 17
[    0.726976] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 processors (2 cpu cores) (version 2.20.00)
[    0.727027] powernow-k8:    0 : fid 0x9 (1700 MHz), vid 0x13
[    0.727030] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[    0.727033] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
[    0.727198] PM: Resume from disk failed.
[    0.727216] registered taskstats version 1
[    0.727576]   Magic number: 2:314:42
[    0.727586] bdi 7:7: hash matches
[    0.727704] rtc_cmos 00:09: setting system clock to 2010-07-03 20:02:25 UTC (1278187345)
[    0.727708] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.727710] EDD information not available.
[    0.734732] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.744610] Freeing initrd memory: 8139k freed
[    0.880434] ACPI: Battery Slot [BAT0] (battery present)
[    1.130490] Freeing unused kernel memory: 880k freed
[    1.131065] Write protecting the kernel read-only data: 7692k
[    1.157918] udev: starting version 151
[    1.340922] pata_amd 0000:00:0d.0: version 0.4.1
[    1.340988] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.346157] scsi0 : pata_amd
[    1.350437] scsi1 : pata_amd
[    1.351329] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.351333] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.354400] sata_nv 0000:00:0e.0: version 3.5
[    1.354419] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    1.354422] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.354489] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.354683] scsi2 : sata_nv
[    1.354824] scsi3 : sata_nv
[    1.355045] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    1.355050] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    1.355224] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.355629] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.355635]   alloc irq_desc for 20 on node 0
[    1.355637]   alloc kstat_irqs on node 0
[    1.355650] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    1.355656] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.355720] nv_probe: set workaround bit for reversed mac addr
[    1.540374] ata1.00: ATAPI: Slimtype DVD A  DS8A1P, CH63, max MWDMA2
[    1.540405] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    1.600298] ata1.00: configured for MWDMA2
[    1.604175] scsi 0:0:0:0: CD-ROM            Slimtype DVD A  DS8A1P    CH63 PQ: 0 ANSI: 5
[    1.614974] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.614979] Uniform CD-ROM driver Revision: 3.20
[    1.615144] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.615236] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.615343] ata2: port disabled. ignoring.
[    1.840072] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.860245] ata3.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC7BP, max UDMA/100
[    1.860248] ata3.00: 156301488 sectors, multi 16: LBA48 
[    1.881384] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:e3:0c:c8
[    1.881388] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    1.900284] ata3.00: configured for UDMA/100
[    1.900415] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    1.900649] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.900654] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.900730] sd 2:0:0:0: [sda] Write Protect is off
[    1.900734] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.900764] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.900970]  sda: sda1 sda2 < sda5 >
[    1.946240] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.240731] ata4: SATA link down (SStatus 0 SControl 300)
[    2.530378] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   17.968934] udev: starting version 151
[   18.266675] acpi device:22: registered as cooling_device2
[   18.266868] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   18.266933] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   18.448939] EDAC MC: Ver: 2.1.0 Jun 11 2010
[   18.450239] lib80211: common routines for IEEE802.11 drivers
[   18.450244] lib80211_crypt: registered algorithm 'NULL'
[   18.452830] vga16fb: initializing
[   18.452837] vga16fb: mapped to 0xffff8800000a0000
[   18.452930] fb0: VGA16 VGA frame buffer device
[   18.465483] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   18.537035] nvidia: module license 'NVIDIA' taints kernel.
[   18.537041] Disabling lock debugging due to kernel taint
[   18.552907] type=1505 audit(1278201763.324:2):  operation="profile_load" pid=647 name="/sbin/dhclient3"
[   18.553241] type=1505 audit(1278201763.324:3):  operation="profile_load" pid=647 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.553428] type=1505 audit(1278201763.324:4):  operation="profile_load" pid=647 name="/usr/lib/connman/scripts/dhclient-script"
[   19.056564] EDAC amd64_edac:  Ver: 3.2.0 Jun 11 2010
[   19.298460] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   19.298489] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   19.298639] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   19.298648] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   19.298650]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   19.298652]  (Note that use of the override may cause unknown side effects.)
[   19.298667] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   19.299633] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 19
[   19.299639]   alloc irq_desc for 19 on node 0
[   19.299641]   alloc kstat_irqs on node 0
[   19.299655] wl 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, high) -> IRQ 19
[   19.299661] wl 0000:03:00.0: setting latency timer to 64
[   19.307804] nvidia 0000:00:05.0: power state changed by ACPI to D0
[   19.307844] nvidia 0000:00:05.0: power state changed by ACPI to D0
[   19.308234] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   19.308240]   alloc irq_desc for 18 on node 0
[   19.308242]   alloc kstat_irqs on node 0
[   19.308254] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18
[   19.308262] nvidia 0000:00:05.0: setting latency timer to 64
[   19.308268] vgaarb: device changed decodes: PCI:0000:00:05.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.308548] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[   19.322679] lib80211_crypt: registered algorithm 'TKIP'
[   19.322898] eth1: Broadcom BCM4311 802.11 Hybrid Wireless Controller 5.60.48.36 
[   19.360449] Console: switching to colour frame buffer device 80x30
[   19.380722] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   19.380731]   alloc irq_desc for 17 on node 0
[   19.380733]   alloc kstat_irqs on node 0
[   19.380750] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 17 (level, high) -> IRQ 17
[   19.380756] hda_intel: Disable MSI for Nvidia chipset
[   19.380815] HDA Intel 0000:00:10.1: setting latency timer to 64
[   19.381857] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   20.099479] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   20.157810] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   21.029922] type=1505 audit(1278201765.792:5):  operation="profile_load" pid=824 name="/usr/share/gdm/guest-session/Xsession"
[   21.037718] type=1505 audit(1278201765.802:6):  operation="profile_replace" pid=826 name="/sbin/dhclient3"
[   21.038067] type=1505 audit(1278201765.802:7):  operation="profile_replace" pid=826 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.038267] type=1505 audit(1278201765.802:8):  operation="profile_replace" pid=826 name="/usr/lib/connman/scripts/dhclient-script"
[   21.059025] type=1505 audit(1278201765.822:9):  operation="profile_load" pid=830 name="/usr/bin/evince"
[   21.063505] type=1505 audit(1278201765.832:10):  operation="profile_load" pid=830 name="/usr/bin/evince-previewer"
[   21.066301] type=1505 audit(1278201765.832:11):  operation="profile_load" pid=830 name="/usr/bin/evince-thumbnailer"
[   21.234736] eth0: no link during initialization.
[   21.235249] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.527949] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   21.527955] vboxdrv: Successfully done.
[   21.527958] vboxdrv: Found 2 processor cores.
[   21.529133] VBoxDrv: dbg - g_abExecMemory=ffffffffa0f1fca0
[   21.529162] vboxdrv: fAsync=1 offMin=0x9440d offMax=0x9440d
[   21.530783] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   21.530790] vboxdrv: Successfully loaded version 3.2.6 (interface 0x00140001).
[   23.679306] lp: driver loaded but no devices found
[   23.686838] ppdev: user-space parallel port driver
[   24.200245] wl 0000:03:00.0: PCI INT A disabled
[   53.072734] wl 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 19 (level, high) -> IRQ 19
[   53.072744] wl 0000:03:00.0: setting latency timer to 64
[   53.077811] eth1: Broadcom BCM4311 802.11 Hybrid Wireless Controller 5.60.48.36 
[   67.546364] eth0: no link during initialization.
[   67.546956] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   77.652537] eth1: no IPv6 routers present
[   85.510043] Clocksource tsc unstable (delta = -175116362 ns)
```

---

### Post by roosh on 2010-07-03
Sorry, I can't see what's wrong here. I would suggest waiting for another person to help in this thread or posting another thread (maybe in a different section, as it's not really a wireless problem anymore). Good luck getting it to load on boot.

---

### Post by bridabom73 on 2010-07-03
Thanks anyway. I guess I'll just live with it for now. Maybe it'll fix itself.

---

