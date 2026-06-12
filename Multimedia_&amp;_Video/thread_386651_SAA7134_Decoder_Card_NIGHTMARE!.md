---
title: "SAA7134 Decoder Card NIGHTMARE!"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by netboy541 on 2007-03-17
Hello folks.

I purchased a Knockoff "Smart TV Card" off of ebay, thinking it should work OK with Kubuntu, and apparently I was wrong.

I have been working on this thing for going on 16 hours now, and my patience is pretty much shot at this point.

I plug this card into my windows laptop, and it works flawlessly. According to it, it says it's a Sinovideo card. Linux says it's a Phillips.

I get NOTHING in Kubuntu using TV time.

I've searched far and wide, and honestly, I think I've only made the situation worse because nothing makes any sense. I've read where you have to pick the tuner type, the card type, and a whole ton of other info, and I simply do not know where, or how, to find the RIGHT information.

Here's what LSPCI -VV says:
```

02:00.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors EUROPA V3 reference design
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (21000ns min, 8000ns max)
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at 3c000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [40] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-

```

and dmesg :
```

[17179592.432000] pccard: CardBus card inserted into slot 0
[17179592.528000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[17179592.528000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179592.528000] cs: IO port probe 0x820-0x8ff: clean.
[17179592.528000] cs: IO port probe 0xc00-0xcf7: clean.
[17179592.528000] cs: IO port probe 0xa00-0xaff: clean.
[17179592.580000] Linux video capture interface: v1.00
[17179592.744000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179592.936000] intel8x0_measure_ac97_clock: measured 55297 usecs
[17179592.936000] intel8x0: clocking to 48000
[17179592.976000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17179592.976000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 169
[17179592.976000] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 169, latency: 0, mmio: 0x3c000000
[17179592.976000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179592.976000] saa7134[0]: subsystem: 1131:2004, board: Philips EUROPA V3 reference design [card=69,autodetected]
[17179592.976000] saa7134[0]: board init: gpio is 40000
[17179593.112000] saa7134[0]: i2c eeprom 00: 31 11 04 20 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179593.112000] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[17179593.112000] saa7134[0]: i2c eeprom 20: 01 40 01 02 02 00 01 03 08 ff 00 b0 ff ff ff ff
[17179593.112000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.112000] saa7134[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 ff ff ff ff ff ff ff
[17179593.112000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.112000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.112000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179593.204000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17179593.228000] saa7134[0]: registered device video0 [v4l2]
[17179593.228000] saa7134[0]: registered device vbi0
[17179593.248000] saa7134 ALSA driver for DMA sound loaded
[17179593.248000] saa7134[0]/alsa: saa7134[0] at 0x3c000000 irq 169 registered as card -1

```

I undid all the damage to my modprobe.d/options file, because nothing I did there helped.

at this point, if I turn off signal level monitoring in TVTime, I can see a black screen with a little snow, but I have cable TV, and it works fine on the windows laptop, so I'm at a loss.

I could care less about recording from the card... at this point, all I want to do is watch tv off of it.

I was curious if someone out there bought one of these cards, and can guide me in the right direction.

I have searched FAR AND WIDE on this. Currently I have over 15 tabs open in firefox, and nothing I've found applies.

It seems like everyone gets video, but no audio.

I'm not getting either!

Any help would be appreciated.

I'm running Kubuntu 6.10 Edgy on a Toshiba a45-s120 laptop.


here's some more info, that might help:

```


[17179766.836000] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 169, latency: 0, mmio: 0x3c000000
[17179766.836000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179766.836000] saa7134[0]: subsystem: 1131:2004, board: Philips EUROPA V3 reference design [card=69,autodetected]
[17179766.840000] saa7134[0]: board init: gpio is 40000
[17179766.944000] saa7134[0]: Huh, no eeprom present (err=-5)?
[17179767.032000] saa7134[0]: registered device video0 [v4l2]
[17179767.036000] saa7134[0]: registered device vbi0
[17179767.056000] saa7134 ALSA driver for DMA sound loaded
[17179767.056000] saa7134[0]/alsa: saa7134[0] at 0x3c000000 irq 169 registered as card -1

```

