---
title: "TV tuner card MEDION 7134 not working"
date: 2009-02-10
forum: Multimedia Software
---

### Post by JGMS on 2009-02-10
I have a TV card "MEDION 7134" more specifically: a CTX921-V.1 TV/FM card from Creatix GmbH, that I cannot possibly get into work on my AMD64 Ubuntu 8.04 system (2.6.24-23).

I read and tried about all I could, but all I got is that only the 'Composite' entry of the card passes a video signal to TVTIME, but never a TV signal. Thoughout all trials "No Signal" appears on the screen. Tvtime-scanner run in the terminal neather finds one.


**Here is what "lspci -v" gives:**
02:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
	Subsystem: Creatix Polymedia GmbH Medion 7134
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at 64000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

**The following data comes from the command "dmesg":**
 Linux video capture interface: v2.00
[   34.956580] saa7130/34: v4l2 driver version 0.2.14 loaded
[   34.956645] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   34.956653] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   34.956661] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 17, latency: 0, mmio: 0x64000000
[   34.956668] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   34.956673] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,insmod option]
[   34.956682] saa7134[0]: board init: gpio is 0
[   35.091715] saa7134[0]: i2c eeprom 00: be 16 03 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   35.091724] saa7134[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 0c c0 08 00 00 00 00 00
[   35.091731] saa7134[0]: i2c eeprom 20: 00 00 00 e3 ff ff ff ff ff ff ff ff ff ff ff ff
[   35.091736] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.091742] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.091747] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.091753] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.091758] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.108860] saa7134[0]: i2c scan: found device @ 0xa0  [eeprom]
[   35.115683] saa7134[0]: i2c scan: found device @ 0xa2  [???]
[   35.139665] saa7134[0] Tuner type is 38
[   35.225997] saa7134[0]: registered device video0 [v4l2]
[   35.226018] saa7134[0]: registered device vbi0
[   35.226037] saa7134[0]: registered device radio0
[   35.396514] saa7134 ALSA driver for DMA sound loaded
[   35.396523] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/acore/init.c:174: cannot find the slot for index 1 (range 0-1), error: -16
[   35.479611] saa7134[0]/dvb: frontend initialization failed

**To complete data listing from the terminal, next are the modules being loaded through "lsmod":**

Module                  Size  Used by
af_packet              27272  4 
binfmt_misc            14860  1 
radeon                131360  2 
drm                   105896  3 radeon
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67620  4 rfcomm,l2cap
rfkill_input            6912  0 
ipv6                  311848  16 
ppdev                  11400  0 
powernow_k8            16608  0 
cpufreq_conservative    10632  0 
cpufreq_stats           8416  0 
cpufreq_ondemand       11152  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       6180  0 
cpufreq_powersave       3200  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
aes_x86_64             26920  2 
dm_crypt               16776  0 
dm_mod                 71160  1 dm_crypt
sbp2                   27272  0 
lp                     14916  0 
saa7134_dvb            19596  0 
videobuf_dvb            8708  1 saa7134_dvb
dvb_core               94380  1 videobuf_dvb
tda1004x               18820  1 saa7134_dvb
saa7134_alsa           17248  0 
tuner                  49056  0 
tea5767                 7812  1 tuner
tda8290                13828  1 tuner
tuner_simple           10632  1 tuner
mt20xx                 14600  1 tuner
tea5761                 6916  1 tuner
saa7134               152280  2 saa7134_dvb,saa7134_alsa
compat_ioctl32         11136  1 saa7134
videobuf_dma_sg        17028  4 saa7134_dvb,videobuf_dvb,saa7134_alsa,saa7134
videobuf_core          22020  3 videobuf_dvb,saa7134,videobuf_dma_sg
ir_kbd_i2c             12560  1 saa7134
ir_common              39812  2 saa7134,ir_kbd_i2c
videodev               30720  1 saa7134
v4l2_common            21888  4 tuner,saa7134,compat_ioctl32,videodev
v4l1_compat            15492  2 saa7134,videodev
pcmcia                 45976  0 
snd_via82xx            33448  3 
gameport               17936  1 snd_via82xx
wbsd                   20496  0 
snd_mpu401_uart        11264  1 snd_via82xx
mmc_core               59272  1 wbsd
wmi_acer               11076  0 
snd_seq_dummy           5764  0 
parport_pc             41128  1 
parport                44300  3 ppdev,lp,parport_pc
snd_seq_oss            38912  0 
serio_raw               9092  0 
snd_seq_midi           10688  0 
snd_via82xx_modem      18572  0 
snd_ac97_codec        123224  2 snd_via82xx,snd_via82xx_modem
psmouse                46236  0 
ac97_bus                3840  1 snd_ac97_codec
snd_rawmidi            29856  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
pcspkr                  4992  0 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
k8temp                  7680  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 15488  0 
snd_pcm                92168  5 saa7134_alsa,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
evdev                  14976  8 
snd_timer              27912  2 snd_seq,snd_pcm
snd_page_alloc         13200  3 snd_via82xx,snd_via82xx_modem,snd_pcm
snd                    70856  20 saa7134_alsa,snd_via82xx,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_via82xx_modem,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              10400  1 snd
arc4                    3456  2 
ecb                     5248  2 
blkcipher               9476  1 ecb
b43                   159280  0 
rfkill                 10144  3 rfkill_input,b43
via_ircc               29632  0 
mac80211              192532  1 b43
irda                  222956  1 via_ircc
container               6656  0 
crc_ccitt               3584  1 irda
video                  23444  0 
cfg80211               17680  1 mac80211
i2c_viapro             11672  0 
output                  5632  1 video
led_class               7176  1 b43
i2c_core               28544  11 saa7134_dvb,tda1004x,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,saa7134,ir_kbd_i2c,i2c_viapro
input_polldev           6928  1 b43
battery                16776  0 
ac                      8328  0 
button                 10912  0 
yenta_socket           30092  3 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            46116  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
usbhid                 35680  0 
hid                    44992  1 usbhid
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  3 
pata_acpi               9856  0 
ata_generic             9988  0 
floppy                 69096  0 
pata_via               15620  2 
libata                176560  3 pata_acpi,ata_generic,pata_via
ehci_hcd               41996  0 
uhci_hcd               29856  0 
scsi_mod              178488  5 sbp2,sg,sr_mod,sd_mod,libata
tg3                   124804  0 
usbcore               170288  4 usbhid,ehci_hcd,uhci_hcd

ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
ssb                    39428  1 b43
thermal                19744  0 
processor              40424  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

