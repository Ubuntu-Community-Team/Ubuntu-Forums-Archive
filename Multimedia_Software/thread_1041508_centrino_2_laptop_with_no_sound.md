---
title: "centrino 2 laptop with no sound"
date: 2009-01-16
forum: Multimedia Software
---

### Post by rootk1t on 2009-01-16
Hi,

I've got a centrino 2 based laptop and **_no_ sound on speakers _or_ headphones**!

I've tried to see if is something muted, but it's **not**. When I start to play a mp3 file, **it acts like it's playing** it but can **hear nothing**. 

What should I do?

**Characteristics**:

13.3" (WXGA,ColorShine) 

Intel Montevina Core2 Duo P8400

ATI Mobility Radeon HD3470 256MB VRAM 

4G DDRII667 RAM 

320G SATA HDD

DVD/RW SuperMulti Dual Layer 

802.11a/g/n Intel WLAN - 

1.3M Pixel Webcam - BlueTooth - Fingerprint - TPM - 6 Cell 

Link: [http://www.asus.com/products.aspx?l1=5&l2=23&l3=519&l4=38&model=2422&modelmenu=1](http://www.asus.com/products.aspx?l1=5&l2=23&l3=519&l4=38&model=2422&modelmenu=1)

Complete product name: Asus F6V-3P195

Here are some important outputs:

kernel: **2.6.27-9 **

**Ubuntu 8.10**

[B]
 aplay -l
[/B]

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**lshw:**

 *-multimedia
                description: Audio device
                product: RV620 Audio device [Radeon HD 34xx Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel



**[B]lspci:**[/B]



root@thc:/home/john# lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)



**lsmod:**


Module                  Size  Used by
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
af_packet              25728  4 
xt_multiport           11392  1 
binfmt_misc            16904  1 
rfcomm                 44432  2 
bridge                 56980  0 
stp                    10628  1 bridge

bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  16 rfcomm,bnep
ppdev                  15620  0 
ipv6                  263972  12 
acpi_cpufreq           15500  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  2 
cpufreq_conservative    14600  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container              11520  0 
wmi                    14504  0 
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
iptable_filter         10752  1 
ip_tables              19600  1 iptable_filter
x_tables               22916  2 xt_multiport,ip_tables
ext2                   72584  1 
mbcache                16004  1 ext2
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
arc4                    9984  2 
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
ecb                    10880  2 
snd_seq_dummy          10884  0 
psmouse                45200  0 
pcspkr                 10624  0 
crypto_blkcipher       25476  1 ecb
snd_seq_oss            38528  0 
joydev                 18368  0 
serio_raw              13444  0 
evdev                  17696  13 
iwlagn                 99588  0 
snd_seq_midi           14336  0 
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
iwlcore                92740  1 iwlagn
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
rfkill                 17176  2 iwlcore
mac80211              216820  2 iwlagn,iwlcore
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               32392  3 iwlagn,iwlcore,mac80211
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
btusb                  19736  3 
bluetooth              61924  11 rfcomm,bnep,sco,l2cap,btusb
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
video                  25104  0 
output                 11008  1 video
fglrx                1813960  28 
battery                18436  0 
ac                     12292  0 
asus_laptop            24440  0 
led_class              12164  2 iwlcore,asus_laptop
shpchp                 37908  0 
button                 14224  0 
intel_agp              33724  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  2 fglrx,intel_agp
usbhid                 35840  0 
hid                    50560  1 usbhid
reiserfs              238848  2 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  3 
ata_generic            12932  0 
pata_acpi              12160  0 
r8169                  35972  0 
libata                177312  3 ata_piix,ata_generic,pata_acpi
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 uvcvideo,btusb,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

---

### Post by rootk1t on 2009-01-17
Anyone?

---

### Post by rootk1t on 2009-01-17
Any suggestions?

---

### Post by rootk1t on 2009-01-18
Hello?

---

### Post by rootk1t on 2009-01-18
dump?

---

### Post by rootk1t on 2009-01-19
suggestions please?

---

### Post by xc3RnbFO8P on 2009-01-19
Show the output of **gedit /etc/modprobe.d/alsa-base**

---

### Post by rootk1t on 2009-01-19
> **Ringi said:**
> Show the output of **gedit /etc/modprobe.d/alsa-base**

cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
[B]#added by me but not working:
#options snd-hda-intel model=mobile[/B]

---

### Post by xc3RnbFO8P on 2009-01-19
Try this: **options snd-hda-intel model=3stack-dig**

---

### Post by rootk1t on 2009-01-19
> **Ringi said:**
> Try this: **options snd-hda-intel model=3stack-dig**

No result, I hear nothing :(

---

### Post by rootk1t on 2009-01-20
Any other suggestions please?

---

### Post by rootk1t on 2009-01-21
hello?

---

### Post by rootk1t on 2009-01-22
so what can I do?

---