It seems it's detecting it.
I've been referring to
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)
and
[http://www.flexbeta.net/forums/lofiv...php/t7604.html](http://www.flexbeta.net/forums/lofiv...php/t7604.html)
among other sites...

no solid answer.
Anyone got any ideas??

All I get is NO SIGNAL on everything...

Oh, and I'm in the USA, Ohio to be exact.

---

### Post by jack van de sande on 2007-03-17
Hi Netboy,

I have these same problems with sound with  a saa7134-card on my laptop (running Kubuntu 6.10)

What works for me is mplayer (I get sound with it)

Herewith my invocation of mplayer:

$> /usr/bin/mplayer -bpp 32 tv:// -tv driver=v4l2:norm=PAL:device=/dev/video0:input=0:quality=0:width=720:height=576:freq=184.000:alsa:adevice=hw.1,0:amode=1:audiorate=32000:immediatemode=0:volume=95:forceaudio: -vf rectangle=688:560:16:8,pp=fd,dsize=4/3,denoise3d=3:4:6 -vo xv 

(it is just one line of course)
Remark the peculiar invocation of alsa.
It makes use of the v4l driver.

To record TV shows I use Kalva.

Give it try,
good luck with it,

Regards,

Jack

---

### Post by netboy541 on 2007-03-17
what card type are you using?

my issue is I am not getting ANYTHING out of this card. 

No video, no sound, nothing.  
I thought I hit the jackpot when I was getting a black screen with a touch of snow, but all channels come back with "NO SIGNAL"....

If you could post your lspci regarding the card, and dmesg too, that would help me out.

I want to see if the PCI id matches...

according to what I have found, is either card # 61 (Phillips Tough DVB-T Reference Design) or 69 (Phillips EUROPA v3 Reference design)  based on the PCI id of 1131:2004

I know this card will work, but I'm getting to the point of shipping it to my Dad in Tennessee and buying another one that is guaranteed to work!

It just aggravates me to no end, on windows I was watching TV with this card in under 3 minutes.  Here we are, day 3 and I'm still not watching TV on my Kubuntu Laptop....

Any help from anyone would be appreciated! :)

---

### Post by jack van de sande on 2007-03-17
Hi Netboy,

I have another card indeed (medion 7134), however the saa7134 chipset is most of the time related to the no-sound problem.

