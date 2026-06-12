---
title: "What is the card and tuner no. for LifeView DVB-T hybrid PCI-mini card"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by leo_m on 2006-06-26
I have a LifeView DVB-T Hybrid PCI-mini TV card which is not supported by the saa7133 driver (it detects the card as unknown/generic board and loads it as card -1, which means the driver is not loaded).

I do not know which card no. to use for LifeView DVB-T Hybrid PCI-mini TV card.

I have found out by trial and error that the tuner type appears to be no. 54, but I do not know the card type.

I had a look at the CARDLIST.saa7134 and it is not mentioned there.

dmesg contents are as below:

```
[17179598.112000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179598.832000] saa7133[0]: found at 0000:06:02.0, rev: 208, irq: 225, latency: 181, mmio: 0xb8006000
[17179598.832000] saa7133[0]: subsystem: 5168:3307, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179598.832000] saa7133[0]: board init: gpio is 10000
[17179599.116000] saa7133[0]: i2c eeprom 00: 68 51 07 33 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179599.120000] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[17179599.120000] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 17 ff ff ff ff
[17179599.120000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179599.120000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 05 01 01 16 22 15 ff ff ff ff
[17179599.120000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179599.120000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179599.120000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179599.120000] saa7133[0]: registered device video0 [v4l2]
[17179599.120000] saa7133[0]: registered device vbi0
[17179599.280000] saa7134 ALSA driver for DMA sound loaded
[17179599.280000] saa7133[0]/alsa: saa7133[0] at 0xb8006000 irq 225 registered as card -1

```
lspci gives the following for this card:

```
0000:06:02.0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder (rev d0)

```
Can I use this card with the ID of some other card with similar/same chipset?  If so, which one?  I have already tried giving IDs of other LifeView cards and also card=82 tuner=54 [from a card which matched Philips Semiconductors SAA7133 Video Broadcast Decoder (rev d0)]

Alternatively, is there a program which talks to the hardware directly and is able to work with most cards whether or not a driver is available for those cards?

---

### Post by leo_m on 2006-06-28
The card has PCI subsystem 5168:3307 (whatever that means): I could not find a matching entry in the CARDLIST.saa7134 - Card no. 94 in kernel 2.6.17.x comes quite close (5168:3306) but that does not help me.

---

### Post by leo_m on 2006-06-29
I know that the chip on the card Philips SAA7133 is well-supported by the driver SAA7134 of Linux.  I also guess that the tuner is supported (has a chip type=54).  What I do not know is how to integrate them into the driver and put an entry for my card in the driver-detection routines.

I am not very familiar with the kernel source, but will it help if I download the kernel source, go to modify a few files for SAA7134 driver, putting in a new entry for the card-chip, tuner-chip combination or will it be solved only when a full-fledged driver is written (I mean, can I just put some entry in, which recognizes that for so and so PCI subsystem, tv card and tuner chip type, this is the card identifier, and go on to load driver for SAA7133 and tuner type 54; thus requiring no new code to be written)?

[update]  I tried to do it but it did not work.  Details:

First the output from dmesg after I recompiled the kernel with the modified saa7134 driver to detect my card:

```

leo@leo:~$ dmesg | grep saa

``` 
```

[4294685.276000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4294685.276000] saa7133[0]: found at 0000:06:02.0, rev: 208, irq: 225, latency: 181, mmio: 0xb8006000
[4294685.276000] saa7133[0]: subsystem: 5168:3307, board: LifeView FlyDVB-T Hybrid PCI-mini [card=95,autodetected]
[4294685.276000] saa7133[0]: board init: gpio is 10000
[4294685.417000] saa7133[0]: i2c eeprom 00: 68 51 07 33 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[4294685.417000] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[4294685.417000] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 17 ff ff ff ff
[4294685.417000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294685.417000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 05 01 01 16 22 15 ff ff ff ff
[4294685.417000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294685.417000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294685.417000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294685.703000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[4294685.852000] saa7133[0]: registered device video0 [v4l2]
[4294685.852000] saa7133[0]: registered device vbi0
[4294685.852000] saa7133[0]: registered device radio0
[4294685.977000] saa7134 ALSA driver for DMA sound loaded
[4294685.977000] saa7133[0]/alsa: saa7133[0] at 0xb8006000 irq 225 registered as card -1

``` 

