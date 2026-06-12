---
title: "cx88_alsa!! (Hauppauge HVR 4000)"
date: 2008-10-12
forum: Multimedia Software
---

### Post by Til_Valhall_vi_drar! on 2008-10-12
i have hauppauge HVR 4000 which have 6 plugs, S-video, normal cable tv, some other which i think is satelite, radio, IR (remote control), and audio in. so the audio is going to the motherboard via PCI. i have ubuntu 2.6.24-19-server and i have installed the v4l thing. im still a noob in linux after a short year with it, so i might ask stupid questions. my problem is that i get no sound. i have used this card at a windows box before and that of course worked fine. (but the software was really lame.) this is the third month i've trying to get this card to work under my linux box, and i only have the soundproblem left. i have reinstalled ubuntu but that didn't help. i am very sure it is the cx88_alsa module that is the audio driver. i have followed this guide: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000) so far. (and googled it and tried over hundreds of sites). after a fresh install i found the cx88_alsa already was modprobed when i executed lsmod | grep "cx". but after i installed v4l ([http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)) it was gone. when i tried to modprobe it, i got:

"FATAL: Error inserting cx88_alsa (/lib/modules/2.6.24-19-server/ubuntu/media/cx88/cx88-alsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)"

and the dmesg:

[ 1039.824354] cx88_alsa: disagrees about version of symbol videobuf_dma_free
[ 1039.824364] cx88_alsa: Unknown symbol videobuf_dma_free
[ 1039.824415] cx88_alsa: disagrees about version of symbol cx88_core_put
[ 1039.824417] cx88_alsa: Unknown symbol cx88_core_put
[ 1039.824504] cx88_alsa: Unknown symbol videobuf_pci_alloc
[ 1039.824539] cx88_alsa: disagrees about version of symbol cx88_core_irq
[ 1039.824541] cx88_alsa: Unknown symbol cx88_core_irq
[ 1039.824586] cx88_alsa: disagrees about version of symbol cx88_core_get
[ 1039.824588] cx88_alsa: Unknown symbol cx88_core_get
[ 1039.824779] cx88_alsa: disagrees about version of symbol btcx_riscmem_free
[ 1039.824781] cx88_alsa: Unknown symbol btcx_riscmem_free
[ 1039.824892] cx88_alsa: disagrees about version of symbol videobuf_dma_init
[ 1039.824894] cx88_alsa: Unknown symbol videobuf_dma_init
[ 1039.824972] cx88_alsa: disagrees about version of symbol cx88_sram_channel_dump
[ 1039.824974] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[ 1039.825020] cx88_alsa: disagrees about version of symbol cx88_sram_channel_setup
[ 1039.825022] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[ 1039.825061] cx88_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[ 1039.825064] cx88_alsa: Unknown symbol videobuf_dma_init_kernel
[ 1039.825125] cx88_alsa: Unknown symbol videobuf_pci_dma_unmap
[ 1039.825205] cx88_alsa: Unknown symbol videobuf_pci_dma_map
[ 1039.825250] cx88_alsa: disagrees about version of symbol cx88_risc_databuffer
[ 1039.825252] cx88_alsa: Unknown symbol cx88_risc_databuffer
[ 1039.825288] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[ 1039.825290] cx88_alsa: Unknown symbol videobuf_to_dma
[ 1749.178725] cx88_alsa: disagrees about version of symbol videobuf_dma_free
[ 1749.178734] cx88_alsa: Unknown symbol videobuf_dma_free
[ 1749.178785] cx88_alsa: disagrees about version of symbol cx88_core_put
[ 1749.178787] cx88_alsa: Unknown symbol cx88_core_put
[ 1749.178874] cx88_alsa: Unknown symbol videobuf_pci_alloc
[ 1749.178909] cx88_alsa: disagrees about version of symbol cx88_core_irq
[ 1749.178911] cx88_alsa: Unknown symbol cx88_core_irq
[ 1749.178957] cx88_alsa: disagrees about version of symbol cx88_core_get
[ 1749.178959] cx88_alsa: Unknown symbol cx88_core_get
[ 1749.179149] cx88_alsa: disagrees about version of symbol btcx_riscmem_free
[ 1749.179151] cx88_alsa: Unknown symbol btcx_riscmem_free
[ 1749.179262] cx88_alsa: disagrees about version of symbol videobuf_dma_init
[ 1749.179264] cx88_alsa: Unknown symbol videobuf_dma_init
[ 1749.179342] cx88_alsa: disagrees about version of symbol cx88_sram_channel_dump
[ 1749.179344] cx88_alsa: Unknown symbol cx88_sram_channel_dump
[ 1749.179390] cx88_alsa: disagrees about version of symbol cx88_sram_channel_setup
[ 1749.179392] cx88_alsa: Unknown symbol cx88_sram_channel_setup
[ 1749.179432] cx88_alsa: disagrees about version of symbol videobuf_dma_init_kernel
[ 1749.179434] cx88_alsa: Unknown symbol videobuf_dma_init_kernel
[ 1749.179496] cx88_alsa: Unknown symbol videobuf_pci_dma_unmap
[ 1749.179575] cx88_alsa: Unknown symbol videobuf_pci_dma_map
[ 1749.179620] cx88_alsa: disagrees about version of symbol cx88_risc_databuffer
[ 1749.179622] cx88_alsa: Unknown symbol cx88_risc_databuffer
[ 1749.179658] cx88_alsa: disagrees about version of symbol videobuf_to_dma
[ 1749.179660] cx88_alsa: Unknown symbol videobuf_to_dma
root@mjolnir:~# "

