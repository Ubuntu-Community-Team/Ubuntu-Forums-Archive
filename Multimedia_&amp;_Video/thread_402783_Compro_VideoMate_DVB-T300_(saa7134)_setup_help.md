---
title: "Compro VideoMate DVB-T300 (saa7134) setup help"
date: 2007-04-06
forum: Multimedia &amp; Video
---

### Post by angelman99 on 2007-04-06
From what I've read the DVB drivers should now be natively supported in the 2.6+ kernals, and a few of the faithful had said &#8220;you shouldn't need to do much to get it working&#8221; - ha :confused: .

I've installed the latest Kubuntu 6.10 (Edgy) done all the updates (added the universe/restricted and proprietary sources as well), 141 darn updates, then another 15 or so (268Mb so still WAY better than Windows).

Jumped in to Adept Manager and added: dvb-utils, Kvdr, libdvb-dev, vdr (allowing their respective dependencies).

# lspci -v

00:0d.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)
        Subsystem: Unknown device 1850:0000
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at be000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [40] Power Management version 1

# lsmod

root@mythtv:/# lsmod
Module                  Size  Used by
saa7134_dvb            15108  0
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sbs                    16804  0
sony_acpi               6412  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
hotkey                 11556  0
dev_acpi               12292  0
button                  7952  0
battery                11652  0
container               5632  0
ac                      6788  0
asus_acpi              17688  0
ipv6                  272288  8
af_packet              24584  0
mt352                   7940  1 saa7134_dvb
video_buf_dvb           7684  1 saa7134_dvb
dvb_core               83368  1 video_buf_dvb
nxt200x                15364  1 saa7134_dvb
dvb_pll                13700  2 saa7134_dvb,nxt200x
tda1004x               17668  1 saa7134_dvb
lp                     12964  0
snd_seq_dummy           4996  0
snd_seq_oss            36480  0
snd_seq_midi            9984  0
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tsdev                   9152  0
usbhid                 45152  0
psmouse                41352  0
saa7134_alsa           15392  1
serio_raw               8452  0
snd_via82xx            30360  1
snd_mpu401_uart        10240  1 snd_via82xx
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
floppy                 63044  0
pcspkr                  4352  0
evdev                  11392  1
analog                 12960  0
gameport               17160  2 snd_via82xx,analog
snd_via82xx_modem      16648  0
snd_ac97_codec         97696  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            3456  1 snd_ac97_codec
parport_pc             37796  1
parport                39496  2 lp,parport_pc
wlan_scan_sta          15744  1
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  5 saa7134_alsa,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
ath_pci               100000  0
ath_rate_sample        16512  1 ath_pci
i2c_viapro              9876  0
via_agp                11264  1
agpgart                34888  1 via_agp
snd_timer              25348  2 snd_seq,snd_pcm
saa7134               118496  2 saa7134_dvb,saa7134_alsa
video_buf              27652  4 saa7134_dvb,video_buf_dvb,saa7134_alsa,saa7134
compat_ioctl32          2432  1 saa7134
v4l2_common            17280  1 saa7134
v4l1_compat            15108  1 saa7134
ir_kbd_i2c              9872  1 saa7134
ir_common              28548  2 saa7134,ir_kbd_i2c
i2c_core               23424  8 saa7134_dvb,i2c_ec,mt352,nxt200x,tda1004x,i2c_viapro,saa7134,ir_kbd_i2c
videodev               10752  1 saa7134
wlan                  207708  4 wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               192976  3 ath_pci,ath_rate_sample
via_rhine              26116  0
mii                     6912  1 via_rhine
snd                    58372  17 snd_seq_oss,snd_seq,saa7134_alsa,snd_via82xx,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
ext3                  142856  1
jbd                    62228  1 ext3
ehci_hcd               34696  0
uhci_hcd               24968  0
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
ide_disk               18560  3
via82cxxx              10500  0 [permanent]
generic                 6276  0
sata_via               10500  0
libata                 74892  1 sata_via
scsi_mod              144648  1 libata
thermal                15624  0
processor              31560  1 thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

So saa7134 drivers appear to be loaded but not correctly detecting the card.

# sudo rmmod -f saa7134
# sudo rmmod -f saa7134_alsa
# sudo rmmod -f saa7134_dvb

# sudo modprobe saa7134 oss=1 card=70
# sudo modprobe saa7134_dvb
# sudo modprobe saa7134_alsa


# dmesg |grep saa

root@mythtv:/home/me# dmesg |grep saa
[17179589.944000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179589.944000] saa7134[0]: found at 0000:00:0d.0, rev: 1, irq: 193, latency: 32, mmio: 0xbe000000
[17179589.944000] saa7134[0]: subsystem: 1850:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179589.944000] saa7134[0]: board init: gpio is 843f00
[17179590.132000] saa7134[0]: i2c eeprom 00: 02 10 00 01 04 00 1c 00 40 03 00 10 04 00 82 10
[17179590.132000] saa7134[0]: i2c eeprom 10: 00 e7 02 00 01 00 10 26 52 41 c0 06 f8 ed cb 00
[17179590.132000] saa7134[0]: i2c eeprom 20: 00 40 01 02 03 41 00 01 00 5e 00 06 40 e7 32 00
[17179590.132000] saa7134[0]: i2c eeprom 30: 01 5f 20 77 ac 5e 00 88 53 71 32 8c c0 01 0f 50
[17179590.132000] saa7134[0]: i2c eeprom 40: 26 02 00 00 02 00 67 00 00 50 51 2b 02 24 66 2b
[17179590.132000] saa7134[0]: i2c eeprom 50: 00 24 67 50 70 e7 66 00 01 71 66 cc 03 50 26 0b
[17179590.132000] saa7134[0]: i2c eeprom 60: 00 24 66 71 57 96 bc 9b 7f 38 57 05 0f 73 58 a0
[17179590.132000] saa7134[0]: i2c eeprom 70: 57 38 57 7c 58 4e 9f 83 f2 ff 80 30 58 d5 b8 14
[17179590.132000] saa7134[0]: registered device video0 [v4l2]
[17179590.132000] saa7134[0]: registered device vbi0
[17179591.184000] saa7134 ALSA driver for DMA sound loaded
[17179591.184000] saa7134[0]/alsa: saa7134[0] at 0xbe000000 irq 193 registered as card -1

I've jumped in and edited the /etc/modules

lp
saa7134 oss=1 card=70
saa7134_dvb

Then restarted.
How the heck do I get it to correctly identify my card ? (my wife is only away for the weekend and then I'll have to abandon the project (again :( )).

PS &#8211; Sorry for this being so long, I figure more detail than less will help diagnosis.

Current Distro: Kubuntu 6.10 (Edgy), (Tried KnoppMythR5E50 too)
Hardware: AMD Athlon 1Ghz, 1Gb RAM, 80Gb HDD
ASUS A7V8X, onboard NIC, onboard sound, ATI Radeon 9600
Compro VideoMate DVB-T300 (hybrid tuner card digital and analogue based on Saa7134)
User Level: Noob (To the world of Linux), hoping to setup VDR or MythTV.

---

### Post by angelman99 on 2007-04-07
I'm downloading the torrent of ubuntu 7.04 (beta) and going to give it a go.
Wish me luck :) 

I still can't understand why it wouldn't recognise the card with the modprobe :confused: .
And from what I've read of other posts this card doesn't need the firmware loaded everytime or anything bizzare like that.

I can see that if I can't get it happening with 7.04 I'll just have to learn how to compile kernels hey :(

---

### Post by steefjeqv on 2007-04-07
Hi,

Have you tried using Kaffeine as DVB player ?

Kaffeine is almost plug&play when it comes to DVB.

My Terratec Cinergy 1400 was immediately recognized.

Greetings,
Steven

---

### Post by angelman99 on 2007-04-07
Yes I did and it warned me during its first startup that it couldn't detect a card so I would only be able to watch DVDs.
7.04 is installing now (on my media PC) its grabbing down 244 updates (305Mb) thank goodness for broadband :) 
Then I'm going to grab a Ghost image and then mess with it :)

---

### Post by angelman99 on 2007-04-07
Good news loaded ubuntu 7.04 beta (and the updates) and my card is now recognised in dmesg

[   32.471254] saa7134[0]: found at 0000:00:0d.0, rev: 1, irq: 20, latency: 32, mmio: 0xbe000000
[   32.471262] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,autodetected]
[   32.471273] saa7134[0]: board init: gpio is 840000
[   32.471388] input: saa7134 IR (Compro Videomate DV as /class/input/input2
[   32.605081] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   32.605094] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   32.605103] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[   32.605112] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.605121] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   32.605130] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   32.605139] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.605147] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.689031] tuner 0-0043: chip found @ 0x86 (saa7134[0])
[   32.689105] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   32.697011] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[   32.705019] tuner 0-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   32.713085] tuner 0-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   32.721072] tuner 0-0068: chip found @ 0xd0 (saa7134[0])
[   32.722542] saa7134[0]: registered device video0 [v4l2]
[   32.722589] saa7134[0]: registered device vbi0