Note that alsa still does not recognize it, perhaps modification is required in alsa related file/s as well; but this should have resulted in atleast the picture getting displayed, what do you think?

Now the files modified by me:
```

leo@leo:/usr/src/linux/drivers/media/video/saa7134$ diff -U3 /home/leo/Desktop/saa7134/saa7134-cards.c saa7134-cards.c > ~/Desktop/diff1.txt

``` 
..the result of above diff:
```

--- /home/leo/Desktop/saa7134/saa7134-cards.c    2006-06-30 18:37:38.000000000 +0100
+++ saa7134-cards.c    2006-07-06 22:03:17.000000000 +0100
@@ -2842,6 +2842,40 @@
             .gpio = 0x000000,    /* GPIO21=Low for FM radio antenna */
         },
     },
+    [SAA7134_BOARD_FLYDVBT_HYBRID_PCIMINI] = {
+        .name        = "LifeView FlyDVB-T Hybrid PCI-mini",
+        .audio_clock    = 0x00200000,
+        .tuner_type     = TUNER_PHILIPS_TDA8290,
+        .radio_type     = UNSET,
+        .tuner_addr    = ADDR_UNSET,
+        .radio_addr    = ADDR_UNSET,
+        .mpeg           = SAA7134_MPEG_DVB,
+        .gpiomask       = 0x00600000, /* Bit 21 0=Radio, Bit 22 0=TV */
+        .inputs         = {{
+            .name = name_tv,
+            .vmux = 1,
+            .amux = TV,
+            .gpio = 0x200000,    /* GPIO21=High for TV input */
+            .tv   = 1,
+        },{
+            .name = name_svideo,    /* S-Video signal on S-Video input */
+            .vmux = 8,
+            .amux = LINE2,
+        },{
+            .name = name_comp1,    /* Composite signal on S-Video input */
+            .vmux = 0,
+            .amux = LINE2,
+        },{
+            .name = name_comp2,    /* Composite input */
+            .vmux = 3,
+            .amux = LINE2,
+        }},
+        .radio = {
+            .name = name_radio,
+            .amux = TV,
+            .gpio = 0x000000,    /* GPIO21=Low for FM radio antenna */
+        },
+    },
 };
 
 const unsigned int saa7134_bcount = ARRAY_SIZE(saa7134_boards);
@@ -3391,6 +3425,12 @@
         .subdevice    = 0x3502,  /* whats the difference to 0x3306 ?*/
         .driver_data  = SAA7134_BOARD_FLYDVBT_HYBRID_CARDBUS,
     },{
+        .vendor       = PCI_VENDOR_ID_PHILIPS,
+        .device       = PCI_DEVICE_ID_PHILIPS_SAA7133,
+        .subvendor    = 0x5168,
+        .subdevice    = 0x3307,
+        .driver_data  = SAA7134_BOARD_FLYDVBT_HYBRID_PCIMINI,
+    },{
         /* --- boards without eeprom + subsystem ID --- */
         .vendor       = PCI_VENDOR_ID_PHILIPS,
         .device       = PCI_DEVICE_ID_PHILIPS_SAA7134,
@@ -3525,6 +3565,10 @@
         saa_writeb(SAA7134_GPIO_GPMODE3, 0x08);
         saa_writeb(SAA7134_GPIO_GPSTATUS3, 0x00);
         break;
+    case SAA7134_BOARD_FLYDVBT_HYBRID_PCIMINI:
+        saa_writeb(SAA7134_GPIO_GPMODE3, 0x08);
+        saa_writeb(SAA7134_GPIO_GPSTATUS3, 0x00);
+        break;
     case SAA7134_BOARD_AVERMEDIA_CARDBUS:
         /* power-up tuner chip */
         saa_andorl(SAA7134_GPIO_GPMODE0 >> 2,   0xffffffff, 0xffffffff);
@@ -3701,6 +3745,14 @@
         i2c_transfer(&dev->i2c_adap, &msg, 1);
         }
         break;
+    case SAA7134_BOARD_FLYDVBT_HYBRID_PCIMINI:
+        /* make the tda10046 find its eeprom */
+        {
+        u8 data[] = { 0x3c, 0x33, 0x62};
+        struct i2c_msg msg = {.addr=0x08, .flags=0, .buf=data, .len = sizeof(data)};
+        i2c_transfer(&dev->i2c_adap, &msg, 1);
+        }
+        break;
     case SAA7134_BOARD_KWORLD_ATSC110:
         {
             /* enable tuner */

``` 
The second file modified by me:
```

leo@leo:/usr/src/linux/drivers/media/video/saa7134$ diff -U3 /home/leo/Desktop/saa7134/saa7134.h saa7134.h > ~/Desktop/diff2.txt

``` 
...and the result of this 2nd diff:
```

--- /home/leo/Desktop/saa7134/saa7134.h    2006-06-30 18:37:38.000000000 +0100
+++ saa7134.h    2006-07-05 14:28:42.000000000 +0100
@@ -221,6 +221,7 @@
 #define SAA7134_BOARD_AVERMEDIA_A169_B1 92
 #define SAA7134_BOARD_MD7134_BRIDGE_2     93
 #define SAA7134_BOARD_FLYDVBT_HYBRID_CARDBUS 94
+#define SAA7134_BOARD_FLYDVBT_HYBRID_PCIMINI 95
 
 #define SAA7134_MAXBOARDS 8
 #define SAA7134_INPUT_MAX 8

``` 
There is no basis for me to believe this modification is correct, I just copied from some other configuration what I thought should work.

