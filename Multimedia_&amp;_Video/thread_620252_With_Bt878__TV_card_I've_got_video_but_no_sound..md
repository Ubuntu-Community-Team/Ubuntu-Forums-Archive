---
title: "With Bt878  TV card I've got video but no sound."
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by SLIMwoogi on 2007-11-22
Hello. Everybody. Please give me good advices. (Sorry about my ugly grammar. I'm not a English speaker.)

I got a PCI type TV tuner card. But this is a very old product, and not a well-known model. 
But I know this card uses**[COLOR=Red] Bt878 chip[/COLOR]**, **[COLOR=Red]Philips NTSC tuner[/COLOR]**, and**[COLOR=Red] msp3400[/COLOR]** sound module , so I've configured this card with**[COLOR=Red] bttv driver[/COLOR]** with insmod option "card=24 tune =2".  Then I installed **[COLOR=Red]TVtime[/COLOR]** program and finally I got a good video. But there was **[COLOR="Red"]no sound[/COLOR]**.[COLOR=Red]:([/COLOR].

All sounds on my system  work properly except this problem. Now I'm using **Gusty Gibon(7.10)** and my sound card is embeded **[COLOR=Red]realtek sound card.[/COLOR]**

I think the audio modules for TV card are not loaded successfully. How can I handle this?

I post the results of "**[COLOR=Red]dmesg[/COLOR]**" , "**[COLOR=Red]lsmod[/COLOR]**" commands. Welcome any advice. Please help me.!!!

**<result of " lspci | grep Bt878">**

02:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
02:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

**<result of "dmesg">**
.....
[   37.914360] bttv: driver version 0.9.17 loaded
[   37.914363] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   37.914407] bttv: Bt8xx card found (0).
[   37.914420] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[   37.914433] bttv0: Bt878 (rev 2) at 0000:02:01.0, irq: 21, latency: 64, mmio: 0xfdcff000
[   37.914441] bttv0: using: Askey CPH05X/06X (bt878) [many vendors] [card=24,insmod option]
[   37.914475] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   37.962907] parport_pc 00:09: reported by Plug and Play ACPI
[   37.963014] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   37.973873] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   38.015294] bttv0: using tuner=2
[   38.015298] bttv0: i2c: checking for MSP34xx @ 0x80... found
[COLOR="Red"][   38.033605] i2c-adapter i2c-1: sendbytes: error - bailout.
[   38.033624] msp3400 1-0040: chip reset failed[/COLOR]
[   38.047609] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   38.075624] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[COLOR="Red"][   38.174780] i2c-adapter i2c-1: Client creation failed at 0x40 (-5)[/COLOR]
[   38.179205] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   38.256960] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   38.256963] tuner 1-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   38.256984] tuner 1-0060: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   38.256987] tuner 1-0060: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   38.274880] bttv0: registered device video0
[   38.274901] bttv0: registered device vbi0
[   38.274938] bttv0: PLL: 28636363 => 35468950 .. ok
[   38.303940] input: bttv IR (card=24) as /class/input/input4
[   38.304115] ACPI: PCI Interrupt 0000:00:14.5[b] -> GSI 17 (level, low) -> IRQ 20
[COLOR="Red"][   38.329646] bt878: AUDIO driver version 0.0.0 loaded[/COLOR]
[   38.329676] bt878: Bt878 AUDIO function found (0).
[   38.329687] ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 21 (level, low) -> IRQ 21
[   38.329695] bt878_probe: card id=[0x0], Unknown card.
[   38.329696] Exiting..
[   38.329702] ACPI: PCI interrupt for device 0000:02:01.1 disabled
[COLOR="Red"][   38.329705] bt878: probe of 0000:02:01.1 failed with error -22[/COLOR]
[   39.377990] lp0: using parport0 (interrupt-driven).
.....
[13947.956000] bttv0: PLL can sleep, using XTAL (28636363).



