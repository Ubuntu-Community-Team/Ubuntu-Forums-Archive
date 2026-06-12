---
title: "Integrated sound cards dissapeared"
date: 2006-02-24
forum: Multimedia &amp; Video
---

### Post by Owdy on 2006-02-24
```
osku@Koti:~$ lspci -v | grep audio
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
```

Those are my sound cards but sounds are suddenly dissapeared. When i look system -> settings -> sounds there are no drivers. How do i reinstall them?

---

### Post by Owdy on 2006-02-25
Im sorry to bumb this but i really need my sound :neutral:

---

### Post by Haegin on 2006-02-25
Whats the output of modprobe? That may give us a clue as to whether you have the drivers loaded. (Enter modprobe in a terminal and paste the  output (in a code block so it gets scrollbars if its massive) here so we can see what its loading. Also can you post the output of "lspci -v" without grep (but look for the audio bits and just copy them over) so we get more info. Finally which is the main soundcard and which is onboard?

Thanks

---

### Post by Owdy on 2006-02-26
Both cards are integrated. Motherboard is Asus a7n8x-e deluxe.
[quote=Human Prototype]Whats the output of modprobe? That may give us a clue as to whether you have the drivers loaded. (Enter modprobe in a terminal and paste the  output

Thanks[/quote]That wont give me anything because i dont know module name.

```
osku@Koti:~$ modprobe
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-o <modname>] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]

``` 
Heres something
```
osku@Koti:~$ cat /proc/asound/oss/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux Koti 2.6.12-10-k7 #1 Mon Feb 13 12:29:26 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
NVidia nForce2 with ALC650F at 0xe1080000, irq 21
MPU-401 UART at 0x330, irq 10

Audio devices:
0: NVidia nForce2 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
1: MPU-401 UART MIDI

Timers:
7: system timer

Mixers:
0: Realtek ALC650F
1: mixer10

``` 
```
osku@Koti:~$ cat /proc/asound/cards
0 [nForce2        ]: NFORCE - NVidia nForce2
                     NVidia nForce2 with ALC650F at 0xe1080000, irq 21
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10

``` ```
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
        Subsystem: Asustek Computer, Inc.: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 9
        Memory at e1000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: Asustek Computer, Inc.: Unknown device 8095
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at d000 [size=256]
        I/O ports at d400 [size=128]
        Memory at e1080000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

```

---

### Post by Haegin on 2006-02-26
Sorry, I meant lsmod not modprobe. Also which is the integrated soundcard and which do you want to use?

---

### Post by Owdy on 2006-02-26
[quote=Human Prototype] Also which is the integrated soundcard and which do you want to use?[/quote] It doesnt matter. They have been there both to choose, since now.

```
osku@Koti:~$ lsmod
Module                  Size  Used by
snd_opl3_lib           10688  0
snd_hwdep               8992  1 snd_opl3_lib
snd_cs4231_lib         25408  0
vmnet                  37796  5
vmmon                 112044  6
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
cpufreq_userspace       4380  0
cpufreq_stats           5316  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
ipt_TCPMSS              4224  1
ipt_limit               2304  8
ip_nat_irc              2624  0
ip_nat_ftp              3456  0
iptable_mangle          2816  0
ipt_LOG                 7040  8
ipt_MASQUERADE          3392  1
iptable_nat            23060  4 ip_nat_irc,ip_nat_ftp,ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5440  1
ip_conntrack_irc       71760  1 ip_nat_irc
ip_conntrack_ftp       72784  1 ip_nat_ftp
ipt_state               1856  8
ip_conntrack           43128  7 ip_nat_irc,ip_nat_ftp,ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2880  1
ip_tables              19648  10 ipt_TCPMSS,ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
ipv6                  252544  6
af_packet              22088  2
tsdev                   7872  0
analog                 11680  0
gameport               14920  1 analog
snd_mpu401              6408  0
snd_mpu401_uart         7360  1 snd_mpu401
snd_rawmidi            25056  1 snd_mpu401_uart
snd_seq_device          8524  2 snd_opl3_lib,snd_rawmidi
floppy                 59412  1
pcspkr                  3460  0
rtc                    12408  0
ohci1394               34804  0
shpchp                 97252  0
pci_hotplug            27636  1 shpchp
snd_intel8x0           33344  0
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  4 snd_cs4231_lib,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    55172  13 snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  3 snd_cs4231_lib,snd_intel8x0,snd_pcm
nvidia_agp              8412  1
dm_mod                 58044  1
eeprom                  7504  0
evdev                   9728  0
asb100                 23380  0
i2c_sensor              3456  2 eeprom,asb100
i2c_nforce2             6784  0
i2c_core               21328  5 i2c_acpi_ec,eeprom,asb100,i2c_sensor,i2c_nforce2nvidia               3711172  12
agpgart                34888  2 nvidia_agp,nvidia
sr_mod                 17252  0
sbp2                   23176  0
ieee1394              101752  2 ohci1394,sbp2
psmouse                30212  0
mousedev               11680  2
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
ext3                  137352  4
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  1 thermal
fan                     4548  0
sd_mod                 19216  6
usbhid                 35552  0
sata_sil                9604  10
skge                   36880  0
forcedeth              21568  0
ehci_hcd               34312  0
ohci_hcd               20740  0
usbcore               118396  4 usbhid,ehci_hcd,ohci_hcd
ide_cd                 41732  1
cdrom                  39904  2 sr_mod,ide_cd
ide_generic             1472  0
sata_nv                 9412  0
libata                 54020  2 sata_sil,sata_nv
scsi_mod              135944  4 sr_mod,sbp2,sd_mod,libata
amd74xx                14044  1
ide_core              139028  3 ide_cd,ide_generic,amd74xx
unix                   27248  633
vesafb                  8088  0
capability              4808  0
commoncap               6912  1 capability
vga16fb                12680  1
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  74
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon

```

---

### Post by Owdy on 2006-02-26
This is weird. I created new user. In his session sounds work just fine. Both cards appears under sound settings. It has to be some of my own setting, but what could it be.

---

### Post by mpvano on 2006-02-26
Check your group settings

---

### Post by Owdy on 2006-02-26
[quote=mpvano]Check your group settings[/quote] Bingo! Wierd, i got only admin rights, all other rights were unchecked. Thanks!

---

