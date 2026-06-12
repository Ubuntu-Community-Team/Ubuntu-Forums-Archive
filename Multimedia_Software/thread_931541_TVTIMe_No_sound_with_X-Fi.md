---
title: "TVTIMe No sound with X-Fi"
date: 2008-09-27
forum: Multimedia Software
---

### Post by brett.hamilton@bredband.n on 2008-09-27
Hi 

I have a problem running tvtime it shows picture but no sounds
unfortuneately im using OSS drivers to get the X-FI card working
The sound card works with vlc, mplayer, amorak etc so i beleive that part of the equation is probably ok
although there is an issue with rec dev (ossxmix) causing sound to stop maybe its related or....

2.6.24-19-generic

 lspci -v

03:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: ASUSTeK Computer Inc. Unknown device 4871
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at efffe000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:07.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Unknown device 0033
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at ac00 [size=32]
	Memory at efc00000 (64-bit, non-prefetchable) [size=2M]
	Memory at e8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

lsmod

oss_usb               140212  1 
oss_sbxfi              47936  1 
osscore               569284  4 oss_usb,oss_sbxfi
af_packet              27272  2 
ipv6                  311848  18 
ppdev                  11400  0 
powernow_k8            16608  1 
cpufreq_conservative    10632  0 
cpufreq_powersave       3200  0 
cpufreq_stats           8416  0 
cpufreq_ondemand       11152  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       6180  0 
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
loop                   21508  0 
tda827x                 9348  1 
saa7134_dvb            19596  0 
videobuf_dvb            8708  1 saa7134_dvb
dvb_core               94380  1 videobuf_dvb
tda1004x               18820  2 saa7134_dvb
serio_raw               9092  0 
tuner                  49056  0 
tea5767                 7812  1 tuner
tda8290                13828  1 tuner
tuner_simple           10632  1 tuner
mt20xx                 14600  1 tuner
tea5761                 6916  1 tuner
nvidia               8858052  34 
saa7134               152280  1 saa7134_dvb
compat_ioctl32         11136  1 saa7134
videobuf_dma_sg        17028  3 saa7134_dvb,videobuf_dvb,saa7134
videobuf_core          22020  3 videobuf_dvb,saa7134,videobuf_dma_sg
ir_kbd_i2c             12560  1 saa7134
ir_common              39812  2 saa7134,ir_kbd_i2c
ath_pci               107824  0 
videodev               30720  1 saa7134
v4l2_common            21888  4 tuner,saa7134,compat_ioctl32,videodev
i2c_nforce2             8704  0 
wlan                  227104  1 ath_pci
v4l1_compat            15492  2 saa7134,videodev
psmouse                46236  0 
ath_hal               219888  1 ath_pci
evdev                  14976  3 
button                 10912  0 
i2c_core               28544  13 tda827x,saa7134_dvb,tda1004x,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,nvidia,saa7134,ir_kbd_i2c,i2c_nforce2
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
pcspkr                  4992  0 
k8temp                  7680  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  5 
usbhid                 35296  0 
hid                    44992  1 usbhid
usb_storage            82496  1 
libusual               23520  1 usb_storage
ata_generic             9988  0 
sata_nv                31752  2 
pata_amd               16772  0 
pata_acpi               9856  0 
ohci1394               36532  0 
ehci_hcd               41996  0 
libata                176432  4 ata_generic,sata_nv,pata_amd,pata_acpi
forcedeth              55564  0 
ieee1394              106968  2 sbp2,ohci1394
scsi_mod              178488  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
ohci_hcd               27524  0 
usbcore               169904  7 oss_usb,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

this from demsg, maybe this is relevant or maybe not, im just a noob 