<result of "lsmod">
Module                  Size  Used by
af_packet              24840  2 
ipv6                  273892  10 
fglrx                 656352  53 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
vboxdrv                60208  0 
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
dock                   10656  0 
sbs                    19592  0 
ac                      6148  0 
container               5504  0 
button                  8976  0 
video                  18060  0 
battery                11012  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
lp                     12580  0 
[COLOR="Red"]bt878                  11832  0 [/COLOR]
snd_atiixp             21132  1 
snd_ac97_codec        100644  1 snd_atiixp
tuner                  63144  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
tvaudio                24348  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
[COLOR="Red"]msp3400                32288  0 [/COLOR]
psmouse                39952  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
serio_raw               8068  0 
8139cp                 25088  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
[COLOR="Red"]bttv                  177012  1 bt878[/COLOR]
pcspkr                  4224  0 
k8temp                  6656  0 
video_buf              26244  1 bttv
ir_common              35460  1 bttv
compat_ioctl32          2304  1 bttv
i2c_algo_bit            7428  1 bttv
usbhid                 29536  0 
hid                    28928  1 usbhid
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  2 
btcx_risc               5896  1 bttv
tveeprom               16784  1 bttv
videodev               29312  1 bttv
v4l2_common            18432  5 tuner,tvaudio,msp3400,bttv,videodev
v4l1_compat            15364  2 bttv,videodev
snd                    54660  12 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_atiixp,snd_pcm
usb_storage            73024  0 
libusual               18448  1 usb_storage
usblp                  15104  0 
i2c_piix4               9740  0 
[COLOR="Red"]i2c_core               26112  7 tuner,tvaudio,msp3400,bttv,i2c_algo_bit,tveeprom,i2c_piix4[/COLOR]
ati_agp                10124  0 
agpgart                35016  2 fglrx,ati_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
ata_generic             8452  0 
floppy                 60004  0 
8139too                27776  0 
mii                     6528  2 8139cp,8139too
atiixp                  7056  0 [permanent]
ide_core              116804  4 ide_cd,ide_disk,usb_storage,atiixp
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  7 usbhid,usb_storage,libusual,usblp,ehci_hcd,ohci_hcd
sata_sil               12168  3 
libata                125168  2 ata_generic,sata_sil
scsi_mod              147084  4 usb_storage,sg,sd_mod,libata
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by stony on 2007-11-22
Hi SLIMwoogi
got the same problem here.

I have a Hercules SmartTV stereo pci card. There is a short sound cable that connects the TV-card and my sound card. If i tap on the end of it i can here the crackling in my speakers. so it's not acctually a sound problem of Ubuntu, Rather the TV-card does not output anything.

My setup works perfectly under windows but i do get a better picture under linux. :confused:

I know my card is of card=100 and tuner=38 because that used to work on a mandrake installation i had about 2 years back.

I found a thread where someone suggested to find a volume slider that could be muted. I tried all of the available ones. Suddenly after some random reboot (Ubuntu setup is not a week old) there was sound from tv. The line-in slider did work. so i disabled/hid all sliders that did not affect the sound output. After next reboot sound was gone again, still is. Tryed again (the thing with all volume slider), but i still don't have any sound from TV-card ;(

maybe it helps ???

found this in dmesg
> 
[   12.832000] bttv: driver version 0.9.17 loaded
[   12.832000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   12.832000] bttv: Bt8xx card found (0).
[   12.832000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   12.832000] bttv0: Bt878 (rev 17) at 0000:01:08.0, irq: 21, latency: 32, mmio: 0xe7000000
[   12.832000] bttv0: subsystem: 1540:952b (UNKNOWN)
[   12.832000] please mail id, board name and the correct card= insmod option to [email]video4linux-list@redhat.com[/email]
[   12.832000] bttv0: using: Hercules Smart TV Stereo [card=100,insmod option]
[   12.832000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   12.832000] bt878 #0 [sw]: Test OK
[   12.832000] bttv0: using tuner=38
[   12.832000] bttv0: i2c: checking for TDA9875 @ 0xb0... found
[   12.840000] tda9875: no such chip at 0xb0 (dic=0x11 rev=0x2)
[   12.840000] i2c-adapter i2c-2: Client creation failed at 0x58 (1)
[   12.840000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   12.860000] tvaudio 2-0058: found tda9874a.
[   12.860000] tvaudio 2-0058: tda9874h/a found @ 0xb0 (bt878 #0 [sw])
[   12.880000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   12.896000] i2c-adapter i2c-2: sendbytes: error - bailout.
[   12.900000] tuner 2-004b: chip found @ 0x96 (bt878 #0 [sw])
[   12.900000] tda9887 2-004b: tda988[5/6/7] found @ 0x4b (tuner)
[   12.900000] tuner 2-0060: All bytes are equal. It is not a TEA5767
[   12.900000] tuner 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   12.900000] tuner 2-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   12.900000] tuner 2-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   12.908000] bttv0: registered device video0
[   12.908000] bttv0: registered device vbi0
[   12.908000] bttv0: PLL: 28636363 => 35468950 .. ok
[   12.944000] i2c-adapter i2c-2: sendbytes: error - bailout.
[   12.944000] tda9887 2-004b: i2c i/o error: rc == -14 (should be 4)
[   12.956000] bt878: AUDIO driver version 0.0.0 loaded
[   12.956000] bt878: Bt878 AUDIO function found (0).
[   12.956000] ACPI: PCI Interrupt 0000:01:08.1[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   12.956000] bt878_probe: card id=[0x952b1540], Unknown card.
[   12.956000] Exiting..


