---
title: "stranges for the ndiswrapper"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by mpeng on 2006-06-13
Hi, 

I have used the ndiswrapper successfully in 5.10 version for my TL-WN220M, but after upgrade to 6.6. The wlan0 can not work for a long time with ths same driver. The dmesg shows as follow:

pengxf@pengxf:~$ dmesg | grep ndiswrapper
[4294700.816000] ndiswrapper version 1.17 loaded (preempt=yes,smp=no)
[4294700.881000] usbcore: registered new driver ndiswrapper
[4294820.048000] ndiswrapper: driver sis162u (Silicon Integrated Systems Corp.(1.03.09),07/28/2004,5.1.1039.1030) loaded
[4294825.796000] wlan0: ndiswrapper ethernet device 00:0a:eb:88:6a:db using driver sis162u, 0B3B:1613.F.conf
[4295020.680000]  [<d0c186a7>] wrap_alloc_urb+0xe7/0x290 [ndiswrapper]
[4295020.680000]  [<d0c18c10>] wrap_bulk_or_intr_trans+0x60/0x1b0 [ndiswrapper]
[4295020.680000]  [<d0c19769>] wrap_submit_irp+0xc9/0xd0 [ndiswrapper]
[4295020.680000]  [<d0c13551>] pdoDispatchDeviceControl+0x11/0x30 [ndiswrapper]
[4295020.681000]  [<d0c118b9>] IofCallDriver+0x29/0x50 [ndiswrapper]
[4295020.681000]  [<d0c119bd>] IofCompleteRequest+0xdd/0x190 [ndiswrapper]
[4295020.681000]  [<d0c189fd>] wrap_urb_complete_worker+0x7d/0x170 [ndiswrapper]
[4295020.684000] ndiswrapper (wrap_alloc_urb:383): couldn't allocate dma buf
[4295020.684000] ndiswrapper (wrap_bulk_or_intr_trans:660): couldn't allocate urb

what's the problem? how can I make the wlan0 interface running stable?

Thanks.

---

### Post by kevindontenville on 2006-06-15
Hi, mpeng

I get the same thing, using an MA111 but as I am squeezing Ubuntu onto a low power 128MB laptop I thought it might be a low memory thing. Seems the driver is still sort of working as for me the DHCP IP remains pingable and the driver/hardware reports as present.

It is a pain, seems it will work fine as long as not much is happening, but use DAAP and a web browser or a VNC session etc together and it dies. I used the blacklist prism2_usb method to get the MA111 driver installed and working as it didnt work out of the box so to speak. Does any of this ring true for you?

Did you get any further?

Kevin

---

### Post by Carandol on 2006-06-15
Just a thought, but have you tried using the wifi card *without* ndiswrapper? A lot of the wifi drivers have been upgraded and work now where they didn't before.

---

### Post by aldegaz on 2006-06-15
try pasting here your lsmod, maybe the bcm43xx driver is conflicting with ndiswrapper

---

### Post by mpeng on 2006-06-15
This is the "lsmod" output: 

mpeng@ubuntu:~$ lsmod
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
sonypi                 23084  0
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
speedstep_ich           5260  0
speedstep_lib           4484  1 speedstep_ich
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 speedstep_ich,cpufreq_stats
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
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
ndiswrapper           170512  0
dm_mod                 58936  1
sg                     37920  0
sd_mod                 19984  0
ipv6                  265600  6
md_mod                 72532  0
af_packet              22920  2
sr_mod                 16932  0
sbp2                   24196  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
usb_storage            74176  0
scsi_mod              139496  5 sg,sd_mod,sr_mod,sbp2,usb_storage
usbhid                 38368  0
joydev                 10048  0
e100                   40580  0
mii                     5888  1 e100
pcmcia                 40508  0
tsdev                   8000  0
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                  2180  0
rtc                    13492  0
hw_random               5652  0
psmouse                36228  0
serio_raw               7300  0
intel_agp              22940  1
agpgart                34888  2 drm,intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               32008  0
ohci_hcd               21892  0
usbcore               129668  6 ndiswrapper,usb_storage,usbhid,ehci_hcd,ohci_hcd
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
mpeng@ubuntu:~$