I do not know what data should go in for my card, does anyone have the correct figures?  Also, this card supports DVB as well, though at this time, I am interested in analog only.

---

### Post by leo_m on 2006-07-06
[update] It seems card type 95 has been taken by some other card in kernel 2.6.18-rc1, so will set my card's ID to a different unused no.  But this is relevant only if I am able to get it to work and then the changes are finally committed to kernel source, which is not possible until I know the correct data and rectify the mistakes...help me people...

---

### Post by leo_m on 2006-07-22
I shall update the PCI vendor and subsystem ID on the [http://pciids.sourceforge.net/](http://pciids.sourceforge.net/) .  I do not know why all the PCI devices are not entered there, should be done.

---

### Post by leo_m on 2006-07-23
[update] I tried the ndiswrapper as well.  It installs the Windows driver successfully and *perhaps* loads it as well.  But I am not able to view TV yet.  I do not know what is wrong and need help.

The lines I think are relevant from the dmesg log:
```

...
...
[17179597.784000] saa7130/34: v4l2 driver version 0.2.14 loaded
...
...
[17179597.836000] saa7133[0]: found at 0000:06:02.0, rev: 208, irq: 225, latency: 181, mmio: 0xb8006000
[17179597.836000] saa7133[0]: subsystem: 5168:3307, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179597.836000] saa7133[0]: board init: gpio is 10000
[17179597.872000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 0.
...
...
[17179598.332000] saa7133[0]: i2c eeprom 00: 68 51 07 33 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179598.332000] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[17179598.332000] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 17 ff ff ff ff
[17179598.332000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.332000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 05 01 01 16 22 15 ff ff ff ff
[17179598.332000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.332000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.332000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179598.332000] saa7133[0]: registered device video0 [v4l2]
[17179598.332000] saa7133[0]: registered device vbi0
...
...
[17179599.060000] saa7134 ALSA driver for DMA sound loaded
[17179599.060000] saa7133[0]/alsa: saa7133[0] at 0xb8006000 irq 225 registered as card -1
[17179599.084000] sdhci: ============== REGISTER DUMP ==============
[17179599.084000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179599.084000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179599.084000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179599.084000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179599.084000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179599.084000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179599.084000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179599.084000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179599.084000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179599.084000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179599.084000] sdhci: ===========================================
[17179599.132000] mmc0: SDHCI at 0xb8008800 irq 58 DMA
[17179599.236000] sdhci: ============== REGISTER DUMP ==============
[17179599.236000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179599.236000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179599.236000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179599.236000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179599.236000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179599.236000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179599.236000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179599.236000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179599.236000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179599.236000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179599.236000] sdhci: ===========================================
[17179599.288000] mmc1: SDHCI at 0xb8008400 irq 58 DMA
[17179599.340000] sdhci: ============== REGISTER DUMP ==============
[17179599.340000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179599.340000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179599.340000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179599.340000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179599.340000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179599.340000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179599.340000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179599.340000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179599.340000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179599.340000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[17179599.340000] sdhci: ===========================================
[17179599.388000] mmc2: SDHCI at 0xb8008000 irq 58 DMA
...
...
[17179600.296000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)

``` 
Output of lsmod is as follows:
```

leo@den:~$ lsmod
Module                  Size  Used by
ndiswrapper           189876  0
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
fglrx                 391756  8
speedstep_centrino      8752  1
cpufreq_userspace       6496  1
cpufreq_stats           6688  0
freq_table              4928  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
nsc_ircc               25452  0
ntfs                  111728  1
nls_cp437               5888  2
msdos                  10784  1
fat                    55548  1 msdos
ipv6                  286976  20
michael_mic             2784  2
arc4                    2048  2
ieee80211_crypt_tkip    11296  2
dm_mod                 63256  1
md_mod                 76052  0
sbp2                   25060  0
parport_pc             37988  0
lp                     12356  0
parport                39400  2 parport_pc,lp
pcmcia                 41948  0
saa7134_alsa           14400  0
af_packet              24520  4
irtty_sir               9312  0
sir_dev                21356  1 irtty_sir
irda                  217980  3 nsc_ircc,irtty_sir,sir_dev
crc_ccitt               2240  1 irda
saa7134               120672  1 saa7134_alsa
video_buf              22724  2 saa7134_alsa,saa7134
v4l2_common             6080  1 saa7134
v4l1_compat            15204  1 saa7134
ir_kbd_i2c              8876  1 saa7134
ipw2200               113548  0
i2c_core               22848  3 i2c_acpi_ec,saa7134,ir_kbd_i2c
sdhci                  16096  0
mmc_core               31816  1 sdhci
yenta_socket           30124  1
rsrc_nonstatic         14624  1 yenta_socket
pcmcia_core            45272  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211              38952  1 ipw2200
ieee80211_crypt         6528  2 ieee80211_crypt_tkip,ieee80211
ieee80211_1_1_13       39880  0
ieee80211_1_1_13_crypt     7040  1 ieee80211_1_1_13
ir_common               9892  2 saa7134,ir_kbd_i2c
sky2                   42660  0
videodev               10144  1 saa7134
snd_hda_intel          20468  4
snd_hda_codec         162160  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  5 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  2 snd_pcm
psmouse                40004  0
serio_raw               7748  0
snd                    60004  13 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm
intel_agp              24700  1
agpgart                36784  2 fglrx,intel_agp
sg                     40160  0
evdev                  10176  1
tsdev                   8032  0
usbhid                 42752  0
ext3                  148104  2
jbd                    65876  1 ext3
ide_generic             1504  0
ohci1394               37524  0
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0
uhci_hcd               35408  0
usbcore               139076  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
sd_mod                 20448  7
generic                 5124  0
ata_piix               11364  10
ahci                   18020  0
libata                 83440  2 ata_piix,ahci
scsi_mod              145960  5 sbp2,sg,sd_mod,ahci,libata
thermal                13768  0
processor              26344  2 speedstep_centrino,thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit
leo@den:~$

``` 
The ndiswrapper documentation says that if the driver installed by ndiswrapper is loaded successfully, I should get something like
```

ndiswrapper: driver ''driver1'' added

``` 
...but I do not see such a line in the dmesg log.

However, doing an ```
 ndiswrapper -l 
``` gives me the following output:
```

leo@den:~$ ndiswrapper -l
Installed ndis drivers:
lvhybrid                driver present, hardware present
leo@den:~$

``` 
This would mean that driver has been installed okay; but loading is a problem?

Trying to list the folder contents to see if the driver is actually there is positive as well:

```

leo@den:~$ ls /etc/ndiswrapper/lvhybrid/
1131:7130:5168:0138.5.conf  1131:7133:1043:5212.5.conf  1131:7133:5168:0304.5.conf  1131:7133:5168:1212.5.conf  1131:7133:5168:5212.5.conf  1131:7134:5168:0301.5.conf
1131:7130:5168:0141.5.conf  1131:7133:14C0:0212.5.conf  1131:7133:5168:0306.5.conf  1131:7133:5168:1502.5.conf  1131:7133:5168:5214.5.conf  1131:7134:5168:0302.5.conf
1131:7130:5168:0214.5.conf  1131:7133:14C0:1212.5.conf  1131:7133:5168:0307.5.conf  1131:7133:5168:2319.5.conf  1131:7133:5168:5304.5.conf  1131:7134:5168:0303.5.conf
1131:7130:5168:0309.5.conf  1131:7133:14C0:5212.5.conf  1131:7133:5168:0309.5.conf  1131:7133:5168:2502.5.conf  1131:7133.5.conf            1131:7134:5168:0309.5.conf
1131:7130:5168:5214.5.conf  1131:7133:5168:0138.5.conf  1131:7133:5168:0314.5.conf  1131:7133:5168:3306.5.conf  1131:7134:5168:0138.5.conf  1131:7134:5168:5214.5.conf
1131:7130.5.conf            1131:7133:5168:0141.5.conf  1131:7133:5168:0315.5.conf  1131:7133:5168:3307.5.conf  1131:7134:5168:0141.5.conf  1131:7134.5.conf
1131:7133:1043:0212.5.conf  1131:7133:5168:0212.5.conf  1131:7133:5168:0319.5.conf  1131:7133:5168:3319.5.conf  1131:7134:5168:0214.5.conf  lvhybrid.inf
1131:7133:1043:1212.5.conf  1131:7133:5168:0214.5.conf  1131:7133:5168:0502.5.conf  1131:7133:5168:3502.5.conf  1131:7134:5168:0300.5.conf  lvhybrid.sys
leo@den:~$

``` 
I have tried to view debug messages, if any, in  /proc/net/ndiswrapper, but the only file named debug in that folder has a zero as its contents:

```

leo@den:~$ sudo cat /proc/net/ndiswrapper/debug
0
leo@den:~$

``` 
I tried to load the module by
```

sudo modprobe ndiswrapper if_name=video0

``` 
but still cannot use my TV Card using TVTime. TVTime just sits there and I cannot change the video source as well (it shows a black screen and does not have any sources other than 'default')

Now the questions are:

1.  ndiswrapper is specifically designed for network cards; however it is able to load any driver using Windows API.  So, how do I use my TV Card using its facilities.
2.  How do I associate the audio (ALSA), and various interfaces for video related things (video0 or video1, vbi0 etc.) with the driver?

In short, how to view television using the ndiswrapper (and why does it not add the driver if I modprobe it although it has installed the driver)?

Thanks very much.

---

### Post by leo_m on 2006-11-29
I have seen a few new LifeView cards added to the latest kernels.  But not my card.  So, I wish to add the entry for it myself.  But I do not know important configuration parameters:

1.  Tuner type - is it TDA8290 or is it TD1316?
2.  GPIO setting
3.  Audio Clock - is it 0x00200000 or is it 0x00187de7?

How do I find the above information for my card?

---

