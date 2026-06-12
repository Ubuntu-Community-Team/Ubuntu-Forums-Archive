---
title: "Yet again, a tv-tuner card problem"
date: 2006-03-07
forum: Multimedia &amp; Video
---

### Post by den benne on 2006-03-07
hey,
I recently found an old tv-tuner car, a "genius video wonder II" and now I would really like it to run on my breezy.
I just plugged it in and breezy auto-detected it (correctly?)-> see [device manager](http://studwww.ugent.be/~bdcooman/tvkaart.png)

then I installed tvtime and scanned for channels, but all I get is a blue screen and a "no signal".

I searched this forum (and others), but I don't really know what to do
I hope that someone can help me? 

grtz

PS: if you need more info-> just shoot


EDIT:
some more info:
lsmod:
```

Module                  Size  Used by
sd_mod                 17424  0
usb_storage            64704  0
scsi_mod              124872  2 sd_mod,usb_storage
tun                    11008  1
binfmt_misc            10888  1
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  8
af_packet              20232  2
analog                 10528  0
snd_mpu401              6344  1
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
usblp                  11776  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  3
gameport               14472  2 analog,snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  3 snd_pcm_oss
snd_pcm                78344  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  2 snd_mpu401,snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  15 snd_mpu401,snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  3 snd
i2c_viapro              7696  0
via_ircc               23700  0
irda                  159804  1 via_ircc
crc_ccitt               2176  1 irda
bttv                  141456  0
video_buf              19844  1 bttv
firmware_class          9472  1 bttv
i2c_algo_bit            8584  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4872  1 bttv
tveeprom               12568  1 bttv
i2c_core               19728  5 i2c_acpi_ec,i2c_viapro,bttv,i2c_algo_bit,tveeprom
videodev                9344  1 bttv
pci_hotplug            24628  0
via_agp                 9472  1
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
nvidia               3711364  12
agpgart                32328  2 via_agp,nvidia
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  3
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
uhci_hcd               28048  0
usbcore               104316  4 usb_storage,usblp,uhci_hcd
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  7
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  991
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

lspci:
```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:09.0 Multimedia video controller: Brooktree Corporation Bt848 Video Capture (rev 12)
0000:00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

---

### Post by mikedtemple on 2006-03-07
Did you install bttv drivers or are they included in the kernel?  (I don't remember!)


do a cat /var/log/syslog | grep bttv and post it

---

### Post by den benne on 2006-03-07
[QUOTE="mikedtemple"]Did you install bttv drivers or are they included in the kernel?  (I don't remember!)
[/QUOTE]

I didn't install any drivers

> 
do a cat /var/log/syslog | grep bttv and post it

here you go:
```

Mar  7 18:29:50 localhost kernel: [4333303.398000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:30:01 localhost kernel: [4333314.498000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:30:18 localhost kernel: [4333331.382000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:30:29 localhost kernel: [4333342.364000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:30:40 localhost kernel: [4333353.869000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:30:54 localhost kernel: [4333367.184000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:30:55 localhost kernel: [4333368.890000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:31:11 localhost kernel: [4333384.038000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:31:13 localhost kernel: [4333386.091000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:31:30 localhost kernel: [4333403.162000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:31:31 localhost kernel: [4333404.178000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:31:38 localhost kernel: [4333411.139000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:31:44 localhost kernel: [4333417.741000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:31:47 localhost kernel: [4333420.524000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:31:51 localhost kernel: [4333424.848000] bttv0: SCERR @ 089b801c,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:31:57 localhost kernel: [4333430.072000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:31:59 localhost kernel: [4333432.009000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:32:00 localhost kernel: [4333433.915000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:32:30 localhost kernel: [4333463.162000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:32:34 localhost kernel: [4333467.538000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:32:42 localhost kernel: [4333475.405000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 18:32:46 localhost kernel: [4333479.401000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 18:32:47 localhost kernel: [4333480.256000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:03:21 localhost kernel: [4338915.215000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:03:24 localhost kernel: [4338918.597000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:03:31 localhost kernel: [4338925.654000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:03:37 localhost kernel: [4338931.583000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:03:38 localhost kernel: [4338932.559000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:03:54 localhost kernel: [4338948.555000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:04:01 localhost kernel: [4338955.418000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:04:12 localhost kernel: [4338966.040000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:04:31 localhost kernel: [4338985.745000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:04:32 localhost kernel: [4338986.548000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:04:34 localhost kernel: [4338988.306000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:04:44 localhost kernel: [4338997.961000] bttv0: SCERR @ 089b801c,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:04:45 localhost kernel: [4338999.790000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:04:48 localhost kernel: [4339002.058000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:04:50 localhost kernel: [4339003.962000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:04:51 localhost kernel: [4339005.131000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:04:54 localhost kernel: [4339008.144000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:05:08 localhost kernel: [4339022.580000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:05:19 localhost kernel: [4339033.266000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:05:29 localhost kernel: [4339043.431000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:05:31 localhost kernel: [4339045.394000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:05:38 localhost kernel: [4339052.800000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:05:46 localhost kernel: [4339060.739000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:05:56 localhost kernel: [4339070.267000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:06:00 localhost kernel: [4339074.128000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:06:00 localhost kernel: [4339074.270000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:06:03 localhost kernel: [4339077.095000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:06:05 localhost kernel: [4339079.544000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:06:07 localhost kernel: [4339081.100000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:06:11 localhost kernel: [4339085.020000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:06:18 localhost kernel: [4339092.782000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:06:20 localhost kernel: [4339094.262000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:06:24 localhost kernel: [4339098.586000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:06:27 localhost kernel: [4339101.766000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:06:31 localhost kernel: [4339104.994000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:06:35 localhost kernel: [4339109.588000] bttv0: SCERR @ 089b801c,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:06:37 localhost kernel: [4339111.020000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:06:42 localhost kernel: [4339116.688000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:06:51 localhost kernel: [4339125.197000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:07:01 localhost kernel: [4339134.946000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:07:06 localhost kernel: [4339140.614000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:07:08 localhost kernel: [4339142.400000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:07:16 localhost kernel: [4339150.154000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:07:17 localhost kernel: [4339151.086000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:07:20 localhost kernel: [4339154.605000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:07:25 localhost kernel: [4339158.991000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:07:40 localhost kernel: [4339174.620000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:07:42 localhost kernel: [4339175.913000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:07:46 localhost kernel: [4339180.271000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:07:53 localhost kernel: [4339187.629000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:08:07 localhost kernel: [4339201.045000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:08:28 localhost kernel: [4339222.732000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:08:32 localhost kernel: [4339226.713000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:08:39 localhost kernel: [4339232.942000] bttv0: SCERR @ 089b8014,bits: HSYNC OFLOW FBUS SCERR*
Mar  7 20:08:48 localhost kernel: [4339242.558000] bttv0: SCERR @ 089b8014,bits: OFLOW FBUS SCERR*
Mar  7 20:14:36 localhost kernel: [4294704.290000] bttv: driver version 0.9.15 loaded
Mar  7 20:14:36 localhost kernel: [4294704.290000] bttv: using 8 buffers with 2080k (520 pages) each for capture
Mar  7 20:14:36 localhost kernel: [4294704.297000] bttv: Bt8xx card found (0).
Mar  7 20:14:36 localhost kernel: [4294704.298000] bttv0: Bt848 (rev 18) at 0000:00:09.0, irq: 5, latency: 32, mmio: 0xea000000
Mar  7 20:14:36 localhost kernel: [4294704.298000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
Mar  7 20:14:36 localhost kernel: [4294704.298000] bttv0: gpio: en=00000000, out=00000000 in=0084ff00 [init]
Mar  7 20:14:36 localhost kernel: [4294704.331000] tveeprom(bttv internal): Huh, no eeprom present (err=-121)?
Mar  7 20:14:36 localhost kernel: [4294704.331000] bttv0: using tuner=-1
Mar  7 20:14:36 localhost kernel: [4294704.331000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
Mar  7 20:14:36 localhost kernel: [4294704.334000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
Mar  7 20:14:36 localhost kernel: [4294704.336000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
Mar  7 20:14:36 localhost kernel: [4294704.338000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
Mar  7 20:14:36 localhost kernel: [4294704.370000] bttv0: registered device video0
Mar  7 20:14:36 localhost kernel: [4294704.400000] bttv0: registered device vbi0Mar  7 20:17:33 localhost kernel: [4294901.580000] bttv0: SCERR @ 088ef014,bits: HSYNC FBUS SCERR*
Mar  7 20:17:36 localhost kernel: [4294904.127000] bttv0: SCERR @ 088ef014,bits: FBUS SCERR*

```

---

### Post by den benne on 2006-03-07
EDIT: sorry, double post

---

### Post by ignatz42 on 2006-03-07
Are you sure the card is good?

I'm no expert, but did some searching and bumped into this thread:

[http://www.uwsg.iu.edu/hypermail/linux/kernel/0502.3/0591.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0502.3/0591.html)

which suggests that the error message you're getting:

> 
Mar  7 20:14:36 localhost kernel: [4294704.298000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
Mar  7 20:14:36 localhost kernel: [4294704.298000] bttv0: gpio: en=00000000, out=00000000 in=0084ff00 [init]
Mar  7 20:14:36 localhost kernel: [4294704.331000] tveeprom(bttv internal): Huh, no eeprom present (err=-121)?
Mar  7 20:14:36 localhost kernel: [4294704.331000] bttv0: using tuner=-1


might mean that your card is dead.

Again, another thing I noticed in the output was that the card was detected as UNKNOWN/GENERIC.  I *think* that you might be able specify your card from this [list]("http://linuxtv.org/cgi-bin/viewcvs.cgi/v4l-dvb/linux/Documentation/video4linux/CARDLIST.bttv?root=v4l&view=markup"). but don't know how. Yet. :)  This [link]("http://www.mythtv.org/wiki/index.php/Bttv") might help.

I hope this helps.

---

### Post by den benne on 2006-03-08
yes, the "generic" is probably the cause why it isn't working
sadly I'm not able to find the cardnumber(or the tuner I need) in any list (maybe it isn't supported?)

---

### Post by den benne on 2006-03-15
Thanks ignatz42, your howto comined with some google helped me a lot:
I have managed to get it working with card=30 and tuner=24

I only had to use thes 2 commands (sudo):
```

modprobe bttv card=30
modprobe tuner type=24

```

this cardnumber/tuner doesn't seem to work a 100%, but at the moment I have a pretty good image. I also read somewhere to use card=8, so maybe I'll try that later.

---

### Post by den benne on 2006-03-22
oke, cardnumber 8 does'nt seem to work, so I'll stick to number 30

now, I can get the card to work through a manual modprobe, but after a reboot its all gone. so how do you make it stick?

---

### Post by Michael Matthews on 2006-03-22
Probably need to put something in /etc/modprobe.d (?) or something. used to be /etc/modules.conf in earlier linux. Research this in docs or someone might chime in.
Could put it in a startup script if you had to, in /etc/rc3.d but I think there is a more appropriate config.

---

### Post by mikedtemple on 2006-03-28
Yeah, It's /etc/modules

put it at the bottom.


[QUOTE=Michael Matthews]Probably need to put something in /etc/modprobe.d (?) or something. used to be /etc/modules.conf in earlier linux. Research this in docs or someone might chime in.
Could put it in a startup script if you had to, in /etc/rc3.d but I think there is a more appropriate config.[/QUOTE]

---

### Post by den benne on 2006-03-29
[QUOTE=mikedtemple]Yeah, It's /etc/modules

put it at the bottom.[/QUOTE]

yep, that did the trick, thanks

now trying to get my remote to work :-?

---