---

### Post by SLIMwoogi on 2007-11-22
Thank you. stony. But I've tried all the things you said. But no effect.

Now my speaker connected to TV card's sound out port directly to check the sound out. But I can't get any sound still.

This device works perfectly on windows platform.

Anyway, now I'm trying everything I can. If I  find a good solution, I will post it in this place. 

Thank you again. 
Good luck.

---

### Post by kvonb on 2007-11-22
-

---

### Post by SLIMwoogi on 2007-11-22
I think this is my problem. In the picture which I attached,  there presents nothing under Bt878 Audio Capture device.

I think there should be something like a "msp4300".

Am I wrong?

Any advice. please.

---

### Post by SLIMwoogi on 2007-11-22
> **kvonb said:**
> Have you tried connecting the audio out from the TV card to the input of your onboard sound card?

Then make sure you enable recording from your line in, and of course unmute it :).

That's what I do, I don't actually use the sound device directly on my TV card.


Yes, That's my original setting. I've tried all the testing on that setting you said. But there was no sound. So I thought this is not a ubuntu sound setting problem. Then connected my speaker directly to my TVcard sound out port.(no sound too)

I think this is a just kind of  audio driver problem.

---

### Post by kvonb on 2007-11-23
_-_

---

### Post by stony on 2007-11-23
i just found this:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789")

especially this part could be interesting (at least i thought so)

> Scott James Remnant  wrote on 2006-04-03:  (permalink)

The easiest "quick fix" for this is to do the following:

  echo bt878 > /etc/modprobe.d/blacklist-bt878
  echo bt878 >> /etc/modules

This blacklists bt878 (and thus bttv, which is what breaks snd_bt87x) from being automatically loaded for the device, leaving only snd_bt87x loaded; and then causes bt878 to be loaded manually later in the boot sequence, thus forcing the load order.

This is a "hack" though, the correct fix is to stop bttv from breaking snd_bt87x in the first place and allow them to be loaded in any order.


unfortunately it did NOT work for me :(

going to try the "Comprehensive Sound Problem Solutions Guide v0.5e" now.

---

### Post by stony on 2007-11-23
nothing applicable found in "Comprehensive Sound Problem Solutions Guide v0.5e"

as said above, the line-in on the audigy is working fine. The TV-card (hercules smart tv in my machine) gives no output :(

---

### Post by gethuk on 2007-11-24
look like my problem.
I use PixelView P7000 and have something mysterius (?). When I put options card=49 or card=49 and tuner=38, my tuner identified as Philips FM1216ME/I. In this case, tvtime did'nt show any picture (no freq recognized); but when I add radio=1 on the options, my tuner identified as Philips FI1246... I try to change tuner number (1, 3, 5, 23, 24, 38, 41), but still identified as FI1246.. In this case, tvtime showing picture with no sound.

Btw, why did v4l register only device video0 and vbi0, but not for radio0?

---

### Post by stony on 2007-11-26
found this:
[http://www.linuxtv.org/v4lwiki/index.php/Hercules_Smart_TV_2_Stereo]("http://www.linuxtv.org/v4lwiki/index.php/Hercules_Smart_TV_2_Stereo")

but unfortunately still no luck, nor sound :(

> Dmesg:
[ 1098.604000] tvaudio 2-004b: pic16c54 (PV951): I/O error (write reg2=0x60)
[ 1098.604000] tvaudio 2-004b: pic16c54 (PV951): I/O error (write reg2=0x60)
[ 1100.372000] tvaudio 2-004b: pic16c54 (PV951): I/O error (write reg2=0x10)
[ 1100.372000] i2c-adapter i2c-2: sendbytes: error - bailout.
[ 1100.372000] tvaudio 2-004b: pic16c54 (PV951): I/O error (write reg2=0x10)


---

### Post by stager on 2007-12-29
Hi! Similar problem (with solution) is described in another thread:
[http://ubuntuforums.org/showthread.php?t=647722]("http://ubuntuforums.org/showthread.php?t=647722")

May be it helps...

---

### Post by lil_niles on 2008-02-23
I have the exact same problem. I will try the hack mentioned above, and report back. I have scoured the interwebs and found nothing but people with this exact problem and no solutions for it.

---

### Post by lil_niles on 2008-02-23
I tried blacklisting the bt878 deal and that did not work. I realize i'm bumping an old thread, but this problem has never been solved. Anyone have anything to say?

---

### Post by bunuhdiri on 2008-02-23
hi there
i'm have a tv card with exactly same chipset
i just installed ubuntu yesterday
where do i find the driver?

---

### Post by librano on 2008-02-24
hi all!

this worked for me on an ancient Brooktree bt878 card :) 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789/comments/40](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789/comments/40)

cheers!

---