Kaffeine is only still giving me the options to play DVDs and CDs :( 
Kaffeine Player 0.8.3

Fingers crossed I'm going to install kvdr now :)

---

### Post by Jose Catre-Vandis on 2007-04-07
have you tried a reboot with your new options?

Maybe saa7134 is already loaded and you can't load new options on top, you have to unload it first.

so do a
```
 sudo rmmod saa7134
```
before trying to load

Also you need to put the options like this

(details is for my card and tuner an Asus P7131 - yours will be different)

Code:

```
sudo gedit /etc/modules
```

and add

```
saa7134-dvb
```

to the list, save and close
then

```
sudo gedit /etc/modprobe.conf
```

and add

```

# sets tv card for both analogue and digital
options saa7134 card=78 tuner=54
```

reboot or reload the saa7134 and saa7134-dvb modules and you should be good to go, assuming you have your card and tuner options right!

---

### Post by angelman99 on 2007-04-07
ok
Had to use 
```
rmmod -f saa7134
```
to force it to remove it

Added saa7134-dvb to the /etc/modules

But I can't find /etc/modprobe.conf
Used Thunar as root still couldn't find it.
I have a /etc/modprobe.d folder and a /etc/modutils folder

I'm using ubuntu 7.04 beta

---

### Post by angelman99 on 2007-04-07
For the Australian Compro VideoMate DVB-T300
saa7134 card=70 tuner=67

---

### Post by angelman99 on 2007-04-07
I also found a file called
/usr/share/doc/module-init-tools/examples/generate-modprobe.conf.gz
It appears to be an executable, bit reluctant to run it :confused:

---

### Post by angelman99 on 2007-04-07
Apparently all the files in the modprobe.d folder form the modprobe options.
So I did the following

```
sudo nano /etc/modprobe.d/options
```

added the line

```
option saa7134 card=70 tuner=67
```

rebooted

Result

```
[   32.070623] saa7134[0]: found at 0000:00:0d.0, rev: 1, irq: 19, latency: 32, mmio: 0xbe000000
[   32.070631] saa7134[0]: subsystem: 1850:0000, board: Compro Videomate DVB-T300 [card=70,insmod option]
[   32.070643] saa7134[0]: board init: gpio is 840000
[   32.070758] input: saa7134 IR (Compro Videomate DV as /class/input/input3
[   32.169726] ath_pci: 0.9.4.5 (0.9.3)
[   32.216143] saa7134[0]: i2c eeprom 00: 02 10 00 01 04 00 1c 00 40 03 00 10 04 00 82 10
[   32.216156] saa7134[0]: i2c eeprom 10: 00 e7 02 00 01 00 10 26 52 41 c0 06 f8 ed cb 00
[   32.216165] saa7134[0]: i2c eeprom 20: 00 40 01 02 03 41 00 01 00 5e 00 06 40 e7 32 00
[   32.216174] saa7134[0]: i2c eeprom 30: 01 5f 20 77 ac 5e 00 88 53 71 32 8c c0 01 0f 50
[   32.216183] saa7134[0]: i2c eeprom 40: 26 02 00 00 02 00 67 00 00 50 51 2b 02 24 66 2b
[   32.216191] saa7134[0]: i2c eeprom 50: 00 24 67 50 70 e7 66 00 01 71 66 cc 03 50 26 0b
[   32.216200] saa7134[0]: i2c eeprom 60: 00 24 66 71 57 96 bc 9b 7f 38 57 05 0f 73 58 a0
[   32.216208] saa7134[0]: i2c eeprom 70: 57 38 57 7c 58 4e 9f 83 f2 ff 80 30 58 d5 b8 14
[   32.344051] tuner 1-0043: chip found @ 0x86 (saa7134[0])
[   32.344127] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   32.356023] tuner 1-0061: chip found @ 0xc2 (saa7134[0])
[   32.368026] tuner 1-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   32.380005] tuner 1-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   32.391992] tuner 1-0068: chip found @ 0xd0 (saa7134[0])
[   32.515661] usbcore: registered new interface driver hiddev
[   32.516022] saa7134[0]: registered device video0 [v4l2]
[   32.516094] saa7134[0]: registered device vbi0


```

Went in to Kaffeine and it asked me about my DVB card - yippee :) 
I just need to configure my channels now, which I should be able to work out.

PS For other newbies (noobs) out there stick with it, it is worth while, the PC I have setup runs faster, more efficiently, looks prettier and cost me nothing more than some of my time :) . Heck even my download speed from this box I get 50Kb/s compared to my Windows box which gets 40Kb/s (and my Windows XP box is more than double the spec in hardware).

---

### Post by iluciv on 2007-04-07
You little ripper :) 

I've been trying to get this working for ages thanks so much for posting this. 

I was trying to build the lastest v4l drivers 

Works wonderfully

---

### Post by angelman99 on 2007-04-08
Finally got some channels to appear for Rockhampton Queensland Australia.

But Kaffeine reports:

14:39:58: xine: couldn't find demux for >/home/me/.kaxtv.ts<
14:39:58: xine: found input plugin : file input plugin
14:39:58: video_decoder: no plugin available to handle 'XviD'
14:39:58: xine: found demuxer plugin: AVI/RIFF demux plugin
14:39:58: xine: found input plugin : file input plugin

Can someone please translate, have I missed installing some dependencies?

---

### Post by Jose Catre-Vandis on 2007-04-08
Well done Angelman

I believe you can just create the modprobe.conf file if it doesn't exist, but you seem to have found the way :-)

Have you fully installed all w32codecs and multimedia codecs using Automatix2?

Also, try running a scan for channels using the dvb-utils package, and then create a channels.conf file. Place this in in your /home/user/.mplayer directory then you can test channels with mplayer:

```
mplayer dvb://
```

---

### Post by angelman99 on 2007-04-08
```
/usr/bin# scan -c -v -o zap -t 1 -A 1
```

