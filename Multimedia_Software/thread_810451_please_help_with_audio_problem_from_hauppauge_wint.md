---
title: "please help with audio problem from hauppauge wintv go fm card"
date: 2008-05-28
forum: Multimedia Software
---

### Post by grooverider on 2008-05-28
hi there ppl :)
i got a analogue wintv go with fm card (i think). It has radio for sure, 1x composite-in, audio out, and an IR. I run ubuntu hardy 64bit system. tvtime xawtv etc work without a problem, only i can't adjust the volume from within the applications. I have atm the line out of my tv card connected to the line-in of my soundcard. That's how i get my audio from my tv card. In my old computer however, with the same tv card and ubuntu feisty i got it working to get the audio from the tvcard itself and not using the line-in of my soundcard, but i have no idea how i got that working, i only know it took me while. Can someone help me with that please? :) here is some info about my system:

uname -r
2.6.24-16-generic

lspci
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
03:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
03:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

lspci -v | grep a4 Brooktree
03:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
        Subsystem: Hauppauge computer works Inc. WinTV Series
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0001000 (32-bit, prefetchable) [size=4K]

03:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
        Subsystem: Hauppauge computer works Inc. WinTV Series
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d0000000 (32-bit, prefetchable) [size=4K]

lsmod
Module                  Size  Used by
nls_cp437               8320  10 
cifs                  251152  10 
binfmt_misc            14860  1 
ppdev                  11400  0 
acpi_cpufreq           10832  0 
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
cpufreq_ondemand       11152  2 
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
video                  23444  0 
output                  5632  1 video
bay                     8064  0 
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  1 bay
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
coretemp                9856  0 
lp                     14916  0 
ipv6                  311720  28 
bt878                  13672  0 
tuner                  49056  0 
tea5767                 7812  1 tuner
tda8290                13828  1 tuner
tuner_simple           10632  1 tuner
mt20xx                 14600  1 tuner
tea5761                 6916  1 tuner
tvaudio                28188  0 
snd_bt87x              19076  1 
bttv                  214772  1 bt878
snd_hda_intel         440408  5 
ir_common              39812  1 bttv
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
compat_ioctl32         11136  1 bttv
i2c_algo_bit            8452  1 bttv
psmouse                46236  0 
videobuf_dma_sg        17028  1 bttv
videobuf_core          22020  2 bttv,videobuf_dma_sg
btcx_risc               6792  1 bttv
dcdbas                 11312  0 
serio_raw               9092  0 
parport_pc             41128  1 
parport                44300  3 ppdev,lp,parport_pc
pcspkr                  4992  0 
snd_pcm                92168  3 snd_bt87x,snd_hda_intel,snd_pcm_oss
tveeprom               20624  1 bttv
videodev               30720  1 bttv
v4l2_common            21888  5 tuner,tvaudio,bttv,compat_ioctl32,videodev
v4l1_compat            15492  2 bttv,videodev
nvidia               8858052  34 
snd_page_alloc         13200  3 snd_bt87x,snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
evdev                  14976  4 
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
i2c_core               28544  11 tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,tvaudio,bttv,i2c_algo_bit,tveeprom,nvidia
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  24 snd_bt87x,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
e1000e                108196  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
heci                   65944  0 
button                 10912  0 
intel_agp              30624  0 
soundcore              10400  1 snd
ext3                  149264  2 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  4 
ata_generic             9988  0 
usbhid                 35168  0 
hid                    44992  1 usbhid
floppy                 69096  0 
ahci                   33028  3 
pata_acpi               9856  0 
ehci_hcd               41996  0 
uhci_hcd               29856  0 
libata                176304  3 ata_generic,ahci,pata_acpi
scsi_mod              178488  4 sg,sr_mod,sd_mod,libata
usbcore               169904  4 usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              41448  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  5 

dmesg | grep 'bttv'
[   29.748371] bttv: driver version 0.9.17 loaded
[   29.748373] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   30.148964] bttv: Bt8xx card found (0).
[   30.148988] bttv0: Bt878 (rev 2) at 0000:03:00.0, irq: 16, latency: 64, mmio: 0xd0001000
[   30.149157] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   30.149159] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   30.149186] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   30.151691] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   30.188929] bttv0: Hauppauge eeprom indicates model#38074
[   30.188930] bttv0: tuner type=5
[   30.188933] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   30.189620] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   30.190307] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   30.289601] bttv0: registered device video0
[   30.289612] bttv0: registered device vbi0
[   30.289623] bttv0: registered device radio0
[   30.289643] bttv0: PLL: 28636363 => 35468950 .. ok

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebdc000 irq 16
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xd0000000, irq 16

cat /proc/asound/pcm
00-01: AD198x Digital : AD198x Digital : playback 1
00-00: AD198x Analog : AD198x Analog : playback 1 : capture 2
01-01: Bt87x Analog : Bt87x Analog : capture 1
01-00: Bt87x Digital : Bt87x Digital : capture 1

amixer -c 1 controls
numid=3,iface=MIXER,name='Capture Source'
numid=2,iface=MIXER,name='Capture Boost'
numid=1,iface=MIXER,name='Capture Volume'

amixer -c 1 cget name='Capture Source'
numid=3,iface=MIXER,name='Capture Source'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'TV Tuner'
  ; Item #1 'FM'
  ; Item #2 'Mic/Line'
  : values=1

amixer -c 1 cget name='Capture Boost'
numid=2,iface=MIXER,name='Capture Boost'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off

amixer -c 1 cget name='Capture Volume'
numid=1,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw------,values=1,min=0,max=15,step=0
  : values=15


i think somehow the card is not recognized properly, at least the sound part, tried to find my card on [http://www.bttv-gallery.de/](http://www.bttv-gallery.de/) but they are so many that look so similar to mine... can anyone help me to get the sound directly from my tv card?
thx in advance

p.s. here r some links, that could be useful but not sure what to follow...
[http://www.linuxtv.org/v4lwiki/index.php/Btaudio_%28bt878%29](http://www.linuxtv.org/v4lwiki/index.php/Btaudio_%28bt878%29)
[http://debian.shorton.info/2008/04/01/btaudio-and-2624/](http://debian.shorton.info/2008/04/01/btaudio-and-2624/)
[http://ubuntuforums.org/showthread.php?t=142414&highlight=btaudio](http://ubuntuforums.org/showthread.php?t=142414&highlight=btaudio)
[http://tldp.org/HOWTO/BTTV/modprobe.html#SND](http://tldp.org/HOWTO/BTTV/modprobe.html#SND)
[http://tldp.org/HOWTO/BTTV/recording.html](http://tldp.org/HOWTO/BTTV/recording.html)
[http://www.wlug.org.nz/TvTunerCards](http://www.wlug.org.nz/TvTunerCards)

---