my lsmod:

Module                  Size  Used by
binfmt_misc            12808  1 
ppdev                  10372  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
loop                   19076  0 
snd_via82xx            29720  0 
gameport               16008  1 snd_via82xx
ipv6                  272804  22 
snd_ac97_codec        100772  1 snd_via82xx
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42016  0 
snd_mixer_oss          17792  1 snd_pcm_oss
isl6421                 3200  1 
snd_pcm                78596  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
cx24116                15492  1 
snd_page_alloc         11528  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9728  1 snd_via82xx
cx88_dvb               21636  0 
cx88_vp3054_i2c         3968  1 cx88_dvb
videobuf_dvb            7812  1 cx88_dvb
dvb_core               86396  2 cx88_dvb,videobuf_dvb
tuner_simple           16528  1 
tuner_types            15104  1 tuner_simple
snd_seq_dummy           4868  0 
tda9887                11908  1 
tda8290                14596  0 
snd_seq_oss            35456  0 
snd_seq_midi            9248  0 
tuner                  28868  0 
snd_rawmidi            25632  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
cx8802                 19332  1 cx88_dvb
cx8800                 36572  0 
cx88xx                 75560  3 cx88_dvb,cx8802,cx8800
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ir_common              44676  1 cx88xx
i2c_algo_bit            7300  2 cx88_vp3054_i2c,cx88xx
videodev               36352  3 tuner,cx8800,cx88xx
v4l1_compat            15748  1 videodev
compat_ioctl32          2304  1 cx8800
v4l2_common            13952  2 tuner,cx8800
tveeprom               13444  1 cx88xx
button                  9232  0 
snd                    56868  12 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
amd64_agp              13444  1 
btcx_risc               5896  3 cx8802,cx8800,cx88xx
videobuf_dma_sg        15108  4 cx88_dvb,cx8802,cx8800,cx88xx
videobuf_core          19716  5 videobuf_dvb,cx8802,cx8800,cx88xx,videobuf_dma_sg
k8temp                  6656  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
i2c_viapro              9876  0 
i2c_core               24832  12 isl6421,cx24116,cx88_vp3054_i2c,tuner_simple,tda9887,tda8290,tuner,cx88xx,i2c_algo_bit,v4l2_common,tveeprom,i2c_viapro
parport_pc             36644  1 
parport                37704  3 ppdev,lp,parport_pc
agpgart                34760  1 amd64_agp
evdev                  12928  0 
soundcore               8800  1 snd
pcspkr                  4224  0 
ext3                  136584  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sd_mod                 30720  3 
sg                     36496  0 
sr_mod                 17828  0 
cdrom                  37280  1 sr_mod
sata_via               12548  2 
floppy                 59332  0 
via_rhine              26888  0 
ehci_hcd               38412  0 
pata_acpi               8320  0 
pata_via               13316  0 
uhci_hcd               27152  0 
ata_generic             8324  0 
mii                     6400  1 via_rhine
usbcore               146028  3 ehci_hcd,uhci_hcd
libata                159344  4 sata_via,pata_acpi,pata_via,ata_generic
scsi_mod              151180  4 sd_mod,sg,sr_mod,libata
thermal                16796  0 
processor              37000  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 

lspci:

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0a.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
00:0a.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0a.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)


can anyone help me, or just give me a hint. im totally lost. i (think i) have tried everything.

---

### Post by xCAFEBABE on 2010-03-06
You could solved?? Right now, I have the same issue...

Thanks

---