Just brings up the help screen for scan again (which isn't very helpful I might add)

---

### Post by angelman99 on 2007-04-08
Sorry I am a newbie but I can't find the Automatix or Automatix2 package you recommended do I have to manually "get" it?

---

### Post by angelman99 on 2007-04-08
Sorry don't answer that last question, for those of you following this thread to install Automatix instructions are at

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by angelman99 on 2007-04-08
Installed mplayer, gone into the preferences for it and there are no settings relating to TV????
I've also installed KMPlayer, in the configuration settings for it the video source is set to default of:
Driver: v4l
Device: /dev/video

If I try to change it to /dev/dvb/adapter0/dvr0
or
/dev/vbi
or
/dev/vbi0

It crashes out.

---

### Post by angelman99 on 2007-04-12
Wasted 5 days on this, reinstalled my Windows XP license, downloaded Media Portal (Freeware) had it up and running with my Compro Videomate DVB-T300 in 20 minutes (not including the Windows install and updates which was somewhere around the 2-3 hour mark - I have low speed ADSL).
I am still surprised that the Compro Videomate DVB-T300 can win over 26 awards and be so ignored and difficult to configure in ANY linux flavour. I know even here in Regional Australia that hundreds of these cards are being sold out here as it has all the features that most users are looking for in a budget priced card. And just quietly I am extremely happy with the quality of the picture on this card (both on a 17" CRT and on my NEC dataprojector).

I'll check back in with ubuntu in another six months. Awesome project keep up the brillant work, ubuntu is definitely my favourite linux distro.

---

### Post by angelman99 on 2007-04-22
Ok I have taken a chill pill and have downloaded Ubuntu 7.04, ready to try again.
So I now have a shiny fresh new install.
Done the following:
Checked for/and done updates, then:

```
sudo nano /etc/modules

added the next 3 lines

saa7134
saa7134_dvb
saa7134_alsa
```

and

```
sudo nano /etc/modprobe.d/options

added the following line

options saa7134 card=70 oss=1 tuner=67

```
I now get

```
[   36.372566] saa7130/34: v4l2 driver version 0.2.14 loaded
[   37.961166] saa7134[0]: found at 0000:00:0d.0, rev: 1, irq: 20, latency: 32, mmio: 0xbe800000
[   37.961174] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,insmod option]
[   37.961185] saa7134[0]: board init: gpio is 840c00
[   37.961578] input: saa7134 IR (Compro Videomate DV as /class/input/input4
[   38.108639] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   38.108650] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   38.108660] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[   38.108669] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.108678] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   38.108687] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   38.108697] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.108706] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.200565] tuner 1-0043: chip found @ 0x86 (saa7134[0])
[   38.212556] tuner 1-0061: chip found @ 0xc2 (saa7134[0])
[   38.248523] tuner 1-0068: chip found @ 0xd0 (saa7134[0])
[   38.250118] saa7134[0]: registered device video0 [v4l2]
[   38.250276] saa7134[0]: registered device vbi0
[   38.277976] saa7134 ALSA driver for DMA sound loaded
[   38.278024] saa7134[0]/alsa: saa7134[0] at 0xbe800000 irq 20 registered as card -2
[   38.672170] DVB: registering new adapter (saa7134[0]).
```

Added Gxine but it does not see or let me configure any DVB input.
Still need help :-(
I must be close ..... really close .......

---

### Post by steefjeqv on 2007-04-22
Hello angelman99,

I think you're getting there.

Do you have Kaffeine installed ?
It's very good in handling DVB devices.

Greetings,
Steven

---

### Post by angelman99 on 2007-04-22
That's a KDE application is it going to cause any troubles now that I am running Gnome (Ubuntu 7.04 Fiesty Fawn)?
Tried Kaffeine before under Kubuntu 7.04 beta and it didn't work on the last attempt. I can probably reload it and check, I've been taking Ghost image snapshots as I've been going long :-)

---

### Post by angelman99 on 2007-04-22
Doesn't Kaffeine use the underlying xine engine anyway?

---

### Post by steefjeqv on 2007-04-22
Angelman99,

Yes, it is a KDE application but I've been using it for 2 years in a Gnome environment.

It should be available through Synaptic.

It's the only mediaplayer which was plug'nplay for my 2 DVB cards.
I just plugged in my Typhoon DVB-S and my Terratec Cinergy DVB-T and they were immediately recognised. It even supported the autoscan function for my DVB-T card.

Just make sure you've installed libxine-extracodecs. Also available through synaptic.

I'm still using Edgy. But I will be upgrading soon.

Greetings,
Steven

---

### Post by angelman99 on 2007-04-22
We have a winner!!!!! :-)
Kaffeine worked this time under ubuntu 7.04 (gnome).
Kaffeine also asked for win32codecs and libdvdcss (no surprises there really).
I've only picked up 2 channels (10 and SBS), just have to remember where the channels.conf file lives and edit it.
Next ....dare I contemplate it in Regional Australia is the dreaded EPG. Here in Australia the TV stations seem to think they own the program guide???? Does that seem weird to anyone else? Don't they want us to watch TV???

I'm going to document up my experience and submit it.

---

### Post by steefjeqv on 2007-04-22
Hi angelman99,

Glad to hear your TV card is working.

The channels.conf can be found at :

your home folder/.kde/share/apps/kaffeine/dvb-t

Make sure to mark "show hidden files".

Greetings,
Steven

---

### Post by joshuag86 on 2007-04-25
FIXED!!

Wat I have found on this issue.

I am running Feisty i386, with a Compro T300.
Run sudo gedit /etc/modules and add the line: saa7134-dvb
Then install dvb-utils, libxine1, libxine1-plugins, kaffeine.
Shut Down your computer. This is Important as a simple restart does not seem to work.
Open kaffeine and select Digital TV (No 6 on my machine).
Do a channel scan and away you go.

Josh.

---

### Post by ajm2005 on 2007-07-18
to summarise this thread, it seems there are two issues.

1. The reference drivers are able to support this card, however they don't recognise the card (card is identified as generic/ unknown, card=0). E.g., try "grep card= /var/log/dmesg" 

```
~$grep card= /var/log/dmesg
[   13.888000] saa7134[0]: subsystem: 1850:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
```


The correct card number for this device is 70. You can force the saa7134 drivers to use card=70 by adding a file of any name to folder: /etc/modprobe.d/ containing a single line "options saa7134 card=70". Reboot after doing this, and try "grep card= /var/log/dmesg" - the card should now be correctly identified:

```
~$grep card= /var/log/dmesg
[   13.616000] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,insmod option]
```


2. The saa7134-dvb driver doesn't seem to be automatically loaded when a program like Kaffeine or mplayer needs to use it. You can either manually load the driver yourself before launching Kaffeine/ mplayer, i.e.,

```
sudo modprobe saa7134-dvb
```

or alternatively add the line "saa7134-dvb" to "/etc/modules" which will have the driver loaded when the computer boots.

---

### Post by ajm2005 on 2007-07-18
The Kaffeine application doesn't need a channels.conf file, it can scan for channels on it's own.

To make a channels.conf file for mplayer or xine, first install the dvb-utils software:

```
sudo apt-get install dvb-utils
```

Then scan for channels:

```
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Sydney > ~/channels.conf
```

(his will scan for channels in Sydney Australia - look in /usr/share/doc/dvb-utils/examples/scan/dvb-t for your own location)

The channels.conf file can then be placed in your ~/.mplayer and ~/.xine directories.

---

### Post by Mad_Max_1412 on 2007-07-26
Hi Guys,

I have a VideoMate DVB-T300 card on my Windows machine but I've been thinking of moving across to Ubuntu, but I guess i've been worried about how to do things in a Linux environment that I've been doing easily in Windows.  

Firstly I gather from this post that the card is easily recognised in Feisty Fawn.  I noticed on the Compro webpage under Support [http://www.comprousa.com/New/en/download/tseries.html](http://www.comprousa.com/New/en/download/tseries.html) that there is a driver for the T300 called "Mandriva Linux 2007 Spring".  Should I install this if I move my card to my Ubuntu box, and if so, is it difficult to do (I'm still learning).

My next question relates to the Compro application which under Windows is what is used to tune into the stations and schedule recordings.  I've seen mention of a program called Kaffeine - is this the equivalent?  I've gone to the Kaffeine website and it appears that it allows you to watch digital TV but I didn't see anything about scheduling recordings.  BTW, the Compro application has the ability to turn on the computer and also power down after recording - Does Kaffeine do this? If not, then it's no big deal - would be nice though.  Is Kaffeine the only choice or is it simply the best choice?

A related concern I have which I had was trimming up my recorded TV shows.  Under Windows I use VideoRedo Plus - [http://www.videoredo.com/](http://www.videoredo.com/) - and I have noticed in the forums that some people have had some success using this program under WINE with requests for a native linux version.  I'll probably give it a go - might take a while learning how to do it since I'm a newbie.  In the meantime, is there any native programs that are easy to use to trim up video files like this?

Thanks

---

### Post by steefjeqv on 2007-07-26
Hi,

Ubuntu Feisty will recognize this TV card, but you may need to follow the instructions made by joshuag86 earlier on in this thread.

Kaffeine will then recognize your DVB device. Just do a channel scan and you can watch TV and schedule your recordings and much more. I'm not sure if Kaffeine can power up and shut down your PC, it would be a nice feature though.
There are other programs like MythTv which are designed as a true multimedia application. Much harder to set up though.

As for trimming up recorded shows :

1. Avidemux : simple program which I use for cutting out commercials after recording.
2. Cinelerra : a professional program which is capable of a lot, and then some more. Haven't used it myself but it seems very good.

Greetings,
Steven

---

### Post by stowe39 on 2007-09-25
Hi Angelman99

What did Kaffeine recognise your dvb card as? Mine shows as a Philips frontend instead of a compro dvb-t300, and I'm unable to get it to find any channels with Kaffeine.

I'm running the new linuxmce, and using mythtv I can get the card to scan for and find analog channels but can't get it to find the digital ones. 

Do you have any tips or instructions for getting it to find the channels in regional queensland?

Cheers

Kym

---

### Post by steefjeqv on 2007-09-26
Hi,

Did you try the following command in terminal ?

sudo modprobe saa7134-dvb

Greetings,
Steven

---

### Post by angelman99 on 2007-09-27
Kaffeine sees it as a Philips TDA10046H DVB-T

MythTV also reports it as a Philips too.

:confused:

---

### Post by stowe39 on 2007-09-28
Hi

I have followed the advice from this thread, particularly from the post by joshuag86 (as he says he got it fixed).  I have also added the line "saa7134-dvb" to "/etc/modules" and tested that the card is recognised correctly using code: grep card= /var/log/dmesg

I'm glad yours shows up as a philips card too Angleman99 :) at least I know I'm on the right track.

When I try to scan for channels using Kaffeine the signal bars indicate its finding signal, but no channels are found.  I've tried entering the settings from [www.dba.org.au](www.dba.org.au) for my region in a channel.config, but still haven't had any success. 

I made sure the mythtv backend was stopped before scanning for channels.

Is there a way to scan for any channels that are available? 

Thanks

Cheers

Kym

---

### Post by steefjeqv on 2007-09-28
Hi ,

You can find some channels.conf for Australia here :
[http://www.linuxtv.org/wiki/index.php/Australia]("http://www.linuxtv.org/wiki/index.php/Australia")

You can also make your own channels.conf using dvb-utils , type this in terminal :

apt-get install dvb-utils

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/your region > ~/channels.conf

Replace your region by the correct file which you can find in  /usr/share/doc/dvb-utils/examples/scan/dvb-t.

Hope this helps.

Greetings,
Steven

---

### Post by OnTarget600 on 2007-09-29
HII stowe39,

Your card has a phillips decoder so its fine that its showing up as that. I  personally don't  use ubuntu so I cant be too specific,I just signed up to answer your question. Ensure you have set the card to card=70 (or 69 as mentioned earlier?) See earlier posts on how to do that in ubuntu. Also ensure the saa7134-dvb module is loaded. (lsmod | grep saa) 

In mythtv set your card to DVB capture card of words VERY similar it has been a while since i was in setup. it should show up as DVB:0 that is the correct card type for your card in mythtv. Digital will not work under any other selection. I hope you persist as Mythtv is a fantastic piece of software, there is no windows app that even comes close. The automatic commercial removal works quite  well. The TV stations are working  this our though so some shows like  cold case have problems but it not too much  of a concern. I hope this helps. It is unlikely I will be back but im sure you will get plenty more help here.

---

### Post by Tom55 on 2007-10-11
I have been following this tread with interest having first attempted to setup Ubuntu - MythTV with my Compro T300 card 12 months ago.  Being very new to Linux it was all "monkey read... monkey do!" and I eventually gave up settling on a WinXP Media Portal option.  I now have a spare pc and so I purchased a LeadTek 100T capture card, used Ubuntu 7.04 and MythTV.  Got it all working with very little trouble from the intructions in the PC User magazine.  I'm using Shepherd for the EPG in Australia and MythWeb for the scheduled recording.

Now I've gone back to the compro T300 with exactly the same setup.  I attempted everything wrtitten above and the T300 wasn't recognised.  I discovered last night that the card would be recognised BUT only if I moved it into another slot on the pc motherboard.

MythTV recognises the card as a Philips variant.  But it doesn't find any channels when I scan.  Tonight I will look at the channel configuration file on the 2nd pc (the LeadTek) and see if I can use the data on the Compro pc and get MythTv to recognise the channels in Adelaide

Tom

---

### Post by angelman99 on 2007-10-12
I would be extremely relieved if that was my problem, but unfortunately it isn't the Compro card is in a middle PCI slot, I do know that some motherboards treat PCI slot 1 differently in case it has has a video card in it (needs to come alive at stratup to display BIOS etc).
We've bought a Topfield PVR so the pressure to get this working in a hurry is gone.
I noticed ComproUSA have released a driver for Mandriva, I excitedly downloaded the distro and loaded it, I'm not one of these people that dumps on a products because I can, but of all the Linux distros I've seen (which is a lest 5) it's one of the crappiest, couldn't config my NIC, wouldn't even recognise my wireless card (both of which worked in the other 5 distros I tried). And no I didn't want to pay $65 a year to join their club so I could get access to standard drivers.

Could someone at Ubuntu have a chat to the people over at Compro, because I'm sure they sell an awful lot of tuner cards globally. The card I bought won 26 awards so I imagine there are alot of them out there in PCs that are not going to be going to Vista :-) Most of them would make ideal Linux Media Centre PCs :-)

---

### Post by steefjeqv on 2007-10-13
Hi,

This may help. At least it's worth a try.

I used to own a Terratec Cinergy 1200 which uses the same tuner (TDA10046H).
In order to lock channels I had to add firmware to my Edgy installation.

You can find this file on the driver cd-rom.
When your using this card with Windows, this file can also be found (somewhere) on your computer.

Just copy it and paste to : /lib/firmware

Also make sure your card (number 70) is recognized correctly, as mentioned in previous posts.

Greetings,
Steven

---

### Post by Tom55 on 2007-10-19
This is what happened when I attempted to use the Compro T300 on Ubuntu with MythTV

Initially the card wasn't recognised by Ubuntu and so I changed it into another PCI socket.  The card was then recognised.  MythTV recognised the card as a Philips TDA10046H DVB-T.  That doesn't appear to be an issue.  However when I attempted to scan for channels in MythTV I get nothing.

I then purchased a LeadTek DVB 1000T.  Installed it into the pc beside the Compro in the PCI slot that the Compro wouldn't work in.  Both Ubuntu and MythTV recognised the card without any issues and the LeadTek card successfully scanned and found my channels here in Adelaide SA.

My conclusion is that there is something about the Compro and MythTV which is beyond my limited Linux/Ubuntu/MythTV knowledge to resolve.

---

### Post by pommattski on 2007-11-13
I've had some luck with this card, thanks to you all in this thread and others.
I found that it wasn't too painful to get it working with TVTime for analogue, and Kaffeine for digital.

I did have a problem when trying to get to scan in MythTV... (Digital only; haven't bothered with analogue in myth) The way I did it in the end was to read the frequencies and other info in the channels.dvb file that kaffeine created: I then asked MythTV to scan those individual frequencies. 

Anyway... Has anyone had much luck getting the card's remote to work properly?
I've done some searching, but I don't really know where to start.

Cheers,
Matt.

---

### Post by angelman99 on 2007-12-14
Well I finally got it sorted out :-) yippee!

I bought a Dell GX270 from auction for a friend and I went about setting it up with Ubuntu (the hard drive was wiped and no OS supplied). So I installed a fresh copy of Ubuntu, did all the updates, and I thought to myself, I might just try that TV Tuner card.........

Well.... the card auto-detected, right card, right model, right tuner and all :-)
I fired up Kaffeine, not brave enough to just jump into MythTV, my goodness it worked (after adding the codec to demux the video (which are packaged, so not really an effort)).
I cautiously hit the scan button under channels and BINGO at least 4 digital channels appeared on the first pass.

So my conclusion from this is that Linux (and I've tried several flavours) doesn't like my ASUS mother (version/model) and/or my ATI video card and/or the combination of the two.

So I'm glad I never gave up :-) it wasn't anything wrong with the card. And as a bonus the GX270 is way quieter than the media box I was going to use anyways.

Now.... I'm off to install MythTV with my working Compro VideoMate DVB-T300 :-)
(I may even install a second card :-) )

---

### Post by Tom55 on 2007-12-26
[QUOTE=pommattski;3762112]
<snip>

Anyway... Has anyone had much luck getting the card's remote to work properly?
I've done some searching, but I don't really know where to start.

Are you using 7.10 (Gutsy) and have you tried installing the Mythbuntu control centre.  There is an option in it for installing the remote.

---

### Post by Tom55 on 2007-12-26
Angelman99

I hope you have better luck than me when it comes to MthTV.  My system has recognised the compro T300 and so does MythTV.  BUT is refuses to find any channels when I scan.  I've also tried manually inserting the frequencies through the Channel Editor option but that doesn't work either.  I still get Timeout messages.  Interestingly I watch the card whilst I attempt the scan and the LED on the card flickers as if it's attempting to find channels.   Back to more Googling I think! 

Tom55

---

### Post by sprucas on 2007-12-26
wow this is a topical thread
i have the same problem - recognises the T300 - then i try to scan in myth and it gets great signal but doesn't add any channels 
same thing in kaffeine - finds signals - kaffeine green icon in scan screen flashes with lock - but it doesn't add any channels

if i scan in myth with v4l which is analog - i get tv - but analog tv sux0r

am going to try the channels.conf and dvbutils to see if i can get lock

where can i get channels.conf for sydney??

i'm using mythbuntu atm

---

### Post by sprucas on 2007-12-26
> **Tom55 said:**
> Angelman99

 BUT is refuses to find any channels when I scan. 
Tom55

tom55, what options are you using for the card in /etc/modprobe.d/options???

---

### Post by sprucas on 2007-12-26
gotta love google - i have been trying to figure out all the options for loading saa7134 module

finally found this site - starts to make sense now

[http://gentoo-wiki.com/HARDWARE_saa7134#tuner]("http://gentoo-wiki.com/HARDWARE_saa7134#tuner")

---

### Post by Tom55 on 2007-12-26
> **sprucas said:**
> tom55, what options are you using for the card in /etc/modprobe.d/options???


I have added to 
/etc/modules

saa7134
saa7134-dvb
saa7134-alsa

and to
/etc/modprobe.d/options

options saa7134 card=70 oss=1 tuner=67

The card is recognised by MythTv also correctly shows in dmesg

---

### Post by Tom55 on 2007-12-26
<snip>

where can i get channels.conf for sydney??

This was posted in an earlier forum

You can also make your own channels.conf using dvb-utils , type this in terminal :

apt-get install dvb-utils

Then

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Sydney > ~/channels.conf


oops.... just found thise piece of information

Athlon chipsets can have issues with saa7134 tuner cards

[http://www.ethics-gradient.net/myth/mythdvb2.html](http://www.ethics-gradient.net/myth/mythdvb2.html)

Now this is interesting because the T300 showed signs of working when being trialled in my old Intel PIII 700.  It just didn't have the grunt to capture standard definition.  So my inability to find channels may be partially due to the motherboard.  More research required

---

### Post by sprucas on 2007-12-27
i made a channels.conf for sydney

7 Digital 1:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:513:514:1313
7 Digital 2:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:513:514:1314
7 Digital 3:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:513:514:1315
7 Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:513:514:1312
7 Guide:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:609:610:1318
7 HD Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:577:0:1316
ABC2:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:513:651:674
ABC DiG Jazz:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:700:679
ABC DiG Radio:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:690:678
ABC HDTV:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:516:0:672
ABC TV:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:675
NINE DIGITAL:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:519:720:1
NINE GUIDE:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:517:700:6
NINE HD:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:0:5
SBS DIGITAL 1:571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:769
SBS DIGITAL 2:571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:770
SBS EPG:571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:163:85:772
SBS HD:571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:768
SBS RADIO 1:571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:782
SBS RADIO 2:571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:783
TEN Digital 1:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1570
TEN Digital 2:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1571
TEN Digital 3:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1572
TEN Digital:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1569
TEN Guide:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:513:660:1575
TEN HD:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:0:1576

---

### Post by Tom55 on 2007-12-27
Do you now have a picture and what program are you using?

---

### Post by sprucas on 2007-12-28
nope - my channels conf was a bit wrong by the way

i'm thinking you hit nail on head with your link re: athlon chip

i have athlon xp 1800 and maybe this is the problem

---

### Post by sprucas on 2007-12-28
okay found some more interesting information re: saa7134 on GENTOO wiki

[http://gentoo-wiki.com/HARDWARE_saa7134#tuner]("http://gentoo-wiki.com/HARDWARE_saa7134#tuner")

check out the section about enabling the DVB-T components about 3/4 down

we need the firmware file

and potential fix the v4l modules if we are using a newer kernel - notice how this impacts the ability to scan

i haven' t got it working yet but here is what i have down so far

before you can rebuild the the v4l drivers if you have a newer kernel you need to download a couple of things

1. follow this post to install linux headers
[http://www.techspot.com/vb/topic92558.html]("http://www.techspot.com/vb/topic92558.html")

2. then do this to install more support files for driver creation
sudo apt-get install build-essential

3. now follow gentoo wiki to create new drivers
 wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
 tar xjf tip.tar.bz2
 cd $(tar tf tip.tar.bz2 | head -n1 | cut -d/ -f1)

 make
 make install

i tried scanning channels
but it still didn't work

so i am now downloading the firmware file as recommended by gentoo wiki

---

### Post by sprucas on 2007-12-28
downloaded the firmware for tda10045 which is the phillips tuner
loads the dvb tuner firmware properly

but i get this error in i2c
[   15.520000] tuner' 0-0043: chip found @ 0x86 (saa7134[0])
[   15.536000] tuner' 0-0061: chip found @ 0xc2 (saa7134[0])
[   15.544000] tuner-simple 0-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   15.560000] tuner' 0-0068: chip found @ 0xd0 (saa7134[0])
[   34.000000] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   34.008000] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   34.008000] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   34.008000] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   34.008000] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)
[   34.032000] tuner-simple 0-0061: i2c i/o error: rc == -5 (should be 4)

i do scan and receive 8 services - but they all look like ABC

try kaffeine but couldn't view anything
try mythtv tune but nothing picked up

---

### Post by Tom55 on 2007-12-29
This ia summary of my situation

I've been able to get the Compro T300 to work on my PIII 700 but the pc isn't powerful enough to smoothly run the graphics.

I've been able to get my Leadtek Winfast 1000 to work with the AMD XP 2800+ straight plug and play and no problems with MythTV

When I put the Compro T300 into the XP 2800+ and add some lines to the /etc/modprobe.d/options and /etc/modules files the system recognises my card (so does MythTV). (card=70 Tuner=67).  When I boot the pc the small yellow LED lights up on the card. when I search for channels it flashes.  I've used the channels.conf file from my other mythTv box which works without any errors on the other box.  I can't get TVTime or Kaffeine to find any channels.

So the channels.conf file is correct,  the pc recognises the card,  the pc works with the LeadTek card.  I think the problem is some form of incompatibility between the T300 and the XP 2800+ processor.

Oops some progress.... I now have the SBS channels.  This is what I did

Goto Input Connections
Select DVB:0 to edit it
Select Scan for Channels
Select Scan Type
Select option "import from channels.conf
In field below enter the path to the file and it's name (I had a copy of the channels.conf file from my other mythtv box)
Goto next field Channel Separator - change it to "None"
Goto Existing Channel Treatment - change it to "rename to Match"
Click "Next"

The scan took place but it only found the SBS channels

I also found this info on Google  [http://www.mythic-beasts.com/~mark/random/mythtv/older-channel-setup.html](http://www.mythic-beasts.com/~mark/random/mythtv/older-channel-setup.html)

I shall see if I can work out how to edit the mythfilldatabase and add/amend the channel info

---

### Post by barmax on 2007-12-31
Besides 

[http://gentoo-wiki.com/HARDWARE_saa7134#tuner]("http://gentoo-wiki.com/HARDWARE_saa7134#tuner")

there are additional cards listed at 

[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134")

plus some good info.

---

### Post by Tom55 on 2007-12-31
Humm.. yes I have already worked out the card=70 and the tuner=67.  Both ubuntu ans MythTv recognise this in their setup.

I've re-installed Ubuntu Gutsy (but not MythTV) and ubuntu seems to have recognised the Compro T300 as Card 70 and the tuner as 67 Philips TD1316 Hybrid Tuner

DMESG

[   41.847741] saa7130/34: v4l2 driver version 0.2.14 loaded
[   41.848241] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 20
[   41.848255] saa7134[0]: found at 0000:00:0d.0, rev: 1, irq: 20, latency: 32, mmio: 0xea004000
[   41.848265] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,autodetected]
[   41.848277] saa7134[0]: board init: gpio is 843f00
[   41.848413] input: saa7134 IR (Compro Videomate DV as /class/input/input2
[   41.981399] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   41.981415] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   41.981426] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[   41.981436] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.981447] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   41.981457] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   41.981467] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.981478] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   42.449348] tuner 1-0043: chip found @ 0x86 (saa7134[0])
[   42.449417] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   42.457337] tuner 1-0061: chip found @ 0xc2 (saa7134[0])
[   42.465343] tuner 1-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   42.473353] tuner 1-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   42.481337] tuner 1-0068: chip found @ 0xd0 (saa7134[0])
[   42.482938] saa7134[0]: registered device video0 [v4l2]
[   42.482987] saa7134[0]: registered device vbi0
[   42.626011] input: GenPS/2 Genius Mouse as /class/input/input3
[   42.850684] saa7134 ALSA driver for DMA sound loaded
[   42.850742] saa7134[0]/alsa: saa7134[0] at 0xea004000 irq 20 registered as card -2
[   42.921330] DVB: registering new adapter (saa7134[0]).
[   42.921347] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   42.969277] tda1004x: setting up plls for 48MHz sampling clock

