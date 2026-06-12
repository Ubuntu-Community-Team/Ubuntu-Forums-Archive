---
title: "No wifi connectivity"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by macdonald on 2009-04-14
I have Ubuntu 8.10 on my compaq presario c700 laptop. The wireless adapter is working fine. But after resuming from suspend mode the metwork connection cannot be established. The icon on the top most panel shows the required wireless connection but is unable to connect.

Please help!!!!!!

---

### Post by jbrown96 on 2009-04-14
What type of wireless card do you have?
You can find it from the output of ```
lspci
```

You probably just need to manually specify that the driver needs to be unloaded before suspend. Could you post the output of ```
lsmod
``` and I can tell you how to unload the driver.

---

### Post by iponeverything on 2009-04-15
In the following file:

/etc/pm/config.d/modules


put:

SUSPEND_MODULES="module-name"

where "module-name" is the name of your wifi module.

See if this solves the problem for you.

---

### Post by macdonald on 2009-04-16
Output of lspci :
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Output of lsmod : 

Module                  Size  Used by
xt_limit               10372  8 
xt_tcpudp              11008  10 
ipt_LOG                13700  8 
ipt_MASQUERADE         10752  0 
xt_DSCP                11264  0 
ipt_REJECT             11136  1 
nf_conntrack_irc       13348  0 
nf_conntrack_ftp       15652  0 
xt_state               10112  6 
af_packet              25856  4 
i915                   38528  2 
drm                    86056  3 i915
ipv6                  264228  17 
binfmt_misc            16904  1 
rfcomm                 44304  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  2 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pci_slot               12680  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wlan_scan_sta          21504  1 
ath_rate_sample        21248  1 
ath_pci               218808  0 
wlan                  239856  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312288  3 ath_rate_sample,ath_pci
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         385072  2 
uvcvideo               63624  0 
snd_pcm_oss            46848  0 
compat_ioctl32          9344  1 uvcvideo
snd_mixer_oss          22784  1 snd_pcm_oss
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
serio_raw              13444  0 
snd_seq_midi           14336  0 
pcspkr                 10624  0 
evdev                  17696  12 
snd_rawmidi            29824  1 snd_seq_midi
iTCO_wdt               18596  0 
psmouse                45200  0 
video                  25488  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 38036  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
pci_hotplug            34976  1 shpchp
output                 11008  1 video
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m
idi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
wmi                    14504  0 
battery                18436  0 
button                 14224  0 
intel_agp              33980  1 
ac                     12292  0 
agpgart                42184  3 drm,intel_agp
iptable_nat            13448  0 
nf_nat                 25368  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21900  9 iptable_nat,nf_nat
nf_conntrack           72032  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle         10880  0 
iptable_filter         10752  1 
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22916  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133384  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usb_storage            83264  0 
libusual               29844  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_piix               24708  2 
8139cp                 27520  0 
ata_generic            12932  0 
libata                177824  3 pata_acpi,ata_piix,ata_generic
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
8139too                31616  0 
mii                    13440  2 8139cp,8139too
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149488  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42284  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60956  3 


I have just started using Ubuntu and do not know which module I should select. Please guide me.
I want to understand what does each folder in the root folder contains. Please tell me where I can find this stuff.

---

### Post by macdonald on 2009-04-16
Output of lspci :
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Output of lsmod : 

Module                  Size  Used by
xt_limit               10372  8 
xt_tcpudp              11008  10 
ipt_LOG                13700  8 
ipt_MASQUERADE         10752  0 
xt_DSCP                11264  0 
ipt_REJECT             11136  1 
nf_conntrack_irc       13348  0 
nf_conntrack_ftp       15652  0 
xt_state               10112  6 
af_packet              25856  4 
i915                   38528  2 
drm                    86056  3 i915
ipv6                  264228  17 
binfmt_misc            16904  1 
rfcomm                 44304  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  2 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pci_slot               12680  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wlan_scan_sta          21504  1 
ath_rate_sample        21248  1 
ath_pci               218808  0 
wlan                  239856  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312288  3 ath_rate_sample,ath_pci
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
snd_hda_intel         385072  2 
uvcvideo               63624  0 
snd_pcm_oss            46848  0 
compat_ioctl32          9344  1 uvcvideo
snd_mixer_oss          22784  1 snd_pcm_oss
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
serio_raw              13444  0 
snd_seq_midi           14336  0 
pcspkr                 10624  0 
evdev                  17696  12 
snd_rawmidi            29824  1 snd_seq_midi
iTCO_wdt               18596  0 
psmouse                45200  0 
video                  25488  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 38036  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
pci_hotplug            34976  1 shpchp
output                 11008  1 video
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m
idi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
wmi                    14504  0 
battery                18436  0 
button                 14224  0 
intel_agp              33980  1 
ac                     12292  0 
agpgart                42184  3 drm,intel_agp
iptable_nat            13448  0 
nf_nat                 25368  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21900  9 iptable_nat,nf_nat
nf_conntrack           72032  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle         10880  0 
iptable_filter         10752  1 
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22916  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133384  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
usb_storage            83264  0 
libusual               29844  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_piix               24708  2 
8139cp                 27520  0 
ata_generic            12932  0 
libata                177824  3 pata_acpi,ata_piix,ata_generic
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
8139too                31616  0 
mii                    13440  2 8139cp,8139too
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149488  6 uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42284  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60956  3 


I have just started using Ubuntu and do not know which module I should select. Please guide me.
I want to understand what does each folder in the root folder contains. Please tell me where I can find this stuff.

---

### Post by macdonald on 2009-04-18
jbrown96 and iponeverythig, please reply. I have posted what you demanded.

Thanks

---

### Post by ddrichardson on 2009-04-18
For me, turning off networking before suspend works. 
   ```
gksudo gedit /etc/default/acpi-support
```   Change the line that reads: 
   ```
STOP_SERVICES=&#8221;&#8221;
```   To 
  ```
 STOP_SERVICES=&#8220;networking&#8221;
```
This cause networking to be reloaded on resume.

---

### Post by macdonald on 2009-04-18
@ddrichardson
It didn't work. I changed the value as you had written but the problem still persists.
Should I manually disable the networking before suspending it?
Any more suggestions...........

---

### Post by ddrichardson on 2009-04-18
That chipset usually uses the ath_5k module but you seem to have a lot of other Atheros modules loaded, my guess is one of them is interfering but kernel and userspace isn't something I know a lot about.

You can open a terminal and use:
```
sudo rmmod modulename
sudo modprobe modulename
```For the modules beginning with "ath" then try to bring up the interface to see which one isn't reloading then add that to iponeverything's method above.

---

### Post by macdonald on 2009-04-22
@iponeverything
in the folder /etc/pm/config.d there is no file named 'modules'. but there is a file named '00sleep_module'. In that file I added the line
SUSPEND_MODULES = "ath_pci"

but its not working.

when i switched on the computer after suspend 'ath_pci' was not in use(indicated by rmmod command) other two i.e. ath_hal and ath_rate_sample were in use. so i chose ath_pci,

now what to do ?

---