**Lastbut not least: here is the contents of /etc/modprobe.d/options:**

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Settings for TV card
options saa7134 card=12 tuner=38
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-alsa
options saa7134-alsa index=1
alias char-major-81 videodev
alias char-major-81-0 saa7134

==========================================================

**Please** can anyone advise whether the above data looks correct or not, and what to do in order to get it to work (if there is still hope). 
Many, many thanks ahead. 

JGMS

---

### Post by Infoteksec on 2009-08-23
Hi

Have you got anywhere with this card.

Mine came bundled with a medion notebook. At present I'm not interested in the TV feature but I plan to try MythVT next. Right now I'm trying to use its composite input to capture some video using zoneminder.

The TV capture frame size is aparently 720x578 but I don't know what parameters I should be supplying to use the capture facility.

Any pointers would be appreciated.

Peter

---

### Post by Kweker on 2009-09-11
Hello

I have the same card, except it's V2. Same thing here, don't get analogue tv to work. Using mythbuntu version 9.04. Card is autodetected as number 12 (detected through I²C). Forcing tuner on type 63 (looked in datasheet of chip on Creatix website =  FMD1216ME tuner chip)

When scanning for channels Mythtv backend says I found like 30 channels or something. 

But when trying to watch them in the frontend it's like the tuner can't change frequency at all. Sometimes if lucky the frequency of the tuner is on an existing tv channel, and then I have a nice clear image:confused:; still sound is another problem... :confused:

I googled around for this but haven't found a solution yet.

Hope somebody can help

Greetz

Kweker

---

### Post by Kweker on 2009-09-12
got it working a few times, without sound though, but still I think it's an improvement:D

it has something to do with the tda9887 module not being loaded always. I unload saa7134-dvb saa7134-alsa and then finally saa7134

I then modprobe tda9987

and then i modprobe saa7134

tvtime founds all the channels (analogues) mythtv works as well

I'm not sure I'm doing this the right way, I will look into it further, and will come back later if I get the sound working

---

### Post by ajay7174 on 2009-09-13
hi
your tv card use saa7134 module best thing is your card have eeprom. if you want more detail about your hardware u can install device manger by [COLOR=Red]add remove programme [/COLOR]or by [COLOR=Red]synaptic package manager[/COLOR].
 
second thing try using [COLOR=Red]xawtv[/COLOR] software its a good software with GUI 
more important  is that you mast known about your place broadcasting pattern etc [COLOR=Red]ntsc[/COLOR] or [COLOR=Red]pal[/COLOR] broadcasting and fallow  europium or astrelian norms.
according above you choose card no and tuner no in mobprobe option 
cite
i am from india we follow [COLOR=Red]eropie[/COLOR]n brobdcostin norm with [COLOR=Red]pal-bg[/COLOR] so i choose 

[COLOR=Red]#sudo modprobe saa7134 card=65 tuner=37  [/COLOR]
where tuner 37 for pal-bg 
u also check software setting acording to above norm 
++++++++++++++++++++++++++++++++++++++++++

for more detail u serch my post 

if u find more satisfing setting plese replying because i also not find accourate setting.
my card working but show in composite (xawtv).
in composite option tvtime not able to nevigate chenel's 

with hope
ajay

---