Lsmod

saa7134               129100  2 saa7134_dvb,saa7134_alsa
irda                  202300  1 via_ircc
crc_ccitt               3072  1 irda
i2c_viapro             10004  0 
video_buf              26244  4 saa7134_dvb,video_buf_dvb,saa7134_alsa,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872  1 saa7134
ir_common              35460  2 saa7134,ir_kbd_i2c
soundcore               8800  1 snd
shpchp                 34580  0 
i2c_core               26112  7 saa7134_dvb,dvb_pll,tda1004x,tuner,saa7134,i2c_viapro,ir_kbd_i2c
videodev               29312  1 saa7134
v4l2_common            18432  3 tuner,saa7134,videodev
v4l1_compat            15364  2 saa7134,videodev

Create a channels.conf file using "scan" and "au-Adelaide"
However Kaffeine doesn't find any channels when I scan (although the documentation stated Kaffeine used it's own data.  Checked the Kaffeine data and it's the same as the data being used by scan.

There doesn't seem much point in installing MythTV until I can get the card to scan and receive a channel.

OK... I installed TVTime and did the scan from within the program.  It collected a number of channels, most of which have a grainy picture.  Interesting I didn't achieve any results with the scan until I changed it from PAL to SECAM. I suspect these channels are analogue.  However the T300 card will work with the AMD XP 2800+.   I think I'm getting close.