Thanks.

---

### Post by Camino on 2006-06-15
Hi,
having exactly the same issue as you.

On heavy load the same dma erros appears. I´m using the dwl-122 wlan usb stick with ndiswrapper. prism2_usb included in dapper are blacklisted....

the only way to get it running again is a rmmod ndiswrapper, modprobe ndiswrapper (but after a certain time it fails again)

I can´t use the included drivers of dapper due of WPA encryption

Bye

---

### Post by runokiab on 2006-08-20
I have exactly the same problem with a D-Link DWL-122 (H/W ver.:A1 F/W Ver.:3.2.1). I also have to use ndiswrapper, because I need WPA support, which does not work with linux-wlan-ng. I tried [ftp://ftp.dlink.com/Wireless/dwl122/Driver/dwl122_driver_102.zip](ftp://ftp.dlink.com/Wireless/dwl122/Driver/dwl122_driver_102.zip) and [ftp://downloads.netgear.com/files/ma111_CD_v2.0.zip](ftp://downloads.netgear.com/files/ma111_CD_v2.0.zip) (only the XP driver worked for me) but the problem is the same with both drivers. 
/var/log/kern.log tells me:
```
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [__alloc_pages+494/736] __alloc_pages+0x1ee/0x2e0
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [__get_free_pages+30/64] __get_free_pages+0x1e/0x40
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [dma_alloc_coherent+189/304] dma_alloc_coherent+0xbd/0x130
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [pg0+276606056/1069368320] wrap_alloc_urb+0x108/0x260 [ndiswrapper]
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [pg0+276607615/1069368320] wrap_bulk_or_intr_trans+0xcf/0x1f0 [ndiswrapper]
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [pg0+276610694/1069368320] wrap_submit_irp+0xc6/0xf0 [ndiswrapper]
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [pg0+276612338/1069368320] pdoDispatchDeviceControl+0x62/0x90 [ndiswrapper]
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [pg0+276593172/1069368320] IofCallDriver+0x54/0x70 [ndiswrapper]
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [pg0+276525552/1069368320] KfAcquireSpinLock+0x0/0x50 [ndiswrapper]
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [pg0+276593413/1069368320] IofCompleteRequest+0xd5/0x1c0 [ndiswrapper]
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [pg0+276606929/1069368320] irp_complete_worker+0x51/0x170 [ndiswrapper]
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [tasklet_action+58/112] tasklet_action+0x3a/0x70
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [__do_softirq+79/176] __do_softirq+0x4f/0xb0
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [do_softirq+53/64] do_softirq+0x35/0x40
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [irq_exit+53/64] irq_exit+0x35/0x40
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [do_IRQ+31/48] do_IRQ+0x1f/0x30
Aug 21 03:44:52 localhost kernel: [17185797.928000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Aug 21 03:44:52 localhost kernel: [17185797.928000] Mem-info:
Aug 21 03:44:52 localhost kernel: [17185797.928000] DMA per-cpu:
Aug 21 03:44:52 localhost kernel: [17185797.928000] cpu 0 hot: low 0, high 0, batch 1 used:0
Aug 21 03:44:52 localhost kernel: [17185797.928000] cpu 0 cold: low 0, high 0, batch 1 used:0
Aug 21 03:44:52 localhost kernel: [17185797.928000] DMA32 per-cpu: empty
Aug 21 03:44:52 localhost kernel: [17185797.928000] Normal per-cpu:
Aug 21 03:44:52 localhost kernel: [17185797.928000] cpu 0 hot: low 0, high 90, batch 15 used:16
Aug 21 03:44:52 localhost kernel: [17185797.928000] cpu 0 cold: low 0, high 30, batch 7 used:21
Aug 21 03:44:52 localhost kernel: [17185797.928000] HighMem per-cpu: empty
Aug 21 03:44:52 localhost kernel: [17185797.928000] Free pages:        1944kB (0kB HighMem)
Aug 21 03:44:52 localhost kernel: [17185797.928000] Active:49819 inactive:5782 dirty:2713 writeback:0 unstable:0 free:486 slab:3999 mapped:43620 pagetables:464
Aug 21 03:44:52 localhost kernel: [17185797.928000] DMA free:1016kB min:124kB low:60kB high:124kB active:11256kB inactive:0kB present:16384kB pages_scanned:0 all_unreclaimable? no
Aug 21 03:44:52 localhost kernel: [17185797.928000] lowmem_reserve[]: 0 0 239 239
Aug 21 03:44:52 localhost kernel: [17185797.928000] DMA32 free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Aug 21 03:44:52 localhost kernel: [17185797.928000] lowmem_reserve[]: 0 0 239 239
Aug 21 03:44:52 localhost kernel: [17185797.928000] Normal free:928kB min:1916kB low:956kB high:1916kB active:188020kB inactive:23128kB present:245696kB pages_scanned:0 all_unreclaimable? no
Aug 21 03:44:52 localhost kernel: [17185797.928000] lowmem_reserve[]: 0 0 0 0
Aug 21 03:44:52 localhost kernel: [17185797.928000] HighMem free:0kB min:128kB low:32kB high:64kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Aug 21 03:44:52 localhost kernel: [17185797.928000] lowmem_reserve[]: 0 0 0 0
Aug 21 03:44:52 localhost kernel: [17185797.928000] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 1*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1016kB
Aug 21 03:44:52 localhost kernel: [17185797.928000] DMA32: empty
Aug 21 03:44:52 localhost kernel: [17185797.928000] Normal: 0*4kB 0*8kB 2*16kB 0*32kB 2*64kB 0*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 928kB
Aug 21 03:44:52 localhost kernel: [17185797.928000] HighMem: empty
Aug 21 03:44:52 localhost kernel: [17185797.928000] Swap cache: add 86771, delete 78719, find 20481/27869, race 0+0
Aug 21 03:44:52 localhost kernel: [17185797.928000] Free swap  = 412092kB
Aug 21 03:44:52 localhost kernel: [17185797.928000] Total swap = 522104kB
Aug 21 03:44:52 localhost kernel: [17185797.928000] Free swap:       412092kB
Aug 21 03:44:52 localhost kernel: [17185797.928000] 65520 pages of RAM
Aug 21 03:44:52 localhost kernel: [17185797.928000] 0 pages of HIGHMEM
Aug 21 03:44:52 localhost kernel: [17185797.928000] 1608 reserved pages
Aug 21 03:44:52 localhost kernel: [17185797.928000] 50006 pages shared
Aug 21 03:44:52 localhost kernel: [17185797.928000] 8052 pages swap cached
Aug 21 03:44:52 localhost kernel: [17185797.928000] 2713 pages dirty
Aug 21 03:44:52 localhost kernel: [17185797.928000] 0 pages writeback
Aug 21 03:44:52 localhost kernel: [17185797.928000] 43620 pages mapped
Aug 21 03:44:52 localhost kernel: [17185797.928000] 3999 pages slab
Aug 21 03:44:52 localhost kernel: [17185797.928000] 464 pages pagetables
Aug 21 03:44:52 localhost kernel: [17185797.928000] ndiswrapper (wrap_alloc_urb:351): couldn't allocate dma buf
Aug 21 03:44:52 localhost kernel: [17185797.928000] ndiswrapper (wrap_bulk_or_intr_trans:621): couldn't allocate urb
```
I blacklisted prism2_usb and bcm43xx though bcm43xx were only used by another device and not by the wlan usb stick. 

Any help would be very much appreciated.
Best regards
runokiab

---