[   40.787542] snd: Unknown symbol unregister_sound_special
[   40.787617] snd: Unknown symbol register_sound_special_device
[   40.787827] snd: Unknown symbol sound_class
[   40.801545] snd_timer: Unknown symbol snd_info_register
[   40.801574] snd_timer: Unknown symbol snd_info_create_module_entry
[   40.801603] snd_timer: Unknown symbol snd_info_free_entry
[   40.801651] snd_timer: Unknown symbol snd_verbose_printk
[   40.801683] snd_timer: Unknown symbol snd_iprintf
[   40.801719] snd_timer: Unknown symbol snd_ecards_limit
[   40.801748] snd_timer: Unknown symbol snd_oss_info_register
[   40.801774] snd_timer: Unknown symbol snd_unregister_device
[   40.801804] snd_timer: Unknown symbol snd_device_new
[   40.801856] snd_timer: Unknown symbol snd_register_device_for_dev
[   40.816482] snd: Unknown symbol unregister_sound_special
[   40.816558] snd: Unknown symbol register_sound_special_device
[   40.816766] snd: Unknown symbol sound_class
[   40.817356] DVB: registering new adapter (saa7133[0])
[   40.817361] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   40.817309] snd_timer: Unknown symbol snd_info_register
[   40.817336] snd_timer: Unknown symbol snd_info_create_module_entry
[   40.817366] snd_timer: Unknown symbol snd_info_free_entry
[   40.817415] snd_timer: Unknown symbol snd_verbose_printk
[   40.817448] snd_timer: Unknown symbol snd_iprintf
[   40.817485] snd_timer: Unknown symbol snd_ecards_limit
[   40.817514] snd_timer: Unknown symbol snd_oss_info_register
[   40.817540] snd_timer: Unknown symbol snd_unregister_device
[   40.817570] snd_timer: Unknown symbol snd_device_new
[   40.817623] snd_timer: Unknown symbol snd_register_device_for_dev
[   40.830315] snd_pcm: Unknown symbol snd_info_register
[   40.830342] snd_pcm: Unknown symbol snd_info_create_module_entry
[   40.830368] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[   40.830414] snd_pcm: Unknown symbol snd_timer_notify
[   40.830446] snd_pcm: Unknown symbol snd_timer_interrupt
[   40.830472] snd_pcm: Unknown symbol snd_info_free_entry
[   40.830497] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[   40.830529] snd_pcm: Unknown symbol snd_info_get_str
[   40.830592] snd_pcm: Unknown symbol snd_verbose_printk
[   40.830647] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[   40.830673] snd_pcm: Unknown symbol snd_card_file_add
[   40.830704] snd_pcm: Unknown symbol snd_iprintf
[   40.830742] snd_pcm: Unknown symbol snd_major
[   40.830797] snd_pcm: Unknown symbol snd_unregister_device
[   40.830827] snd_pcm: Unknown symbol snd_timer_new
[   40.830853] snd_pcm: Unknown symbol snd_device_new
[   40.830902] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[   40.830941] snd_pcm: Unknown symbol snd_lookup_minor_data
[   40.830967] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[   40.831001] snd_pcm: Unknown symbol snd_info_create_card_entry
[   40.831027] snd_pcm: Unknown symbol snd_power_wait
[   40.831056] snd_pcm: Unknown symbol snd_device_free
[   40.831100] snd_pcm: Unknown symbol snd_card_file_remove
[   40.831126] snd_pcm: Unknown symbol snd_register_device_for_dev
[   40.831185] snd_pcm: Unknown symbol snd_device_register
[   40.831213] snd_pcm: Unknown symbol snd_info_get_line
[   40.843881] saa7134_alsa: Unknown symbol snd_ctl_add
[   40.843911] saa7134_alsa: Unknown symbol snd_pcm_new
[   40.843955] saa7134_alsa: Unknown symbol snd_card_register
[   40.844000] saa7134_alsa: Unknown symbol snd_card_free
[   40.844043] saa7134_alsa: Unknown symbol snd_pcm_stop
[   40.844071] saa7134_alsa: Unknown symbol snd_pcm_format_physical_width
[   40.844097] saa7134_alsa: Unknown symbol snd_ctl_new1
[   40.844203] saa7134_alsa: Unknown symbol snd_card_new
[   40.844231] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   40.844277] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   40.844325] saa7134_alsa: Unknown symbol snd_pcm_format_signed
[   40.844352] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   40.844408] saa7134_alsa: Unknown symbol snd_pcm_format_big_endian
[   40.844451] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[   40.844477] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[   40.844542] saa7134_alsa: Unknown symbol snd_pcm_format_width




I have tried using sox to point the O/P to oss with no success. maybe its still pointing to alsa for some reason but I really have no clue how to find that out and redirect it..

so how about it anyone up to the challenge of helping me out with this
thanks in advance

---