OK... reinstalled Ubuntu Gutsy and did all the updates.  Installed tvtime and was able to get channels.  This time using PAL rather than SECAM.  Pictures still look grainy and there is no sound which leads me to believe the signal is analogue.  The Compro T300 is capable of both analogue and digital.

Installed the dvb-utils and then did a scan.  See below.  This time the scan found the SBS channels but missed all the others (ABC, 7, 9, 10, 31).

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Adelaide
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 2 9 3 1 2 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 564500000 1 2 9 3 1 2 0
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
0x0000 0x0340: pmt_pid 0x0400 SBS -- SBS HD (running)
0x0000 0x0341: pmt_pid 0x0401 SBS -- SBS (running)
0x0000 0x0342: pmt_pid 0x0402 SBS -- SBS NEWS (running)
0x0000 0x0343: pmt_pid 0x0408 SBS -- SBS 2 (running)
0x0000 0x034e: pmt_pid 0x0403 SBS -- SBS RADIO 1 (running)
0x0000 0x034f: pmt_pid 0x0404 SBS -- SBS RADIO 2 (running)
Network Name 'SBS NETWORK'
>>> tune to: 571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (6 services)
Done.


  Getting closer

---

### Post by Tom55 on 2008-01-06
OK.  I can view all the SBS channels but nothing else

I've made a copy of my channels.conf file from my working MythTv box and inserted it into the AMD XP2800+ pc.  tzap will give me a lock on all channels but xine will still only show the SBS channels.  I must be missing something in the tuning process that creates the channels.conf file.  When I scan in this pc it only picks up the SBS channels.  More googling I think!

---

### Post by Tom55 on 2008-01-06
I now have three channels (SBS, ABC and TEN).  I decided to ignore the frequency information in the au-Adelaide file (it was only giving me SBS).  

I went to the dba.org.au website and noted that transmissions are broadcast from two different locations.  Mt Lofty and the city.  All the frequencies from the city are UHF and Mt Lofty only broadcasts SBS on UHF.  

So I altered the frequencies in the au-Adelaide file to those UHF frequencies and tzap recognised the additional two channels.  Now I need to understand if this is a problem with the card only being able to receive UHF frequencies.

Getting closer

---

### Post by Patto77 on 2008-01-09
This thread has been invaluable!  I have the Compro Videomate DVB-T 200a, but the instructions here are much the same.  I'm using GG 7.10.

I've currently given up on MythTV because I have had no success with scanning in the channels, but I have got every channel except for CH7 Brisbane working in Kaffeine.  So I'm definitely on the right track.:)

---

### Post by Tom55 on 2008-01-10
Do you get a channel frequency "lock" when using tzap?  If you can get the channels with Kaffeine then I suggest the problem is with your MythTV setup.  Don't give up on MythTv because it's darn good.

---

