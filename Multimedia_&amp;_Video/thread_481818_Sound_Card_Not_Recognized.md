---
title: "Sound Card Not Recognized"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by robperry on 2007-06-22
All,

I am new to Linux so forgive my ignorance. I installed Ubuntu Linux on a Gateway Solo 5150 333 MHZ 256MB RAM Laptop

I am impressed with the product, however I have encountered a glitch. While the system has an ESS es1879 sound chip it is not recognized by Linux. When i click of the Xed-out speaker icon I receive an error message "No volume control GStreamer plugins and/or devices found"

Is anyone able to provide me the steps to implement the sound card.  I have tried the process discussed at 

[http://ubuntuforums.org/archive/index.php/t-12525.html](http://ubuntuforums.org/archive/index.php/t-12525.html)

and received the following

root@fahrenheit451:~# cd /etc/modprobe.d/soundcard
root@fahrenheit451:/etc/modprobe.d/soundcard# gedit snd-es18xx
ALSA lib confmisc.c:670: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391: (snd_func_concat) error evaluating strings
.
.
.
LSA lib confmisc.c:1070: (snd_func_refer) error evaluating name

ALSA lib conf.c:3500: (_snd_config_evaluate) function snd_func_refer returned error: No such device

ALSA lib conf.c:3968: (snd_config_expand) Evaluate error: No such device

ALSA lib pcm.c:2145: (snd_pcm_open_noupdate) Unknown PCM default

root@fahrenheit451:/etc/modprobe.d/soundcard# modprobe snd-es18xx

FATAL: Error inserting snd_es18xx (/lib/modules/2.6.20-16-generic/kernel/sound/isa/snd-es18xx.ko): No such device

root@fahrenheit451:/etc/modprobe.d/soundcard# /etc/init.d/alsa-utils restart

 * Shutting down ALSA...            * warning: 'alsactl store' failed with error message 'alsactl: save_state:1253: No soundcards found...'...          [fail] 
 * Setting up ALSA...                                                    [ OK ] 

Thank you

---

### Post by robperry on 2007-06-23
[FONT="Courier New"][FONT="Fixedsys"]As an FYI

As a user, when I run 


lspnp

--------following is returned----------
00 PNP0c02 Motherboard resources
01 PNP0c01 System board
02 PNP0200 AT DMA controller
03 PNP0000 AT programmable interrupt controller
04 PNP0100 AT system timer
05 PNP0b00 AT real-time clock
06 PNP0303 IBM enhanced keyboard (101/102-key, PS/2 mouse support)
07 PNP0c04 Math coprocessor
08 PNP0800 AT-style speaker sound
09 PNP0a03 PCI bus
0a PNP0c02 Motherboard resources
0b PNP0c02 Motherboard resources
0c ESS0001 multimedia controller: audio
0d ESS0009 multimedia controller: audio
0e ESS1879 multimedia controller: audio
0f PNP0501 16550A-compatible COM port
10 PNP0f13 PS/2 port for PS/2-style mice
16 PNP0400 Standard LPT printer port
18 PNP0700 PC standard floppy disk controller
1a PNP0e03 Intel 82365-compatible CardBus controller
-----------------------------------
The above indicates that the system sees the ESS1879 sound chip. 

-----------------------------------

after "sudo -s"   I run

cd /proc

proc#:  lsmod

--------following is returned----------
Module                  Size  Used by
wlan_wep                7936  1 
ipv6                  268960  8 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
apm                    22752  2 
ppdev                  10116  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
af_packet              23816  4 
lp                     12452  0 
fuse                   46612  0 
wlan_scan_sta          14976  1 
ath_rate_sample        14080  1 
ath_pci                97312  0 
wlan                  204484  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
pcmcia                 39212  0 
analog                 12832  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
ns558                   5760  0 
gameport               16520  3 analog,ns558
pcspkr                  4224  0 
psmouse                38920  0 
serio_raw               7940  0 
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               9740  0 
i2c_core               22656  1 i2c_piix4
tsdev                   8768  0 
evdev                  11008  1 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
floppy                 59524  0 
uhci_hcd               25360  0 
usbcore               134280  2 uhci_hcd
piix                   10756  0 [permanent]
generic                 5124  0 [permanent]
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

Thanks in advance
-r

---