herewith my lspci:
[INDENT]
03:00.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)
        Subsystem: Creatix Polymedia GmbH Medion 7134
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (2000ns min, 8000ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 36000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

[/INDENT]

Herewith my dmesg:
[INDENT]
[17179594.200000] saa7134[0]: found at 0000:03:00.0, rev: 1, irq: 11, latency: 0, mmio: 0x36000000
[17179594.200000] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[17179594.200000] saa7134[0]: board init: gpio is 0
[17179594.340000] saa7134[0]: i2c eeprom 00: be 16 03 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17179594.340000] saa7134[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 0c c0 08 00 00 00 00 00
[17179594.340000] saa7134[0]: i2c eeprom 20: 00 00 00 e3 ff ff ff ff ff ff ff ff ff ff ff ff
[17179594.340000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179594.340000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179594.340000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179594.340000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179594.340000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179594.360000] saa7134[0] Tuner type is 38
[17179594.500000] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[17179594.512000] tda9887 0-0043: chip found @ 0x86 (saa7134[0])
[17179594.520000] saa7134[0]: registered device video0 [v4l2]
[17179594.520000] saa7134[0]: registered device vbi0
[17179594.520000] saa7134[0]: registered device radio0
[17179594.524000] saa7134 ALSA driver for DMA sound loaded
[17179594.524000] saa7134[0]/alsa: saa7134[0] at 0x36000000 irq 11 registered as card -1
[/INDENT]

Jack

---

### Post by netboy541 on 2007-03-17
bah!  

low and behold, your card has the eeprom, and it's setting the tuner type automatically.

Mine is not.... i don't see an entry for a tuner in my logs... 

Hmmm...

Sounds like I may have a card match, but the tuner is the problem...

I have a script that unloads the module and then changes the tuner type, and then reloads the module... i'll try that...

in the meantime, I know some other poor chap has experienced this same problem somewhere...

one can only wait...

What's a laptop card that is GUARANTEED to work with linux that is cheap?

I paid 40 dollars for this card, shipping and all....  came with a nice antenna and everything...

---

### Post by bekamyn on 2007-03-23
I think I have the same card as you.

[http://cgi.ebay.com/TV-Tuner-Card-4-Laptop-PCMCIA-Cardbus-S-Video-DVR-NEW_W0QQitemZ300093383380QQcategoryZ74958QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/TV-Tuner-Card-4-Laptop-PCMCIA-Cardbus-S-Video-DVR-NEW_W0QQitemZ300093383380QQcategoryZ74958QQrdZ1QQcmdZViewItem)


The Good news:
I have Video

The Bad news:
I don't have sound

lspci -v
```

06:00.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors EUROPA V3 reference design
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at 36000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [40] Power Management version 1

```


dmesg
```

[17180450.536000] saa7134[0]: quirk: PCIPCI_NATOMA
[17180450.536000] saa7134[0]: found at 0000:06:00.0, rev: 1, irq: 11, latency: 0, mmio: 0x36000000
[17180450.536000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[17180450.536000] saa7134[0]: subsystem: 1131:2004, board: Typhoon TV+Radio 90031 [card=13,insmod option]
[17180450.536000] saa7134[0]: board init: gpio is 40000
[17180450.712000] tuner 1-004b: chip found @ 0x96 (saa7134[0])
[17180450.760000] tuner 1-004b: setting tuner address to 61
[17180450.800000] tuner 1-004b: type set to tda8290+75a
[17180450.896000] saa7134[0]: i2c eeprom 00: 31 11 04 20 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17180450.896000] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[17180450.896000] saa7134[0]: i2c eeprom 20: 01 40 01 02 02 00 01 03 08 ff 00 b0 ff ff ff ff
[17180450.896000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180450.896000] saa7134[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 ff ff ff ff ff ff ff
[17180450.896000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180450.896000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180450.896000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180453.436000] saa7134[0]: registered device video0 [v4l2]
[17180453.436000] saa7134[0]: registered device vbi0
[17180453.436000] saa7134[0]: registered device radio0
[17180453.436000] saa7134[0]/alsa: saa7134[0] at 0x36000000 irq 11 registered as card -1

```

I'm running Xubuntu kernel 
2.6.17-10-generic

lsmod
```

Module                  Size  Used by
saa7134_alsa           15392  0 
saa7134               118496  1 saa7134_alsa
ipv6                  272288  8 
speedstep_smi           7184  0 
speedstep_lib           5764  1 speedstep_smi
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_smi,cpufreq_stats
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
dock                    8716  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
lp                     12964  0 
af_packet              24584  4 
3c589_cs               14596  1 
serial_cs              19844  1 
tda9887                18448  0 
tuner                  54828  0 
video_buf              27652  2 saa7134_alsa,saa7134
compat_ioctl32          2432  1 saa7134
v4l2_common            17280  2 saa7134,tuner
v4l1_compat            15108  1 saa7134
ir_kbd_i2c              9872  1 saa7134
ir_common              28548  2 saa7134,ir_kbd_i2c
videodev               10752  1 saa7134
joydev                 11200  0 
pcmcia                 40380  2 3c589_cs,serial_cs
tsdev                   9152  0 
snd_maestro3           27524  2 
snd_ac97_codec         97696  1 snd_maestro3
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 saa7134_alsa,snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd_page_alloc         11400  1 snd_pcm
intel_agp              26012  1 
agpgart                34888  1 intel_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
3c59x                  47912  0 
mii                     6912  1 3c59x
snd                    58372  11 saa7134_alsa,snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
floppy                 63044  0 
evdev                  11392  2 
yenta_socket           28812  6 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  5 3c589_cs,serial_cs,pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                  4352  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
psmouse                41352  0 
i2c_piix4              10000  0 
serio_raw               8452  0 
i2c_core               23424  6 saa7134,i2c_ec,tda9887,tuner,ir_kbd_i2c,i2c_piix4
ext3                  142728  1 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
usbcore               134912  2 uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 5764  0 
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

```

I think that's enough info, now how I got it to give me video

I installed TVtime from Synaptic and that would run but only give me a blue screen so I started scouring Google as you did and this is what made it work for me.


Insert Card
From a terminal
# sudo rmmod saa7134_alsa
# sudo rmmod saa7134
# sudo modprobe saa7134 tuner=54 card=13
# sudo modprobe sa7134_alsa


Now I start TVTime (broadcast mode using antenna)
And after a few seconds the screen goes from black to TV !

I'm looking into getting the sound to work now.

---

### Post by netboy541 on 2007-03-23
yup.  that's the same TV card I have.

All i get in tv time under the tuner is blackness....

Same, exact thing I was getting..........

[IMG]http://i27.photobucket.com/albums/c153/netboy541/junk/tvtime-output-103800PM.png[/IMG]

I don't get it...

works great under windows....... GRR!

When I do channel searching, I get this:

[IMG]http://i27.photobucket.com/albums/c153/netboy541/junk/tvtime-output-041310AM.png[/IMG]

running TVTime in verbose uncovers TONS of weird errors...

Check it out:

```

Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/rminick/.tvtime/tvtime.xml"
I/O error : Permission denied
Cannot change owner of /home/rminick/.tvtime/tvtime.xml: Permission denied.
cpuinfo: CPU Intel(R) Celeron(R) CPU 2.60GHz, family 15, model 2, stepping 9.
cpuinfo: CPU measured at 2594.069MHz.
tvtime: Cannot set priority to -10: Permission denied.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 70101000
xfullscreen: Single-head detected, pixel aspect will be calculated.
xfullscreen: Pixel aspect ratio on the primary head is: 1299/1156 == 1.12.
xfullscreen: Using the XFree86-VidModeExtension to calculate fullscreen size.
xfullscreen: Fullscreen to 0,0 with size 1024x768.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is KWin and is EWMH compliant.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 74: Intel(R) Video Overlay.
speedycode: Using MMXEXT optimized functions.
station: Adding frequency table us-broadcast, all channels active
videoinput: Using video4linux2 driver 'saa7134', card 'Typhoon TV+Radio 90031' (bus PCI:0000:02:00.0).
videoinput: Version is 526, capabilities 5010015.
videoinput: Width 720 too high, using 704 instead as suggested by the driver.
videoinput: Maximum input width: 704 pixels.
tvtime: Sampling input at 704 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (80).
xcommon: Window fully obscured, marking window as hidden (80).
xcommon: Window made visible, marking window as visible (80).
I/O error : Permission denied


```

I get that I/O error when I try to change channels....
Any Ideas??

I even tried running it as sudo, just to see if that would make it happy...  but it didn't.......

---

### Post by bekamyn on 2007-03-26
Try this you'll need to create the file as it probably doesn't exist (found using search)

1. sudo nano /etc/modprobe.d/saa1734

2. added these lines to the file

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=13 tuner=54 oss=1

3. sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134


This give me the tuner and now the radio also. I'm still trying to get sound to work.

---

### Post by Gina on 2007-03-26
I too have the Medion card and looking into how to make it work in Ubuntu (6.06). I'll try anything suggested and if I find new things that work I'll post them.

I have only been using Ubuntu for just over a month and gradually learning how to make it work with all my hardware.  I'm very impressed and use it most of the time in preference to Win XP.

---

### Post by netboy541 on 2007-03-26
Nope. 

Already did it. :)  Didn't work. :(

Well.. I changed some stuff around actually, but it made no difference.

I had the alias stuff in an alias file, and had the tuner type and all in the modprobe statement, but I still get nothing....

I even hooked my PS2 up to the composite cable, and I don't get anything there either...

so, nothing on the tuner, nothing on composite...

but, a positive --

dmesg says:

```

[17342406.996000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17342406.996000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 169
[17342406.996000] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 169, latency: 0, mmio: 0x3c000000
[17342406.996000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17342406.996000] saa7134[0]: subsystem: 1131:2004, board: Typhoon TV+Radio 90031 [card=13,insmod option]
[17342406.996000] saa7134[0]: board init: gpio is 40000
[17342407.100000] saa7134[0]: Huh, no eeprom present (err=-5)?
[17342407.184000] saa7134[0]: registered device video0 [v4l2]
[17342407.184000] saa7134[0]: registered device vbi0
[17342407.184000] saa7134[0]: registered device radio0
[17342407.184000] cannot find the slot for index 0 (range 0-0)
[17342410.676000] saa7134 ALSA driver for DMA sound unloaded
[17342410.692000] Trying to free free IRQ169
[17342410.788000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17342410.788000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 169
[17342410.788000] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 169, latency: 64, mmio: 0x3c000000
[17342410.788000] saa7134[0]: subsystem: 1131:2004, board: Typhoon TV+Radio 90031 [card=13,insmod option]
[17342410.792000] saa7134[0]: board init: gpio is 40000
[17342410.900000] saa7134[0]: Huh, no eeprom present (err=-5)?
[17342410.956000] saa7134[0]: registered device video0 [v4l2]
[17342410.988000] saa7134[0]: registered device vbi0
[17342411.024000] saa7134[0]: registered device radio0
[17342411.108000] saa7134 ALSA driver for DMA sound loaded
[17342411.108000] saa7134[0]/alsa: saa7134[0] at 0x3c000000 irq 169 registered as card -1

```

So, it's listening to me... but it was doing that before.

On the sound issue, I've read where you can use something called sox to get it to work.
I've done that and got a ton of static...

I've yet to get this thing to work.  I'm halfway tempted to say forget it and get a happauge or something... talk about frustrating....

---

### Post by jpolega on 2007-03-27
This worked for me to fix my sound problems (both rate and disappearing sound) on a KWorld ATSC-110!

Jeff

> **jack van de sande said:**
> Hi Netboy,

I have these same problems with sound with  a saa7134-card on my laptop (running Kubuntu 6.10)

What works for me is mplayer (I get sound with it)

Herewith my invocation of mplayer:

$> /usr/bin/mplayer -bpp 32 tv:// -tv driver=v4l2:norm=PAL:device=/dev/video0:input=0:quality=0:width=720:height=576:freq=184.000:alsa:adevice=hw.1,0:amode=1:audiorate=32000:immediatemode=0:volume=95:forceaudio: -vf rectangle=688:560:16:8,pp=fd,dsize=4/3,denoise3d=3:4:6 -vo xv 

(it is just one line of course)
Remark the peculiar invocation of alsa.
It makes use of the v4l driver.

To record TV shows I use Kalva.

Give it try,
good luck with it,

Regards,

Jack

---

### Post by jpolega on 2007-03-28
Actually, once I went back and tried to do it again...it didn't work this time around.

I thought about what I had done, and realized I had just reset the ALSA subsystem by:

[FONT="Courier New"]/etc/init.d/alsa-utils reset[/FONT]

(I think, I'm typing from memory)

After doing this, mencoder will capture sounds for me.  I don't know why this is, though, and I don't think it should be this way...

Try that?

---

### Post by netboy541 on 2007-05-14
I figured when Fiesty was released, maybe this tv card would work...

Low and behold, it still don't.

If anyone has gotten this TV card to work in the UNITED STATES, please post what you did to get it to work here!!

Thanks!

:sad:

---

### Post by netboy541 on 2007-05-21
well, for anyone that reads this thread later, i gave up and bought [this tv card]("http://www.hauppauge.com/pages/products/data_hvr950.html") instead.

Here's [a review]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html") of it -- 


I am still interested in getting this TV Card I bought working, but for now... I just want something to work...
So, if you figure it out, please post in here!

---

### Post by gavinjc on 2007-05-22
I have an AverMedia AverTV 777 which uses the saa7134 chip and it works fine with some small help.

I had to manually add a couple of modules to my setup that were required for it to work:

- saa7134-dvb       (DVB module)
- mt352                  (Digital Terrestrial TV (DTV) Demodulator)

There may be others that you will need to add so just google around and check out lists of modules that ppl post and look for any that you are missing.

Good luck

---

### Post by bliffle on 2007-07-19
> **netboy541 said:**
> well, for anyone that reads this thread later, i gave up and bought [this tv card]("http://www.hauppauge.com/pages/products/data_hvr950.html") instead.

Here's [a review]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html") of it -- 


I am still interested in getting this TV Card I bought working, but for now... I just want something to work...
So, if you figure it out, please post in here!

So, did you get the Hauppage HVR-950 to work? How?

The HVR-950 has a "xc3028" instead of a saaa7134, but I don't know if the xc3028 is a knockoff, an upgrade or totally different. Anybody know?

---

### Post by bliffle on 2007-07-19
> **netboy541 said:**
> Nope. 

Already did it. :)  Didn't work. :(

Well.. I changed some stuff around actually, but it made no difference.

I had the alias stuff in an alias file, and had the tuner type and all in the modprobe statement, but I still get nothing....

I even hooked my PS2 up to the composite cable, and I don't get anything there either...

so, nothing on the tuner, nothing on composite...

but, a positive --

dmesg says:

```

[17342406.996000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17342406.996000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 169
[17342406.996000] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 169, latency: 0, mmio: 0x3c000000
[17342406.996000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17342406.996000] saa7134[0]: subsystem: 1131:2004, board: Typhoon TV+Radio 90031 [card=13,insmod option]
[17342406.996000] saa7134[0]: board init: gpio is 40000
[17342407.100000] saa7134[0]: Huh, no eeprom present (err=-5)?
[17342407.184000] saa7134[0]: registered device video0 [v4l2]
[17342407.184000] saa7134[0]: registered device vbi0
[17342407.184000] saa7134[0]: registered device radio0
[17342407.184000] cannot find the slot for index 0 (range 0-0)
[17342410.676000] saa7134 ALSA driver for DMA sound unloaded
[17342410.692000] Trying to free free IRQ169
[17342410.788000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17342410.788000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 169
[17342410.788000] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 169, latency: 64, mmio: 0x3c000000
[17342410.788000] saa7134[0]: subsystem: 1131:2004, board: Typhoon TV+Radio 90031 [card=13,insmod option]
[17342410.792000] saa7134[0]: board init: gpio is 40000
[17342410.900000] saa7134[0]: Huh, no eeprom present (err=-5)?
[17342410.956000] saa7134[0]: registered device video0 [v4l2]
[17342410.988000] saa7134[0]: registered device vbi0
[17342411.024000] saa7134[0]: registered device radio0
[17342411.108000] saa7134 ALSA driver for DMA sound loaded
[17342411.108000] saa7134[0]/alsa: saa7134[0] at 0x3c000000 irq 169 registered as card -1

```

So, it's listening to me... but it was doing that before.

On the sound issue, I've read where you can use something called sox to get it to work.
I've done that and got a ton of static...

I've yet to get this thing to work.  I'm halfway tempted to say forget it and get a happauge or something... talk about frustrating....

I've got a Hauppage HVR-950 and still haven't got it going. After 3 days.

---