### Post by Nojatron on 2008-01-18
Has anyone got this working for Channel 7 and 9 (I'm in Sydney).

I'm running Gutsy 64-bit with a Leadtek dtv2000h and scan is picking up all channels apart from these 2. The odd thing is I had it working at one stage but I didn't really do anything to get it working (that I can think of) and it stopped running next time I rebooted.

Tzapping the 2 channels gets a lock every now and then but it's not consistent.

Output of running a scan:
```
scanning au-sydney_north_shore
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 2 9 3 1 2 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 571500000 1 2 9 3 1 2 0
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
0x0000 0x0220: pmt_pid 0x0102 ABC -- ABC HDTV (running)
0x0000 0x0221: pmt_pid 0x0100 ABC -- ABC TV Sydney (running)
0x0000 0x0222: pmt_pid 0x0101 ABC -- ABC2 (running)
0x0000 0x0223: pmt_pid 0x0103 ABC -- ABC TV (running)
0x0000 0x0226: pmt_pid 0x0104 ABC -- ABC DiG Radio (running)
0x0000 0x0227: pmt_pid 0x0105 ABC -- ABC DiG Jazz (running)
Network Name 'ABC Sydney'
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE (tuning failed)
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
0x0000 0x0300: pmt_pid 0x0400 SBS -- SBS HD (running)
0x0000 0x0301: pmt_pid 0x0401 SBS -- SBS (running)
0x0000 0x0302: pmt_pid 0x0402 SBS -- SBS NEWS (running)
0x0000 0x0304: pmt_pid 0x0408 SBS -- SBS 2 (running)
0x0000 0x030e: pmt_pid 0x0403 SBS -- SBS RADIO 1 (running)
0x0000 0x030f: pmt_pid 0x0404 SBS -- SBS RADIO 2 (running)
Network Name 'SBS NETWORK'
>>> tune to: 536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
0x0330 0x000a: pmt_pid 0x00b0 WIN Digital -- WIN TV HD (running)
0x0330 0x0001: pmt_pid 0x0020 WIN Digital -- WIN TV Illawarra (running)
Network Name 'WIN Digital'
>>> tune to: 564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 585500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
0x327b 0x000a: pmt_pid 0x00b0 WIN Digital -- WIN TV HD (running)
0x327b 0x0001: pmt_pid 0x0020 WIN Digital -- WIN TV Illawarra (running)
Network Name 'WIN Digital'
dumping lists (16 services)
```

---

### Post by Tom55 on 2008-01-19
I have a similar problem and have only been able to get three channels.  It's now been suggest by an ABC tech that I may have too many TV's and capture cards connected to the antenna.  He advised that every additional TV reduces the total signal strength by 50% for each connection.  That is:
1 TV 100% strength
2 TV's 50%
3 TV's 25% to each TV
etc

If he is correct this might explain my problem as I have 3 TV's and 3 capture cards on the one antenna.  I'm going to unplug some of the TV's and see if it makes any difference.

The trouble is it doesn't explain why the two LeadTek 100's still get a signal but the Compro doesn't?

---

### Post by Mad_Max_1412 on 2008-03-14
Guys,

I need help.  I have the VideoMate DVB-T300 card in Gutsy Ubuntu and have tried to follow this thread, but don't seem to be having much luck.  At the moment, Kaffeine goes through the motions of scanning, with the signal and SNR bars moving and the lock button turning on and off, but no channels appear.

In /etc/modules, I now have:

> fuse
lp
sbp2
saa7134 card=70 tuner=67
saa7134
saa7134-dvb
saa7134_alsa


My /etc/modprobe.d/options reads

> # Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
options psmouse resetafter=1
options saa7134 card=70 oss=1 tuner=67

Tom55 wrote:
> You can also make your own channels.conf using dvb-utils , type this in terminal :

apt-get install dvb-utils

Then

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Sydney > ~/channels.conf

I ran the command "apt-get install dvb-utils" and then ran the 2nd command slighty modified as scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-sydney_north_shore as this was the best choice (au-Sydney didn't exist).  Please note that I'm from Thornton which is between Newcastle and Maitland and the transmission towers are at Mount Sugerloaf.  Anyway, I get the following output:

> scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-sydney_north_shore
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 2 9 3 1 2 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 571500000 1 2 9 3 1 2 0
initial transponder 578500000 1 2 9 3 1 2 0
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 578500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 578500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (0 services)
Done.


what am I doing wrong?

Thanks

---

### Post by angelman99 on 2008-03-15
I'd love to help but I'm a complete newbie to this too. Hopefully someone useful will spot this thread and provide some meaningful assistance.
Do you get any channels using the pre-configured channels list in Kaffine?
If you can find the option to increase the "time out" for when it scans for the channels that seems to help (well it helped for me in MythTV).

---

### Post by Mad_Max_1412 on 2008-03-26
Guys,

Sorry to bump this, but haven't had any replies now for a while and was hoping someone could help me out.

I did try MythTV but got confused by SQL stuff etc.  

I'm just after a decent program which can scan for TV channels and then I can schedule recordings.

Thanks

---

### Post by steefjeqv on 2008-03-26
Hi,

As long as your not able to tune to your local channels, no program is going to work.

Did you add additional firmware ?
If so, you can try changing the rights to this file to 777.

You can also try to upgrade your dvb drivers :

[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

My preffered application is called VDR :

[http://www.cadsoft.de/vdr/]("http://www.cadsoft.de/vdr/")

[http://linuxtv.org/vdrwiki/index.php/Main_Page]("http://linuxtv.org/vdrwiki/index.php/Main_Page")

Greetings,
Steven

---

### Post by Mad_Max_1412 on 2008-03-26
Hi,

I now have 3 "versions" of channel 10, these being SC10 HD, SC 10 Newcastle and SC Ten.  I didn't make any changes but over the past few days I just kept hitting the "Scan Channels" button and one day these 3 turned up.  I assume it must have been a recently installed update that was "pushed" (ie via the update notification icon).

I haven't added any firmware - my computer experience isn't that great that I know what chipset I've got etc so I'm a bit hesitant about flashing any firmware when I know the card worked ok under WinXP.

You mentioned..

> If so, you can try changing the rights to this file to 777.

Unfortunately I don't know what you mean by changing the rights to 777

I will have a look at that page about dvb drivers, although not tonight as it's getting late.

I'm looking forward to moving totally from WinXP to Ubuntu, but I can see why people are hesitant about making the leap.  With WinXP, most times you install the device and run a file which will install drivers and a program to use the device, whereas with Ubuntu, you need to know how to do configuration editing (plus knowing where to go etc) and for the average Joe, it's sometimes frustrating.

I know that WinXP is different from Ubuntu, but just making a comment on how quickly one can get a new piece of equipement running under XP compared to Ubuntu.  But I'm trying to learn.

Cheers

---

### Post by steefjeqv on 2008-03-27
Hi,

First let's see if adding firmware to your Ubuntu setup helps you out.

I've attached the firmware which may be required.

Just untar it into your /lib/firmware/2.6.22-14-generic directory.
Check if your kernel directory is the same as the one I'm using. It should be, otherwise change the above path to whatever you're kernel version you're using.

Then type in terminal :

sudo chmod 777 /lib/firmware/2.6.22-14-generic/dvb-fe-tda10046.fw

Try scanning for channels.

Please let me know if this helps or not.
If it doesn't we'll try upgrading the dvb-drivers.

Greetings,
Steven

---

### Post by Mad_Max_1412 on 2008-03-28
Hi steefjeqv, thanks for your help. Unfortunately no luck.

Firstly, I downloaded the file to the desktop and right-clicking on it allowed me to extract it to the desktop but when I went to copy it to the directory it said I didn't have permissions on that folder to copy things there.  I had a quick search and found out about using the command gksudo nautilus to copy/move things around which worked.

BTW, I also have in that firmware directory a folder called 2.6.20.16-generic just in case this info is important.

Anyway, I did another scan and it still only found the same 3 variations of Channel 10.  It only scanned for about 3-4 seconds before the "stop scan" button reverted back to "start scan".

My "configure DVB" option under the DVB menu is as follows:

DVB Device name is Philips TDA10046H DVB-T
Type: Terrestrial
Tuner Timeout: 1600ms
Source: au-Newcastle

Broadcast option reads
Broadcast address: 192.168.0.255
Broadcast port:1234
Info Port: 1235

Misc option reads:
Default charset ISO8859-1  (also has ISO6937 in drop-down box)
Update scan data: Download
Dump epg's events to ~/kaffeine_dvb_events.tx

Thanks for your help so far, keep it coming.  I may take a day or two to get back to you as work is very busy at the moment, so I don't get much free time at home.

---

### Post by steefjeqv on 2008-03-28
Hi,

The correct directory for the firmware is /lib/firmware/the kernel that you're using.
If you're not sure which directory to copy to, you can check your kernel version in the grub boot screen when Ubuntu starts up.
I wasn't exactly clear in the previous post about that fact. The kernel I mentioned is the Hardy Heron kernel (I just upgraded !).
When you copy the firmware to this directory, right-click on it and then go to the "Permissions" tab.
Change the read-write permissions so that everyone can use this file and set it to executable. This isn't exactly "safe" and shouldn't be used all the time, so if it isn't helpful I suggest you change it back to its original settings.

You can try w_scan as a scanning application. It doesn't use a channels.conf for scanning, instead it scans all transponders. Perhaps this will solve the missing channels problem.
It is designed to create a channels.conf for VDR, but can also create one for Kaffeine.
I've added the w_scan script which you can try out. It isn't the complete tool but it can be used as a quick way to test your DVB card.
When you've extracted the script, be sure to set it to executable.  
To run the script, you'll have to navigate(in terminal or with gksudo nautilus) to the place where you've unpacked it (your Desktop, your home folder,.......).

Using terminal : sudo ./w_scan_start.sh

Using nautilus : double-click on it, then choose run in terminal.

The link gives you the manual for the complete tool.
[http://www.edafe.org/vdr/wscan.html]("http://www.edafe.org/vdr/wscan.html")

Greetings,
Steven

---

### Post by Mad_Max_1412 on 2008-04-02
Hi,

I tried using your attachment but kept getting errors, so I went to the link you gave me and downloaded the source as it says, by copying the following into a terminal window:

> wget "http://free.pages.at/wirbel4vdr/w_scan/w_scan-20070909.tar.bz2"
root@ubuntu:~# tar xfvj w_scan-20070909.tar.bz2

I unpacked it and copied w_scan to /usr/local/bin/

I then went to my terminal window and navigated to that directory and it failed - see below:

> max@ubuntu:~$ cd /usr/local/bin
max@ubuntu:/usr/local/bin$ sudo ./w_scan_start.sh
[sudo] password for max:
sudo: ./w_scan_start.sh: command not found
max@ubuntu:/usr/local/bin$ 

I then realised the reason it failed was only w_scan was in that directory, not w_scan_start.sh.  So I then went in the terminal window to where I unpacked the tarball and tried it with this result:

> max@ubuntu:~/Desktop/w_scan-20070909$ sudo ./w_scan_start.sh
./w_scan_start.sh: 178: Syntax error: "(" unexpected
max@ubuntu:~/Desktop/w_scan-20070909$ 

The 'manual' page at the bottom says:

> DVB-T Channels for Kaffeine
root@ubuntu:~# w_scan -k > channels.dvb

so I tried that and this is what I got:

> root@ubuntu:/home/max/Desktop/w_scan-20070909# w_scan -k > channels.dvb
w_scan version 20070909
Info: using DVB adapter auto detection.
   Found DVB-T frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
frontend Philips TDA10046H DVB-T supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO not supported, trying HIERARCHY_NONE.
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
177500: 
184500: 
191500: 
198500: 
205500: 
212500: 
219500: 
226500: 
474000: 
482000: 
490000: 
498000: 
506000: 
514000: 
522000: 
530000: 
538000: 
546000: 
554000: 
562000: 
570000: 
578000: 
586000: 
594000: 
602000: 
610000: 
618000: 
626000: 
634000: 
642000: 
650000: 
658000: 
666000: 
674000: 
682000: 
690000: 
698000: 
706000: 
714000: 
722000: 
730000: 
738000: 
746000: 
754000: 
762000: 
770000: 
778000: 
786000: 
794000: 
802000: 
810000: 
818000: 
826000: 
834000: 
842000: 
850000: 
858000: 
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!
dumping lists (0 services)
Done.
root@ubuntu:/home/max/Desktop/w_scan-20070909# 

I'm assuming I didn't have to compile it as the top of the "manual" page says that a pre-compiled version was included.

I'm not having much luck, but thanks for trying.

Max

---

### Post by Audiossis on 2008-04-05
Hi all,

Just thought I'd add my two cents.

I'm not actually using Ubuntu, I'm using Fedora 7, but I'm having the same problems with my Compro DVB-T300 as you guys.

In the three days I've thus far spent working on this ,I've noticed that there seems to be an issue with the receiver sensitivity under Linux. My hardware setup (card & roof mounted antenna) works flawlessly under Win2K. I have line of sight with the transmitter towers on Mt Dandenong (Melbourne, Australia) and can get a crystal clear, stable image on every channel under Win2K (using my roof mounted antenna). So signal strength/antenna performance is not the issue for me.

Under Fedora I was intially unable to get a stable channel lock on any channel using tzap. ABC was the only one in the first instance and that would only give me a partial lock with tzap. I then tried the firmware thing suggested earlier in this forum. Lo and behold! Suddenly ABC would lock stable and I was able to get partial locks on other stations as well, where previously I could not. 

The channels.conf file wasn't really an issue for me. I just downloaded the Melbourne one from (I can't remember where) and then verified the channel frequencies and other specs in a google search.

That being said, however, I am still suffering from (apparent) poor reception issues. You should see me standing in my lounge waving a pair of hand held antenna 'round the place! Very funny :)

This leads me to the conclusion that the firmware being loaded has something to do with the receiver sensitivity. It must be able to adjust the bias on the receiver front-end amplifier to compensate for higher or lower signal strengths. 

Further, I am lead to conclued that an incorrect firmware will adjust the bias incorrectly and thus perpetuate these issues.

I don't believe that off-setting the channel frequencies (as was mentioned at the beginning of this thread) is the answer. I tried off-setting them up to 200KHz (in 5KHz steps) either side of center frequency and I found that it only exacerbates the problem.

I am currently trying to figure out how to extract the correct firmware from the Compro driver CD that came with the card while I continue to experiment with the different firmwares available through the script.

If anyone has any in-depth knowledge about theses firmwares and how to extract them from the Windows drivers, please drop me a line. I would really appreciate the help.

That's it for now, I'll post again when I know more.

Ben

BTW, I used xine, kaffeine and klear to test the DVB side of the card and I used TVTime to test the analogue side (never had a problem on the analogue side except for grainy images).

---

### Post by Mad_Max_1412 on 2008-04-07
Guys,

The [http://www.comprousa.com/en/download/tseries.html](http://www.comprousa.com/en/download/tseries.html) has a driver for "Mandriva Linux 2007 Spring" - is that any good for Ubuntu (I don't know if one version of Linux would use the same driver as another version Mandriva vs Ubuntu)

I would love to solve my problem and start recording shows.

Thanks

Max

---

### Post by Audiossis on 2008-04-08
> **Mad_Max_1412 said:**
> Guys,

The [http://www.comprousa.com/en/download/tseries.html](http://www.comprousa.com/en/download/tseries.html) has a driver for "Mandriva Linux 2007 Spring" - is that any good for Ubuntu (I don't know if one version of Linux would use the same driver as another version Mandriva vs Ubuntu)

I would love to solve my problem and start recording shows.

Thanks

Max


Don't bother with it. This driver is in fact a complete, pre-compiled mandriva kernel. You will not be able to use it with Ubuntu any more than I can with Fedora 7.

It doesn't matter which flavour of linux you use, the rules are the same. ALL kernel mode drivers MUST be compiled for that kernel and that kernel alone (that includes different versions of the same kernel).

Sorry to rain on your parade.....:)

Trick is:

1> Make sure you have GOOD reception. and by good I mean clean as well as strong. No good having a strong signal if it is full of noise.

2> Make sure you follow the suggestions earlier in this forum. Modprobe entries, channels.dvb/channels.conf files are CORRECT etc.....

3> If you can, test your hardware under Windows ON THE SAME BOX. It's good to have a base line for comparison.


Also, there is definitely a receiver sensitivity issue with the compro DVB-T300. I installed mast head amplifier at the base of my antenna on Sunday and it has made a considerable improvement.  Using Kaffeine, I can now get 26 of the 32 service detected under Windows. I shouldn't have had to do this just for the DVB-T card. The only reason I did is because I would like to attach other devices (3 TV's, 2 VCR's etc)  to the same antenna. It has cleared up the analogue signal too. I now get a crystal clear image on the analogue side of the T300 using TvTime.

Having said that though, I've noticed that If I adjust the VHF gain and amplify the signal too much, Channel TEN and SBS start to get BER and freezing issues. I may try elevating my antenna further this weekend, if I get a chance.

I can't get past the fact that, stand alone, the T-300 shouldn't have needed this. As I've said before, the card works perfectly under Windows and I've got line of site to ALL the transmitter towers on Mt Dandenong.

Still haven't figured out why the T-300 is performing SOOOO poorly under Linux....

---

### Post by steefjeqv on 2008-04-08
Hi,

Sorry for the late reply. I've been very busy gardening.

Anyway, concerning the firmware :
If I'm not mistaken you can just copy it from the Program Files directory of your Windows OS. It's most probably a .bin file called firmware or tuner ...... .
Just copy it to the correct Ubuntu dir (/lib/firmware/yourkernelversion) and rename it to dvb-fe-tda10046.fw

You can also try upgrading your dvb drivers. The link shows an excellent how-to (remember, always use sudo when using terminal) :

[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

Greetings,
Steven

---

### Post by Audiossis on 2008-04-10
> **steefjeqv said:**
> Hi,

Sorry for the late reply. I've been very busy gardening.

Anyway, concerning the firmware :
If I'm not mistaken you can just copy it from the Program Files directory of your Windows OS. It's most probably a .bin file called firmware or tuner ...... .
Just copy it to the correct Ubuntu dir (/lib/firmware/yourkernelversion) and rename it to dvb-fe-tda10046.fw

You can also try upgrading your dvb drivers. The link shows an excellent how-to (remember, always use sudo when using terminal) :

[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

Greetings,
Steven


Hi Steve,
Thanks for the reply. I've a few more questions as I am having trouble identifying the firmware file in the windows installation. Below is a list of the files installed in a working windows installation.

./ComproDTV 2.5/Teletext
./ComproDTV 2.5/Teletext/msvcp60.dll
./ComproDTV 2.5/Teletext/teletext.exe
./ComproDTV 2.5/Teletext/VbiCallback.dll
./ComproDTV 2.5/Teletext/Vtx.exe
./ComproDTV 2.5/Teletext/VTX.HLP
./ComproDTV 2.5/Teletext/WSTDEC.dll
./ComproDTV 2.5/table
./ComproDTV 2.5/table/1.ccf
./ComproDTV 2.5/table/1001.ccf
./ComproDTV 2.5/table/1852.ccf
./ComproDTV 2.5/table/353.ccf
./ComproDTV 2.5/table/81.ccf
./ComproDTV 2.5/table/852.ccf
./ComproDTV 2.5/table/86.ccf
./ComproDTV 2.5/table/886.ccf
./ComproDTV 2.5/table/90.ccf
./ComproDTV 2.5/table/DVBTTable.bin
./ComproDTV 2.5/table/tuner.tsf
./ComproDTV 2.5/rc
./ComproDTV 2.5/rc/skin.bin
./ComproDTV 2.5/rc/string.bin
./ComproDTV 2.5/rc/YCString.bin
./ComproDTV 2.5/Help
./ComproDTV 2.5/Help/ComproDTV.pdf
./ComproDTV 2.5/Filters
./ComproDTV 2.5/Filters/ComproADec.ax
./ComproDTV 2.5/Filters/ComproSM.ax
./ComproDTV 2.5/Filters/ComproTSDump.ax
./ComproDTV 2.5/Filters/CpMpgMux.ax
./ComproDTV 2.5/Filters/CproDec.ax
./ComproDTV 2.5/Filters/CproDump.ax
./ComproDTV 2.5/Filters/CproDVBScale.ax
./ComproDTV 2.5/Filters/CproDVBSplt.ax
./ComproDTV 2.5/Filters/CproInfTee.ax
./ComproDTV 2.5/Filters/CproLogo.ax
./ComproDTV 2.5/Filters/CproPsiP.ax
./ComproDTV 2.5/Filters/CproRead.ax
./ComproDTV 2.5/Filters/CproScale.ax
./ComproDTV 2.5/Filters/CproSnapShot.ax
./ComproDTV 2.5/Filters/CproSplitter.ax
./ComproDTV 2.5/Filters/CproSS2.ax
./ComproDTV 2.5/Filters/CproTrans.ax
./ComproDTV 2.5/Filters/CProVSD.ax
./ComproDTV 2.5/Filters/DVBTeletext.ax
./ComproDTV 2.5/Filters/LightSpeed.ax
./ComproDTV 2.5/Filters/TSTransform.ax
./ComproDTV 2.5/ComproDTV.exe
./ComproDTV 2.5/ComproEPG.exe
./ComproDTV 2.5/dmcrypto.dll
./ComproDTV 2.5/mfc42.dll
./ComproDTV 2.5/TweakYC.exe
./ComproDTV.pdf

I can't find any similarities between these and any of the firmware files I downloaded for the T300.
Do you have any clues?

Also, I'm not using Ubuntu. I'm actually using Fedora 7. Despite this though I have found in the past that what works in these forums for Ubuntu also works for Fedora. I'm hoping that it will be the case in this instance as well. Which leads me to my next question....

How does one tell if the firmware has or has not been loaded. I've never seen any reference to the firmware, positive or negative, when using dmesg. Is there another way to confirm one way or the other?

Thanks in advance.

Ben

---

### Post by steefjeqv on 2008-04-10
Hi,

It may be the tuner.tsf file.

You can also try looking for the firmware on your driver cd.

Has anyone tried updating the DVB drivers ? It may improve the behavior of the Compro card.
I've tried the howto myself and the installation went good, but as I'm not using the Compro it's difficult to try them out.

Greetings,
Steven

---

### Post by kreegor on 2008-07-03
I am going to bump this to see if there was any progress made on the card. I have the same card and it is being detected in mythtv but I can't scan (same as everyone else).

Has anyone been able to get it working?

---

### Post by steefjeqv on 2008-07-04
Hi,

I'm not using the Compro nor mythtv (I'm using VDR). So I haven't got any specific experience.

Did you try the following command (as previously mentioned in this thread) :

sudo modprobe saa7134-dvb

Try a scan using Kaffeine. 

If this doesn't help, you may need to add the tda firmware I've attached in one of my previous posts.

Hope this helps.

Greetings,
Steven

---

### Post by Mad_Max_1412 on 2008-07-06
Hi,

I've taken out the T300 card from the last PCI slot and moved it to another in case it made any difference, plus waited until Hardy Heron was released, but i'm still having trouble with Kaffeine only scanning and finding 3 variations of Channel 10.

I've looked at "case 1 - out of the box support" at [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers) and I get the following when I type ls -l /dev/dvb/adapter0

max@ubuntu:~$ ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 4 2008-07-06 16:30 demux0
crw-rw----+ 1 root video 212, 5 2008-07-06 16:30 dvr0
crw-rw----+ 1 root video 212, 3 2008-07-06 16:30 frontend0
crw-rw----+ 1 root video 212, 7 2008-07-06 16:30 net0

Therefore I'm going to try to do "Case 2 - Installation of LinuxTV Drivers Required"

This is where I'm going to show how new I am.  It shows examples of how to install the Mercurial software package, but what I want to know is which one do I select?  Is it the Debian, Gentoo, Fedora or Mandriva?  It's getting very confusing for a newbie.

Regards

Max

---

### Post by steefjeqv on 2008-07-06
Hi,

It's Debian.

Greetings,
Steven

---

### Post by Mad_Max_1412 on 2008-07-08
Thanks.  I followed the instructions and my Kaffeine can still only see the 3 variants of Channel 10.

Is there another TV Tuner/Recording program available that I can try?  I've heard of Myth, but when I installed it, it talked about backends, frontends and databases.

Basically I'm looking for a program similar to Kaffeine where you just start the program, tell it to initially scan for channels and away you go, either watch shows live or go into some scheduler to schedule recordings to be done.

I did find MeTV and I installed that and when I started it, it scanned for channel and found 4 varients of Channel 7 plus the 3 variants of Channel 10.  Therefore it did better at finding channels than Kaffeine, but has still missed a heap of others - including variations of the same station, there should be about 20.

Any suggestions on other programs?  In the meantime I'll see if I can find out where to obtain the information to put in the Channels.conf file for the stations which didn't appear.

FYI, here's what MeTV wrote to the conf file.

PRIME Newcastle:704500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2660:2661:2366
PRIME HD:704500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2660:2661:2410
PRIME View 1:704500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2660:2661:2411
PRIME View 2:704500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2660:2661:2412
PRIME View 3:704500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2660:2661:2413
SC10 Newcastle:690500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:401:402:2058
SC Ten:690500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:401:402:2122
SC10 HD:690500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2011:0:2090

---

### Post by kreegor on 2008-07-08
> **steefjeqv said:**
> Hi,

I'm not using the Compro nor mythtv (I'm using VDR). So I haven't got any specific experience.

Did you try the following command (as previously mentioned in this thread) :

sudo modprobe saa7134-dvb

Try a scan using Kaffeine. 

If this doesn't help, you may need to add the tda firmware I've attached in one of my previous posts.

Hope this helps.

Greetings,
Steven

Hey, yeah I have done all the above. My system has been modprobed to within an inch of its life but still no luck. I also installed kaffeine and that knew the card was there but couldn't scan with it either. I haven't tried the tda firmware though. I will find that post and give that a go.

Thanks

---

### Post by Mad_Max_1412 on 2008-07-09
> **steefjeqv said:**
> My preffered application is called VDR :

[http://www.cadsoft.de/vdr/]("http://www.cadsoft.de/vdr/")

[http://linuxtv.org/vdrwiki/index.php/Main_Page]("http://linuxtv.org/vdrwiki/index.php/Main_Page")

Greetings,
Steven

Hi Steven,

I've gone to Synaptic Package Manager and installed VDR but I can't find it in any of my pull down menus, nor is there a shortcut on the desktop.  The version that SPM is showing I've installed is 1.6.0-lubuntu2

Am I missing something?

---

### Post by steefjeqv on 2008-07-10
Hello,

The Ubuntu VDR packages are a bit incomplete (no descent channelscan) and a bit outdated, but they should work.

I doubt that VDR will change anything concerning the quality of reception. This Compro card has a problem with signal quality for one reason or another.
If someone has better results, please let us know.

VDR needs to be configured.
If you want a basic VDR setup you'll need to install some plugins :

sudo apt-get install vdr-plugin-xineliboutput libxineliboutput-sxfe xineliboutput-sxfe

Then you've got to edit some files :

sudo gedit /etc/default/vdr

enable the auto-start script by changing 0 to 1. Save and close


sudo gedit /etc/vdr/plugins/plugin.xineliboutput.conf

add or replace by the following :

--local=sxfe
--primary
--display=0.0

Save and close.

Now you can start VDR with the following command :

sudo /etc/init.d/vdr start

If everything has gone well, you should see "No Signal" on your screen.


If your Compro comes with a remote :

sudo apt-get install vdr-plugin-remote

Edit the following file :

sudo gedit /etc/vdr/plugins/plugin.remote.conf

You'll have to change -i autodetect to the following :

--input=/dev/input/eventx

where x is the number of your remote
You can find the correct event number by typing in terminal :

cat /proc/bus/input/devices

Look for something like : H: Handlers=remotex eventx 

Now restart VDR :

sudo /etc/init.d/vdr restart

You can now configure your remote on screen.


The most important thing : channelscan
The Ubuntu repo's don't come with a decent scan plugin.
You can use w_scan (like you did for kaffeine) or you can completely upgrade the VDR package with a special repository provided by a nice German guy called hanno (and e-Tobi).

If you prefer the "hanno" repo, you'll have to edit two files :

sudo gedit /etc/apt/sources.list

add the following lines :

deb [http://www.hanno.de/vdr-experimental](http://www.hanno.de/vdr-experimental) hardy base backports addons vdr-multipatch
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

Save and close

sudo gedit /etc/apt/preferences

add the following lines :

Package: * 
Pin: origin [www.hanno.de](www.hanno.de) 
Pin-Priority: 1000

Save and close.

Update your system :

sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get upgrade


Using Synaptic, look for wirbelscan and install it.

Restart vdr :

sudo /etc/init.d/vdr restart

You should be able to browse the OSD using your remote.

Setup > Plugins > wirbelscan
Country: Australia
Source Type: DVB-T

Press the green button to scan.
Wirbelscan needs some time to feed the scanned signals to VDR, so give it about 20 minutes. You may not get instant result (it may need a partial channels.conf to perform a scan).

I know this seems quite a hassle to configure but VDR is worth the effort.
As I said in the beginning of this post, don't expect any scanning miracles. 
Most important is getting this TV card to receive a decent signal.

Greetings,
Steven

---

### Post by Mad_Max_1412 on 2008-07-11
Thanks Steven, I'll give it a go tonight when I get home or at least sometime on the weekend.

BTW, I purchased a new Plasma TV a few months ago and it had a HD tuner built in, but Channel 7 would pixelate and the sound would "pop" etc.  Their support staff said that before they would accept that something was wrong, I needed to prove my reception was fine.

I paid an Antenna tech to come out and check the signal strength on each of my sockets throughout the house and he said that my signal strength was so good that it might be overpowering on some devices.

I'll see how I go after following your instructions.  I have to say though that I am very impressed with the level of support you have given myself and others in this post, and I'm also impressed with the support community in Ubuntu as a whole.  Makes newbies like me happy knowing that there are people out there willing to help.  I hope I can learn enough to return the favour to others in the future.

Cheers

Max

---

### Post by steefjeqv on 2008-07-12
Hi,

I once tried adding an extra TV signal amplifier and ended up with no TV channels. Lowering the amount of amplification solved the problem.

Congratulations with your new plasma TV.
You can always hook up your PC to your plasma. VDR makes a great settopbox.

Greetings,
Steven

---

### Post by Mad_Max_1412 on 2008-07-13
> **steefjeqv said:**
> 

Now you can start VDR with the following command :

sudo /etc/init.d/vdr start

If everything has gone well, you should see "No Signal" on your screen.



All I get when I run this is:

> max@ubuntu:~$ sudo /etc/init.d/vdr start
[sudo] password for max: 
Starting Linux Video Disk Recorder: vdr
Searching for plugins (VDR 1.6.0/1.6.0): xineliboutput.
max@ubuntu:~$ 

---

### Post by steefjeqv on 2008-07-13
Hi,

You can try the following in terminal :

xhost +

This will allow any host to use X (your display).


Then start VDR with : sudo /etc/init.d/vdr start
You can stop or restart vdr by replacing "start" with "stop" or "restart".


Something else you can try in terminal :

sudo vdr-sxfe

This will only start the vdr frontend (xine). Always make sure that vdr is running with sudo /etc/init.d/vdr start


If this doesn't do the trick, it's best to have a look at /var/log/messages. You can attach the output in your next post if you like.


Greetings,
Steven

---

