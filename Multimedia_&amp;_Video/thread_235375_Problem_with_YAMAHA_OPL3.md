---
title: "Problem with YAMAHA OPL3"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by revenger98 on 2006-08-13
Hello guys !

I'm a newbee on UBUNTU, but really interested on it becasue my country goverment (PERU) dependences are moving to linux platform becasue free.
So I've installed UBUNTU Drapper but I have a problem with my sound card, executing 'lsmod' bring me that report, I see some sound modules were loaded, but no sound card is detect, any help please?
A former KNOPPIX detected YAMAHA OPL3SA2
Thanks
FER
-------------------------------------------------
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
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
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ipv6                  265728  6
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
af_packet              22920  2
rsrc_nonstatic         13440  0
pcmcia_core            42640  1 rsrc_nonstatic
tsdev                   8000  0
serio_raw               7300  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0
snd_opl3_lib           10624  0
snd_hwdep               9376  1 snd_opl3_lib
snd_cs4231_lib         26752  0
snd_mpu401_uart         7808  0
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
bt878                  10552  0
analog                 12320  0
snd_pcm                89864  2 snd_cs4231_lib,snd_pcm_oss
tuner                  42276  0
snd_timer              25220  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
msp3400                32304  0
bttv                  164304  1 bt878
video_buf              22148  1 bttv
i2c_algo_bit            9608  1 bttv
ns558                   5636  0
gameport               15496  3 analog,ns558
snd                    55268  10 snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_mpu40 1_uart,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 sound,snd
v4l2_common             6016  1 bttv
btcx_risc               5128  1 bttv
tveeprom               15248  1 bttv
videodev                9856  1 bttv
snd_page_alloc         10632  2 snd_cs4231_lib,snd_pcm
pcspkr                  2180  0
via_rhine              23940  0
floppy                 62148  0
mii                     5888  1 via_rhine
psmouse                36100  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
i2c_viapro              8980  0
via_agp                 9856  1
agpgart                34888  1 via_agp
i2c_core               21904  7 i2c_acpi_ec,tuner,msp3400,bttv,i2c_algo_bit,tvee prom,i2c_viapro
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  2 uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
via82cxxx               9988  0 [permanent]
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

---

### Post by az on 2006-08-13
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

sudo modprobe snd-opl3sa2

---

### Post by revenger98 on 2006-08-13
Hi Azz

I did it and got this reply

FATAL: Error inserting snd_opl3sa2 (/lib/modules/2.6.15-26-386/kernel/sound/isa/snd-opl3sa2.ko): No such device

any help?
FER

---

### Post by revenger98 on 2006-08-14
Hi !

I've been phisically checking my sound card, adn found this writing o it

YMF719
FCC ID : LWHA151A00
A151-A00 
QS1000   ROM 1MX8
7EA0A09599

Is it a Yamaha one as forme KNOPPIX reported it???
Is there any tools to diagnose it ?

Thanks
FER

---

### Post by revenger98 on 2006-09-01
Hi guys !! :) 
still having same problem ...
I was wondering about ....Is there any linux related software to let me check  my isapnp yamaha sound card configuration?
I guess there is some setup data I need to check 
thanks
FER

---

### Post by revenger98 on 2006-09-01
HI  :p 
I've just got these messages from dmesg:
.
.
[17179574.520000] isapnp: Scanning for PnP cards...
[17179574.620000] isapnp: Card 'OPL3-SAX Sound Board'
[17179574.620000] isapnp: 1 Plug & Play card detected total
.
.
[17179604.156000] snd-opl3sa2-pnpbios: probe of 01:01.00 failed with error -2
[17179604.156000] Yamaha OPL3-SA soundcard not found or device busy
.
.
[17183191.832000] ad1848: PnP reports 'OPL3-SAX Sound Board' at i/o 0x530, irq 5, dma 0, 1
[17183191.936000] opl3sa2: Unknown parameter `snd_port'
.
.

I see I have a problem
Any help ?
see you
FER

---

### Post by bikeboy on 2006-09-01
I had this problem way back on the 1st Ubuntu release when I was a complete noob. I got help and it worked, here is the thread.

[http://ubuntuforums.org/showthread.php?t=4111](http://ubuntuforums.org/showthread.php?t=4111)

ps. ignore my post, look at the reply it should get you going.

---

### Post by revenger98 on 2006-09-02
hey Bikeboy !!!

Thanks so much, I've followed those instruction and it runs partially ok now,  I mean I can use Rhythmbox 0.9.3.1 to listen internet radio, and it's toally ok! (deeply thanks to you).

But  I can't listen mp3 audio files on VLC media player 0.8.4 (wxWidgets interface)
it reports next messages on its MESSAGE window :
     oss error: cannot open audio device (/dev/dsp)
     main error: couldn't find a filter for the conversion
     main error: couldn't set an output pipeline

I've checked for that file and it does exists so I dont know why I dont have sound on that player
Any suggestion/help ?
bye
FER

---

### Post by bikeboy on 2006-09-04
This is only a guess because I don't use VLC (or the lappy with the Yamaha) but maybe there is an option within VLC to change the sound system it uses. If there is...try them out, esound, oss, alsa etc is what your're looking for. Still, it's only a guess.

---

### Post by jensenhearing on 2006-09-15
What a relief. Great post. Make sure it is saved. Now Ubuntu is finally music to my ears.

---

