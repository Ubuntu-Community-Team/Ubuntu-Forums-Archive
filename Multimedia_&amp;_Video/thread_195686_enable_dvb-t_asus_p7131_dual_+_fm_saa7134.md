---
title: "enable dvb-t asus p7131 dual + fm saa7134"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by rosebud on 2006-06-13
hello
First thanks for the ubuntu developers for this great distribution!!
 
 I just bought a asus mycinema p7131 dual dvb-t + fm which seems to work 
 ok with saa7134 . Kaffeine supports the device and accepts "autoscan".
 
 I live in France, the "autoscan" fr-Paris ( i have tested with an another usb-tv card ) in kaffeine feature seems to work but detect nothing. ( the signal bar goes between 100% to 60% and snr stays most of the time at 60%; 49% ...) but i have any channel :sad: .
 
Anybody knows how to enable dvb-t for my tv-card asus mycinema p7131 dual ( hybrid ) + fm.

thank you for your help

kernel 2.6.15-23-k7 dapper 6.06 LTS

lspci:

```
0000:01:09.0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder (rev d0)

```

after modprobe saa7134_dvb, i have

dmesg :
```

[4294667.296000] Linux version 2.6.15-23-k7 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294670.051000] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
[4294676.647000] usbcore: registered new driver usbfs
[4294676.648000] usbcore: registered new driver hub
[4294677.009000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[4294677.009000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[4294677.009000] ehci_hcd 0000:00:02.2: debug port 1
[4294677.009000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[4294677.009000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[4294684.880000] agpgart: Detected NVIDIA nForce2 chipset
[4294684.884000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294685.294000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[4294685.294000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5500
[4294685.303000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.
[4294685.920000] Linux video capture interface: v1.00
[4294685.967000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Logitech QC Communicate STX
[4294686.130000] intel8x0_measure_ac97_clock: measured 50715 usecs
[4294686.130000] intel8x0: clocking to 47422
[4294686.131000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294686.361000] nvidia: module license 'NVIDIA' taints kernel.
[4294686.368000] **** SET: Misaligned resource pointer: f7435ba2 Type 07 Len 0
[4294686.368000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[4294686.368000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 201
[4294686.369000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[4294686.569000] usbcore: registered new driver spca5xx
[4294686.569000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[4294686.643000] usbcore: registered new driver snd-usb-audio
[4294686.657000] usbcore: registered new driver hiddev
[4294686.672000] input: Logitech Logitech BT Mini-Receiver as /class/input/input2
[4294686.672000] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:02.1-2.2
[4294686.713000] input: Logitech Logitech BT Mini-Receiver as /class/input/input3
[4294686.714000] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:02.1-2.3
[4294686.714000] usbcore: registered new driver usbhid
[4294686.714000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294686.816000] ts: Compaq touchscreen protocol output

[4294686.992000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4294686.993000] **** SET: Misaligned resource pointer: f74d1e42 Type 07 Len 0
[4294686.993000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[4294686.993000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 209
[4294686.993000] saa7133[0]: found at 0000:01:09.0, rev: 208, irq: 209, latency: 32, mmio: 0xe8000000
[4294686.993000] saa7133[0]: subsystem: 1043:4862, board: ASUSTeK P7131 Dual [card=78,autodetected]
[4294686.993000] saa7133[0]: board init: gpio is 40000
[4294687.116000] saa7133[0]: i2c eeprom 00: 43 10 62 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[4294687.116000] saa7133[0]: i2c eeprom 10: 00 01 20 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[4294687.116000] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d6 ff ff ff ff
[4294687.116000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294687.116000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 00 ff ff ff ff ff ff
[4294687.116000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294687.116000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294687.116000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294687.148000] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[4294687.176000] tuner 2-004b: setting tuner address to 61
[4294687.201000] tuner 2-004b: tuner: type set to tda8290+75a
[4294687.236000] saa7133[0]: registered device video1 [v4l2]
[4294687.236000] saa7133[0]: registered device vbi0
[4294687.237000] saa7133[0]: registered device radio0
[4294687.248000] saa7134 ALSA driver for DMA sound loaded
[4294687.248000] saa7133[0]/alsa: saa7133[0] at 0xe8000000 irq 209 registered as card -1
[4294687.676000] lp0: using parport0 (interrupt-driven).
[4294687.707000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294702.175000] Bluetooth: Core ver 2.8

[4295132.246000] DVB: registering new adapter (saa7133[0]).
[4295132.246000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[4295174.893000] tda1004x: found firmware revision 33 -- invalid
[4295174.919000] tda1004x: booting from eeprom
[4295175.426000] tda1004x: found firmware revision 29 -- ok
[4295187.217000] tda1004x: found firmware revision 29 -- ok

```

when i run kaffeine in console i have this:

```

buddy@ubuntu:~$ kaffeine
Link points to "/tmp/ksocket-buddy"
Link points to "/tmp/kde-buddy"
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DVB 1 : Aucun fichier ou répertoire de ce type
DVB 2 : Aucun fichier ou répertoire de ce type
DVB 3 : Aucun fichier ou répertoire de ce type
Card 0 : opened ( Philips TDA10046H DVB-T )
Card 1 :openFe :: Aucun fichier ou répertoire de ce type
Card 2 :openFe :: Aucun fichier ou répertoire de ce type
Card 3 :openFe :: Aucun fichier ou répertoire de ce type
buddy@ubuntu:~$ Using DVB card "Philips TDA10046H DVB-T"
tuning DVB-T to 474000000 Hz
inv:2 bw:0 fecH:2 fecL:9 mod:3 tm:1 gi:0 hier:0
polling....
Getting frontend event
polling....
Getting frontend event
polling....
Getting frontend event
polling....
Getting frontend event
polling....
Getting frontend event
polling....
Getting frontend event
polling....
Getting frontend event
polling....
Getting frontend event
dvbsi : Cant tune DVB
Frontend closed

```


for the french readers

je n'arrive pas à configurer cet carte tnt ( dvb-t) , kaffeine se lance, il me propose l'autoscan, je choisis fr-Paris, le scan se lance, le signal est bon souvent 100% mais aucune chaîne n'apparait ou n'est mémorisée.

le fr-Paris est bon car testé avec une autre carte dvb usb.

---

### Post by Jose Catre-Vandis on 2006-06-13
Have you first tried the dvb scan and other utils for the kernel, to verify that your card and signal are OK?

FWIW your dmesg appears to read OK, I have the same card but with a 1043:4857 subset which doesn't seem to be fully supported yet!

---

### Post by rosebud on 2006-06-14
thanks

in the web site of asus it said for xp

ASUS My Cinema-P7131Dual card Firmware AA.F7.C0.01
If ASUS My Cinema-P7131Dual card can't scan all the TV channels, please update this BIOS for resolving this issue.

Notice:
If a warning message "Wrong_ASUS_Tiger_Board_Sub-vendor ID!" shows while running this firmware update tool, it means no need to update firmware of your My Cinema 7131 Dual card.


my card don't need an update firmware because i can scan all channels in xp

---

### Post by Jose Catre-Vandis on 2006-06-14
Yep, my card works perfectly in XP too, but refuses to scan under Linux. just suggesting you try out the linuxtv scan utilities in the console to see if you can create a channels list. This might help to identify why it won't work. Otherwise try joining the [https://www.redhat.com/mailman/listinfo/video4linux-list](https://www.redhat.com/mailman/listinfo/video4linux-list) mailing list. There is a guy there called Hartmut who knows these cards inside and out.

Also worth a read here too: [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

---

### Post by rosebud on 2006-06-15
hello thanks

i have read the gentoo wiki

i have post on mailing-list, he says for my dmesg :[I]

card=78 1043:4862 works since about eight or nine months for me now. With nice FM stereo sound since about four months after Hartmut adjusted the saa7133/35/31e to the special 5.5MHz FM IF the Philips silicon tuners use. Is in 2.6.16.

[4295132.246000] DVB: registering new adapter (saa7133[0]).
[4295132.246000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[4295174.893000] tda1004x: found firmware revision 33 -- invalid
[4295174.919000] tda1004x: booting from eeprom
[4295175.426000] tda1004x: found firmware revision 29 -- ok
[4295187.217000] tda1004x: found firmware revision 29 -- ok

Here we can see that a older revision of the tda1004x is in use, which misses some sensitivity improvements Hartmut added later. Some reported to get nothing without it, for me it was only one transponder not found.
Upgrade the kernel or install a v4l-dvb mercurial snapshot.[/I]

how can get v4l-dvb mercurial snapshot ( step by step) and what can i do if i have error message because my kernel is an 2.6.15-25-k7

thanks

---

### Post by rosebud on 2006-06-15
:D thanks for your help it's work:D :D

---

### Post by Jose Catre-Vandis on 2006-06-15
What did you do that was different?

---

### Post by rosebud on 2006-06-15
hello

before i boot on 2.6.15-23-k7, i remove my logitech webcam communicate stx
- first i have downloaded  linux-source linux-source-2.6.15 linux-headers-2.6.15-23-k7 linux-headers-2.6.15-23-386 linux-headers-2.6.15-23 all codecs win32, libcss, ogg...

```
sudo adduser your_user src
``` ( perhaps it's no necessary)

(firmware are on linux-tv) 

```
sudo cp dvb-fe-tda10046.fw /lib/firmware
``` 

```
sudo apt-get install mercurial
```
 
```

hg clone http://linuxtv.org/hg/~mrechberger/v4l-dvb
cd v4l-dvb
sudo make clean
sudo make distclean
sudo make ( error message like leaving directory /2.6.15-23 etc..)
sudo make install
sudo make reload

```

then i run xine 
```
buddy@ubuntu:~/v4l-dvb/v4l$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/fr-Paris > ~/.xine/channels.conf

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/fr-Paris
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 474000000 0 2 0 3 1 0 0
initial transponder 498000000 0 2 0 3 1 0 0
initial transponder 522000000 0 2 0 3 1 0 0
initial transponder 562000000 0 2 0 3 1 0 0
initial transponder 586000000 0 3 0 3 1 2 0
>>> tune to: 474000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 474000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 586000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 586000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
```

**my fr-Paris is bad!!!!!!but good for another usb-card budget?????**

```
buddy@ubuntu:~/v4l-dvb/v4l$ sudo gedit /usr/share/doc/dvb-utils/examples/scan/dvb-t/fr-Paris

**i modify with +167 then, for france  **

buddy@ubuntu:~/v4l-dvb/v4l$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/fr-Paris > ~/.xine/channels.conf

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/fr-Paris
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 474167000 0 2 0 3 1 0 0
initial transponder 498167000 0 2 0 3 1 0 0
initial transponder 522167000 0 2 0 3 1 0 0
initial transponder 562167000 0 2 0 3 1 0 0
initial transponder 586167000 0 3 0 3 1 2 0
>>> tune to: 474167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
0x0002 0x0201: pmt_pid 0x0000 NTN -- Direct 8 (running)
0x0002 0x0202: pmt_pid 0x0000 NTN -- TMC (running)
0x0002 0x0203: pmt_pid 0x0000 NTN -- BFM TV (running)
0x0002 0x0204: pmt_pid 0x0000 NTN -- i>TELE (running)
0x0002 0x0205: pmt_pid 0x0000 NTN -- Europe 2 TV (running)
0x0002 0x0206: pmt_pid 0x0000 NTN -- Gulli (running)
Network Name 'r&#65533;seau num&#65533;rique terrestre fran&#65533;ais'
>>> tune to: 498167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
0x0004 0x04ff: pmt_pid 0x03f2 ATH -- (null) (running)
0x0004 0x0401: pmt_pid 0x006e MULTI4 -- M6 (running)
0x0004 0x0402: pmt_pid 0x00d2 MULTI4 -- W9 (running)
0x0004 0x0403: pmt_pid 0x0136 MULTI4 -- NT1 (running)
0x0004 0x0404: pmt_pid 0x019a MULTI4 -- PARIS PREMIERE (running, scrambled)
0x0004 0x0405: pmt_pid 0x01fe MULTI4 -- TF6 (running, scrambled)
0x0004 0x0406: pmt_pid 0x0262 MULTI4 -- AB1 (running, scrambled)
Network Name 'r&#65533;seau num&#65533;rique terrestre fran&#65533;ais'
>>> tune to: 522167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
0x0003 0x0301: pmt_pid 0x0500 CNH -- CANAL+ (running)
0x0003 0x0302: pmt_pid 0x0501 CNH -- CANAL+ CINEMA (running, scrambled)
0x0003 0x0303: pmt_pid 0x0502 CNH -- CANAL+ SPORT (running)
0x0003 0x0304: pmt_pid 0x0503 CNH -- PLANETE (running, scrambled)
0x0003 0x0305: pmt_pid 0x0504 CNH -- CANAL J (running, scrambled)
0x0003 0x03f0: pmt_pid 0x050a CNH -- (null) (running)
0x0003 0x03f1: pmt_pid 0x050b CNH -- (null) (running)
Network Name 'r&#65533;seau num&#65533;rique terrestre fran&#65533;ais'
>>> tune to: 562167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
0x0006 0x0605: pmt_pid 0x01f4 TPS Star -- TPS Star (running, scrambled)
0x0006 0x0601: pmt_pid 0x0064 TF1 -- TF1 (running, scrambled)
0x0006 0x0603: pmt_pid 0x012c LCI -- LCI (running, scrambled)
Network Name 'R&#65533;seau Num&#65533;rique Terrestre Fran&#65533;ais'
>>> tune to: 586167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_NONE:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
Network Name 'r&#65533;seau num&#65533;rique terrestre fran&#65533;ais'
0x0001 0x0101: pmt_pid 0x006e GR1 -- France 2 (running)
0x0001 0x0103: pmt_pid 0x019a GR1 -- France 4 (running)
0x0001 0x0104: pmt_pid 0x0136 GR1 -- France 5 (running)
0x0001 0x0105: pmt_pid 0x01fe GR1 -- ARTE (running)
0x0001 0x0106: pmt_pid 0x0262 GR1 -- LCP (running)
0x0001 0x0111: pmt_pid 0x00d2 Reg -- France 3 (running)
0x0001 0x01ff: pmt_pid 0x03f2 ATH -- (null) (running)
>>> tune to: -10:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: -10:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (33 services)
Done.

```

then i run xine and i have sound and video

a part of my dmesg:
```
[4295368.272000] saa7134 ALSA driver for DMA sound unloaded
[4295368.500000] Linux video capture interface: v1.00
[4295368.601000] i2c_adapter i2c-3: SMBus Quick command not supported, can't probe for chips
[4295368.601000] i2c_adapter i2c-4: SMBus Quick command not supported, can't probe for chips
[4295368.601000] i2c_adapter i2c-5: SMBus Quick command not supported, can't probe for chips
[4295368.657000] i2c_adapter i2c-3: SMBus Quick command not supported, can't probe for chips
[4295368.657000] i2c_adapter i2c-4: SMBus Quick command not supported, can't probe for chips
[4295368.657000] i2c_adapter i2c-5: SMBus Quick command not supported, can't probe for chips
[4295368.758000] saa7146: register extension 'dvb'.
[4295368.765000] saa7146: register extension 'budget dvb'.
[4295368.770000] saa7146: register extension 'budget_ci dvb'.
[4295368.775000] saa7146: register extension 'budget_av'.
[4295368.782000] usbcore: registered new driver ttusb
[4295368.787000] usbcore: registered new driver ttusb-dec
[4295368.794000] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[4295368.924000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4295368.925000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 209
[4295368.925000] saa7133[0]: found at 0000:01:09.0, rev: 208, irq: 209, latency: 32, mmio: 0xe8000000
[4295368.925000] saa7133[0]: subsystem: 1043:4862, board: ASUSTeK P7131 Dual [card=78,autodetected]
[4295368.925000] saa7133[0]: board init: gpio is 40000
[4295369.045000] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[4295369.045000] tuner-core.c: no tuner extensions loaded!
[4295369.045000] tuner-core.c: no tuner extensions loaded!
[4295369.073000] tuner 2-004b: setting tuner address to 61
[4295369.098000] tuner 2-004b: type set to tda8290+75a
[4295369.157000] saa7133[0]: i2c eeprom 00: 43 10 62 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[4295369.157000] saa7133[0]: i2c eeprom 10: 00 01 20 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[4295369.157000] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d6 ff ff ff ff
[4295369.157000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4295369.157000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 00 ff ff ff ff ff ff
[4295369.158000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4295369.158000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4295369.158000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4295371.083000] saa7133[0]: registered device video0 [v4l2]
[4295371.083000] saa7133[0]: registered device vbi0
[4295371.083000] saa7133[0]: registered device radio0
[4295371.143000] saa7134 ALSA driver for DMA sound loaded
[4295371.143000] saa7133[0]/alsa: saa7133[0] at 0xe8000000 irq 209 registered as card -1
[4295371.228000] DVB: registering new adapter (saa7133[0]).
[4295371.228000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[4295371.237000] em28xx v4l2 driver version 0.0.1 loaded
[4295371.240000] usbcore: registered new driver em28xx
[4295450.811000] tda1004x: setting up plls for 48MHz sampling clock
[4295452.764000] tda1004x: found firmware revision 29 -- ok
[4295460.213000] tda1004x: setting up plls for 48MHz sampling clock
[4295462.156000] tda1004x: found firmware revision 29 -- ok
[4295537.127000] tda1004x: setting up plls for 48MHz sampling clock
[4295539.064000] tda1004x: found firmware revision 29 -- ok
[4295651.733000] tda1004x: setting up plls for 48MHz sampling clock
[4295653.677000] tda1004x: found firmware revision 29 -- ok
[4295696.492000] tda1004x: setting up plls for 48MHz sampling clock
[4295698.431000] tda1004x: found firmware revision 29 -- ok
[4295790.971000] tda1004x: setting up plls for 48MHz sampling clock
[4295792.916000] tda1004x: found firmware revision 29 -- ok
[4296654.657000] tda1004x: setting up plls for 48MHz sampling clock
[4296656.601000] tda1004x: found firmware revision 29 &#8211; ok

```

thanks good luck

---

### Post by cblanquer on 2006-06-21
Salut Rosenbud,

I am trying to follow your steps to activate my card (same as yours).

I am not finding the firmware you used in linuxtv.org - can you give an accurate link to download it ?

THX/Merci.

---

### Post by cblanquer on 2006-06-26
Hi 
Just to complete my former post, the card worked as a DVB-T receiver with Kaffeine, no firmware has been necessary to install, the other steps are similar to those detailed by Rosebud. Image & sound are perfect.

Issues: 
[LIST]
[*]the scanned channels that were found are few, I must test a manual set-up per channel
[*]the analogue capture works as well (tvtime) but I am not able to enable the analog sound capture from the digital output (there is no analog wire from the card to the motherboard audio input), saa7134-alsa loads and defines device as "card -1" which is apparently wrong, I am still investigating.
[/LIST]

I shall post later if I have any relevant progress.

---

### Post by rosebud on 2006-06-30
hello

excuse me for my mistake, i found  firmware dvb-fe-tda10046.fw in web site of geexbox when you use their script to make a custom geexbox.

i have the same problem like you: dvb-t works, tv-time analog video works but without sound. radio doesn't work.

i am still investigating perhaps with another kernel 

bye

---

### Post by cblanquer on 2006-07-06
Hi,

Just to ease work to others searching for it, I picked the fw file mentioned before from [http://www.thadathil.net/dvb/fw/](http://www.thadathil.net/dvb/fw/)  (thanks to the owner).

Update 20070216 - this site is lately not available.

---

### Post by Jose Catre-Vandis on 2006-09-25
Thanks Rosebud

After 9 months of trying, and three clean installs later, your guide finally got my Asus P7131 Dual working in dvb-t for TV. One more nail in the coffin for XP :-)

---

### Post by aniskasa on 2006-11-26
I have a problem with this card...

I *think* the correct modules are running, but the card just doesn't apper in /dev/... I suppose there should be something like /dev/dvb but there isn't...

this is lsmod:

```
Module                  Size  Used by
saa7134_dvb            14468  0
dvb_pll                14724  1 saa7134_dvb
mt352                   6788  1 saa7134_dvb
video_buf_dvb           6660  1 saa7134_dvb
nxt200x                13188  1 saa7134_dvb
tda1004x               15108  1 saa7134_dvb
dvb_core               77736  1 video_buf_dvb
ip_conntrack_irc        6936  0
ip_conntrack_ftp        7708  0
ip_conntrack           47640  2 ip_conntrack_irc,ip_conntrack_ftp
nfnetlink               6936  1 ip_conntrack
binfmt_misc            11656  1
rfcomm                 37276  0
l2cap                  23428  5 rfcomm
capability              5128  0
commoncap               7296  1 capability
video                  16004  0
sbs                    14624  0
i2c_ec                  5248  1 sbs
button                  6800  0
battery                 9988  0
container               4608  0
ac                      5380  0
asus_acpi              15384  0
af_packet              21384  0
nls_utf8                2304  1
ntfs                  100724  1
dm_mod                 54324  3
md_mod                 76948  0
lp                     11584  0
snd_seq_dummy           3972  0
snd_seq_oss            31076  0
snd_seq_midi            8736  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                48204  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipv6                  245824  14
tsdev                   7872  0
hci_usb                16668  2
bluetooth              49892  7 rfcomm,l2cap,hci_usb
saa7134_alsa           13152  0
usbhid                 40800  0
snd_via82xx            27416  1
snd_via82xx_modem      14472  0
snd_usb_audio          72288  0
snd_usb_lib            15744  1 snd_usb_audio
snd_hwdep               9348  1 snd_usb_audio
analog                 11808  0
snd_ac97_codec         88096  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            2432  1 snd_ac97_codec
parport_pc             34544  1
parport                35144  2 lp,parport_pc
snd_pcm_oss            41760  0
snd_mixer_oss          16384  2 snd_pcm_oss
nvidia               4547668  16
gameport               14984  2 snd_via82xx,analog
rtc                    13364  0
saa7134               113504  2 saa7134_dvb,saa7134_alsa
psmouse                36872  0
snd_mpu401_uart         8320  1 snd_via82xx
floppy                 56844  0
video_buf              24964  4 saa7134_dvb,video_buf_dvb,saa7134_alsa,saa7134
compat_ioctl32          1536  1 saa7134
ir_kbd_i2c              9104  1 saa7134
snd_pcm                74504  6 saa7134_alsa,snd_via82xx,snd_via82xx_modem,snd_usb_audio,snd_ac97_codec,snd_pcm_oss
snd_timer              23044  2 snd_seq,snd_pcm
snd_rawmidi            24352  3 snd_seq_midi,snd_usb_lib,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
serio_raw               7044  0
via_agp                 9984  1
ir_common              28164  2 saa7134,ir_kbd_i2c
i2c_viapro              8724  0
via_rhine              23432  0
mii                     5760  1 via_rhine
snd_page_alloc          9992  3 snd_via82xx,snd_via82xx_modem,snd_pcm
pcspkr                  3072  0
agpgart                31664  2 nvidia,via_agp
videodev               24192  1 saa7134
v4l1_compat            13828  2 saa7134,videodev
v4l2_common            21376  2 saa7134,videodev
snd                    49536  15 snd_seq_oss,snd_seq,saa7134_alsa,snd_via82xx,snd_via82xx_modem,snd_usb_audio,snd_hwdep,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
soundcore               9952  2 snd
shpchp                 36252  0
pci_hotplug            31416  1 shpchp
i2c_core               21392  10 saa7134_dvb,dvb_pll,mt352,nxt200x,tda1004x,i2c_ec,nvidia,saa7134,ir_kbd_i2c,i2c_viapro
evdev                   9856  3
ext3                  129672  1
jbd                    56616  1 ext3
mbcache                 9092  1 ext3
ide_generic             1536  0 [permanent]
ehci_hcd               31368  0
uhci_hcd               22796  0
usbcore               122400  7 hci_usb,usbhid,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd
ide_cd                 38688  0
cdrom                  35632  1 ide_cd
ide_disk               15360  5
via82cxxx               9348  0 [permanent]
generic                 5252  0 [permanent]
sata_via               10244  0
libata                 97044  1 sata_via
scsi_mod              131436  1 libata
thermal                13960  0
processor              24620  1 thermal
fan                     5124  0
vga16fb                12300  0
vgastate                9472  1 vga16fb
aniskasa@rk3-60-1:~$ lsmod > lsmod.txt
aniskasa@rk3-60-1:~$ clear
aniskasa@rk3-60-1:~$ lsmod
Module                  Size  Used by
saa7134_dvb            14468  0
dvb_pll                14724  1 saa7134_dvb
mt352                   6788  1 saa7134_dvb
video_buf_dvb           6660  1 saa7134_dvb
nxt200x                13188  1 saa7134_dvb
tda1004x               15108  1 saa7134_dvb
dvb_core               77736  1 video_buf_dvb
ip_conntrack_irc        6936  0
ip_conntrack_ftp        7708  0
ip_conntrack           47640  2 ip_conntrack_irc,ip_conntrack_ftp
nfnetlink               6936  1 ip_conntrack
binfmt_misc            11656  1
rfcomm                 37276  0
l2cap                  23428  5 rfcomm
capability              5128  0
commoncap               7296  1 capability
video                  16004  0
sbs                    14624  0
i2c_ec                  5248  1 sbs
button                  6800  0
battery                 9988  0
container               4608  0
ac                      5380  0
asus_acpi              15384  0
af_packet              21384  0
nls_utf8                2304  1
ntfs                  100724  1
dm_mod                 54324  3
md_mod                 76948  0
lp                     11584  0
snd_seq_dummy           3972  0
snd_seq_oss            31076  0
snd_seq_midi            8736  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                48204  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipv6                  245824  14
tsdev                   7872  0
hci_usb                16668  2
bluetooth              49892  7 rfcomm,l2cap,hci_usb
saa7134_alsa           13152  0
usbhid                 40800  0
snd_via82xx            27416  1
snd_via82xx_modem      14472  0
snd_usb_audio          72288  0
snd_usb_lib            15744  1 snd_usb_audio
snd_hwdep               9348  1 snd_usb_audio
analog                 11808  0
snd_ac97_codec         88096  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            2432  1 snd_ac97_codec
parport_pc             34544  1
parport                35144  2 lp,parport_pc
snd_pcm_oss            41760  0
snd_mixer_oss          16384  2 snd_pcm_oss
nvidia               4547668  16
gameport               14984  2 snd_via82xx,analog
rtc                    13364  0
saa7134               113504  2 saa7134_dvb,saa7134_alsa
psmouse                36872  0
snd_mpu401_uart         8320  1 snd_via82xx
floppy                 56844  0
video_buf              24964  4 saa7134_dvb,video_buf_dvb,saa7134_alsa,saa7134
compat_ioctl32          1536  1 saa7134
ir_kbd_i2c              9104  1 saa7134
snd_pcm                74504  6 saa7134_alsa,snd_via82xx,snd_via82xx_modem,snd_usb_audio,snd_ac97_codec,snd_pcm_oss
snd_timer              23044  2 snd_seq,snd_pcm
snd_rawmidi            24352  3 snd_seq_midi,snd_usb_lib,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
serio_raw               7044  0
via_agp                 9984  1
ir_common              28164  2 saa7134,ir_kbd_i2c
i2c_viapro              8724  0
via_rhine              23432  0
mii                     5760  1 via_rhine
snd_page_alloc          9992  3 snd_via82xx,snd_via82xx_modem,snd_pcm
pcspkr                  3072  0
agpgart                31664  2 nvidia,via_agp
videodev               24192  1 saa7134
v4l1_compat            13828  2 saa7134,videodev
v4l2_common            21376  2 saa7134,videodev
snd                    49536  15 snd_seq_oss,snd_seq,saa7134_alsa,snd_via82xx,snd_via82xx_modem,snd_usb_audio,snd_hwdep,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
soundcore               9952  2 snd
shpchp                 36252  0
pci_hotplug            31416  1 shpchp
i2c_core               21392  10 saa7134_dvb,dvb_pll,mt352,nxt200x,tda1004x,i2c_ec,nvidia,saa7134,ir_kbd_i2c,i2c_viapro
evdev                   9856  3
ext3                  129672  1
jbd                    56616  1 ext3
mbcache                 9092  1 ext3
ide_generic             1536  0 [permanent]
ehci_hcd               31368  0
uhci_hcd               22796  0
usbcore               122400  7 hci_usb,usbhid,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd
ide_cd                 38688  0
cdrom                  35632  1 ide_cd
ide_disk               15360  5
via82cxxx               9348  0 [permanent]
generic                 5252  0 [permanent]
sata_via               10244  0
libata                 97044  1 sata_via
scsi_mod              131436  1 libata
thermal                13960  0
processor              24620  1 thermal
fan                     5124  0
vga16fb                12300  0
vgastate                9472  1 vga16fb
```

lspci gives

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:13.0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder (rev d1)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1)
```

dmesg gives:
```
0695] TCP reno registered
[   19.890830] Simple Boot Flag at 0x3a set to 0x1
[   19.891514] audit: initializing netlink socket (disabled)
[   19.891525] audit(1164560744.994:1): initialized
[   19.891639] VFS: Disk quotas dquot_6.5.1
[   19.891664] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.891716] Initializing Cryptographic API
[   19.891720] io scheduler noop registered
[   19.891726] io scheduler anticipatory registered
[   19.891731] io scheduler deadline registered
[   19.891742] io scheduler cfq registered (default)
[   19.891810] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   19.892022] isapnp: Scanning for PnP cards...
[   20.248219] isapnp: No Plug & Play device found
[   20.271999] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.272134] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.272825] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.273631] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.273746] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.273750] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.274019] PNP: No PS/2 controller found. Probing ports directly.
[   20.275552] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.275718] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.275812] mice: PS/2 mouse device common for all mice
[   20.276232] EISA: Probing bus 0 at eisa.0
[   20.276266] EISA: Detected 0 cards.
[   20.276385] TCP bic registered
[   20.276391] NET: Registered protocol family 1
[   20.276398] NET: Registered protocol family 8
[   20.276401] NET: Registered protocol family 20
[   20.276436] Using IPI Shortcut mode
[   20.276491] ACPI: (supports S0 S1 S4 S5)
[   20.276930] Freeing unused kernel memory: 284k freed
[   20.277154] Time: tsc clocksource has been installed.
[   20.606112] vga16fb: initializing
[   20.606117] vga16fb: mapped to 0xc00a0000
[   20.606166] fb0: VGA16 VGA frame buffer device
[   23.002086] SCSI subsystem initialized
[   23.006589] libata version 2.00 loaded.
[   23.008946] sata_via 0000:00:0f.0: version 2.0
[   23.008974] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 169
[   23.008992] sata_via 0000:00:0f.0: routed to hard irq line 0
[   23.009077] ata1: SATA max UDMA/133 cmd 0xD800 ctl 0xD402 bmdma 0xB400 irq 169
[   23.009113] ata2: SATA max UDMA/133 cmd 0xD000 ctl 0xB802 bmdma 0xB408 irq 169
[   23.009133] scsi0 : sata_via
[   23.209659] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   23.220166] ATA: abnormal status 0x7F on port 0xD807
[   23.220190] scsi1 : sata_via
[   23.420547] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   23.431051] ATA: abnormal status 0x7F on port 0xD007
[   23.433384] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   23.433411] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 169
[   23.433418] PCI: VIA IRQ fixup for 0000:00:0f.1, from 14 to 9
[   23.433444] VP_IDE: chipset revision 6
[   23.433447] VP_IDE: not 100% native mode: will probe irqs later
[   23.433459] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   23.433468]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:DMA, hdb:pio
[   23.433483]     ide1: BM-DMA at 0xa808-0xa80f, BIOS settings: hdc:DMA, hdd:DMA
[   23.433495] Probing IDE interface ide0...
[   23.818431] hda: ST340014A, ATA DISK drive
[   24.430594] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   24.430755] Probing IDE interface ide1...
[   24.815920] hdc: Maxtor 6Y200P0, ATA DISK drive
[   25.223715] hdd: HL-DT-ST RW/DVD GCC-4522B, ATAPI CD/DVD-ROM drive
[   25.275136] ide1 at 0x170-0x177,0x376 on irq 15
[   25.283783] hda: max request size: 512KiB
[   25.300986] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(33)
[   25.301460] hda: cache flushes supported
[   25.301513]  hda: hda1 hda2 < hda5 > hda3
[   25.346261] hdc: max request size: 512KiB
[   25.346862] hdc: 398297088 sectors (203928 MB) w/7936KiB Cache, CHS=24792/255/63, UDMA(33)
[   25.346997] hdc: cache flushes supported
[   25.347020]  hdc: hdc1 hdc2
[   25.396340] hdd: ATAPI 52X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[   25.396351] Uniform CD-ROM driver Revision: 3.20
[   25.675204] usbcore: registered new driver usbfs
[   25.675234] usbcore: registered new driver hub
[   25.676143] USB Universal Host Controller Interface driver v3.0
[   25.676207] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 177
[   25.676217] PCI: VIA IRQ fixup for 0000:00:10.0, from 0 to 1
[   25.676245] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   25.676775] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   25.676809] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000a400
[   25.676955] usb usb1: configuration #1 chosen from 1 choice
[   25.676984] hub 1-0:1.0: USB hub found
[   25.676996] hub 1-0:1.0: 2 ports detected
[   25.777664] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 177
[   25.777672] PCI: VIA IRQ fixup for 0000:00:10.1, from 0 to 1
[   25.777698] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   25.777796] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   25.777820] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000a000
[   25.778070] usb usb2: configuration #1 chosen from 1 choice
[   25.778169] hub 2-0:1.0: USB hub found
[   25.778180] hub 2-0:1.0: 2 ports detected
[   25.878511] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 177
[   25.878517] PCI: VIA IRQ fixup for 0000:00:10.2, from 0 to 1
[   25.878538] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   25.878631] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   25.878651] uhci_hcd 0000:00:10.2: irq 177, io base 0x00009800
[   25.878895] usb usb3: configuration #1 chosen from 1 choice
[   25.878992] hub 3-0:1.0: USB hub found
[   25.879004] hub 3-0:1.0: 2 ports detected
[   25.979465] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 177
[   25.979470] PCI: VIA IRQ fixup for 0000:00:10.3, from 0 to 1
[   25.979492] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   25.979591] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   25.979611] uhci_hcd 0000:00:10.3: irq 177, io base 0x00009400
[   25.979878] usb usb4: configuration #1 chosen from 1 choice
[   25.979980] hub 4-0:1.0: USB hub found
[   25.979992] hub 4-0:1.0: 2 ports detected
[   25.983242] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   26.082026] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 177
[   26.082034] PCI: VIA IRQ fixup for 0000:00:10.4, from 0 to 1
[   26.082067] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   26.082126] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   26.082203] ehci_hcd 0000:00:10.4: irq 177, io mem 0xed800000
[   26.082210] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.082325] usb usb5: configuration #1 chosen from 1 choice
[   26.082356] hub 5-0:1.0: USB hub found
[   26.082369] hub 5-0:1.0: 8 ports detected
[   26.280186] Attempting manual resume
[   26.326559] kjournald starting.  Commit interval 5 seconds
[   26.326575] EXT3-fs: mounted filesystem with ordered data mode.
[   26.496982] usb 1-1: device not accepting address 2, error -71
[   27.946252] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   28.117688] usb 1-1: configuration #1 chosen from 1 choice
[   28.326047] usb 1-2: new full speed USB device using uhci_hcd and address 5
[   28.502491] usb 1-2: configuration #1 chosen from 1 choice
[   28.710853] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   28.887349] usb 2-2: configuration #1 chosen from 1 choice
[   39.563678] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.566620] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.900738] Linux video capture interface: v2.00
[   39.934349] Linux agpgart interface v0.101 (c) Dave Jones
[   39.993083] input: PC Speaker as /class/input/input0
[   40.085941] via-rhine.c:v1.10-LK1.4.1 July-24-2006 Written by Donald Becker
[   40.086005] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 185
[   40.086135] eth0: VIA Rhine II at 0x19000, 00:11:2f:7d:76:e3, IRQ 185.
[   40.086849] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
[   40.127211] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   40.131200] agpgart: AGP aperture is 64M @ 0xf8000000
[   40.375658] Floppy drive(s): fd0 is 1.44M
[   40.394579] FDC 0 is a post-1991 82077
[   40.474408] saa7130/34: v4l2 driver version 0.2.14 loaded
[   40.474486] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 193
[   40.474498] saa7133[0]: found at 0000:00:13.0, rev: 209, irq: 193, latency: 32, mmio: 0xec800000
[   40.474505] saa7133[0]: subsystem: 1043:4876, board: UNKNOWN/GENERIC [card=0,autodetected]
[   40.474515] saa7133[0]: board init: gpio is 40000
[   40.486561] Real Time Clock Driver v1.12ac
[   40.605793] saa7133[0]: i2c eeprom 00: 43 10 76 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   40.605803] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   40.605810] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d5 ff ff ff ff
[   40.605817] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.605825] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 55 50 ff ff ff ff ff ff
[   40.605832] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.605839] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.605846] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.606101] saa7133[0]: registered device video0 [v4l2]
[   40.606134] saa7133[0]: registered device vbi0
[   40.943372] nvidia: module license 'NVIDIA' taints kernel.
[   40.948277] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[   40.948846] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[   41.172650] parport: PnPBIOS parport detected.
[   41.172711] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   41.419990] usbcore: registered new driver snd-usb-audio
[   41.434764] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   41.434778] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 209
[   41.478099] usbcore: registered new driver hiddev
[   41.480817] input: Logitech USB Receiver as /class/input/input1
[   41.480874] input: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:10.0-1
[   41.483882] input: Logitech USB Receiver as /class/input/input2
[   41.484012] input,hiddev96: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:10.0-1
[   41.484034] usbcore: registered new driver usbhid
[   41.484039] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   41.487227] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   41.534161] saa7134 ALSA driver for DMA sound loaded
[   41.534197] saa7133[0]/alsa: saa7133[0] at 0xec800000 irq 193 registered as card -1
[   41.629269] Bluetooth: Core ver 2.10
[   41.629359] NET: Registered protocol family 31
[   41.629362] Bluetooth: HCI device and connection manager initialized
[   41.629367] Bluetooth: HCI socket layer initialized
[   41.701710] Bluetooth: HCI USB driver ver 2.9
[   41.703854] usbcore: registered new driver hci_usb
[   42.185984] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   42.358536] ts: Compaq touchscreen protocol output
[   42.624357] NET: Registered protocol family 10
[   42.624467] lo: Disabled Privacy Extensions
[   42.624630] IPv6 over IPv4 tunneling driver
[   42.686952] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   42.686965] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   42.687162] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 209
[   42.687302] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   43.197934] codec_read: codec 0 is not valid [0xfe0000]
[   43.204175] codec_read: codec 0 is not valid [0xfe0000]
[   43.210371] codec_read: codec 0 is not valid [0xfe0000]
[   43.216512] codec_read: codec 0 is not valid [0xfe0000]
[   43.891447] lp0: using parport0 (interrupt-driven).
[   44.031693] Adding 1606492k swap on /dev/hda3.  Priority:-1 extents:1 across:1606492k
[   44.374024] EXT3 FS on hda1, internal journal
[   44.793740] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   44.793746] md: bitmap version 4.39
[   45.294147] device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: dm-devel@redhat.com
[   46.107626] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   46.107633] device-mapper: ioctl: error adding target to table
[   46.111055] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   46.111062] device-mapper: ioctl: error adding target to table
[   46.114482] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   46.114489] device-mapper: ioctl: error adding target to table
[   46.121749] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[   46.121756] device-mapper: ioctl: error adding target to table
[   46.125229] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[   46.125235] device-mapper: ioctl: error adding target to table
[   46.128673] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[   46.128679] device-mapper: ioctl: error adding target to table
[   46.132240] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[   46.132247] device-mapper: ioctl: error adding target to table
[   46.135610] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[   46.135617] device-mapper: ioctl: error adding target to table
[   46.139027] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[   46.139033] device-mapper: ioctl: error adding target to table
[   46.142482] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[   46.142489] device-mapper: ioctl: error adding target to table
[   46.145929] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[   46.145936] device-mapper: ioctl: error adding target to table
[   46.149401] device-mapper: table: 253:2: linear: dm-linear: Device lookup failed
[   46.149407] device-mapper: ioctl: error adding target to table
[   46.535798] NTFS driver 2.1.27 [Flags: R/O MODULE].
[   46.609340] NTFS volume version 3.1.
[   48.385055] NET: Registered protocol family 17
[   53.488945] ACPI: Power Button (FF) [PWRF]
[   53.488956] ACPI: Power Button (CM) [PWRB]
[   53.509273] Using specific hotkey driver
[   53.569966] ibm_acpi: ec object not found
[   53.597150] eth0: no IPv6 routers present
[   53.622952] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   56.945761] Capability LSM initialized
[   59.377381] Bluetooth: L2CAP ver 2.8
[   59.377387] Bluetooth: L2CAP socket layer initialized
[   59.381423] Bluetooth: RFCOMM socket layer initialized
[   59.381445] Bluetooth: RFCOMM TTY layer initialized
[   59.381447] Bluetooth: RFCOMM ver 1.8
[   62.648791] Netfilter messages via NETLINK v0.30.
[   62.679198] ip_conntrack version 2.4 (4095 buckets, 32760 max) - 192 bytes per conntrack
[   63.428525] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   63.428673] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   63.428834] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
```

---

### Post by Jose Catre-Vandis on 2006-12-30
You problem appears to lie with "Card=0"

You need to tell Ubuntu the card number and tuner number.

The card should be 78

so

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
save and close

Reboot and check dmesg, it should now be different and your card found and dvb up and running.

---

### Post by Jose Catre-Vandis on 2007-02-05
I also have FM radio working on this card, having followed the howto and instructions on this thread. I installed gnomeradio and it started tuning stations immediately without further configuration.

Plus the firmware for this card can be found here:

[ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/2007.0/non-free/release/binary/i586/dvb-firmware-frontends-20061120-1plf2007.0.noarch.rpm](ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/2007.0/non-free/release/binary/i586/dvb-firmware-frontends-20061120-1plf2007.0.noarch.rpm)

Download and unpack, copying the correct firmware to /lib/firmware

---

### Post by cblanquer on 2007-02-16
Hi,

My card is an ASUS 7131 dual & I tried today to scan the channels for DVB-T. 
In Windows I can get some of them (20 ones) working but here I am getting nothing.
(regarding the analog channels, ok in W and in Linux under tvtime)

Notice Kaffeine exploration says SNR varies but signal is always 0%.

I copied the right firmware to /lib/firmware (), then rebooted and tried again but no success.
I tried tuning manually but failed.

Here is the output of the tuning:
> carlos@mubuntu:~/.kde/share/apps/kaffeine/dvb-t$ scan -v -t 1 -p -u lista_barna > channels.conf
scanning lista_barna
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 514000000 0 2 9 3 1 3 0
initial transponder 570000000 0 2 9 3 1 3 0
initial transponder 794000000 0 2 9 3 1 3 0
initial transponder 818000000 0 2 9 3 1 3 0
initial transponder 834000000 0 2 9 3 1 3 0
initial transponder 842000000 0 2 9 3 1 3 0
initial transponder 850000000 0 2 9 3 1 3 0
initial transponder 858000000 0 2 9 3 1 3 0
>>> tune to: 514000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
>>> tuning status == 0x00
>>> tuning status == 0x01
>>> tuning status == 0x01
>>> tuning status == 0x1f
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 570000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
>>> tuning status == 0x00
>>> tuning status == 0x01
>>> tuning status == 0x01
>>> tuning status == 0x1f
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 794000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
>>> tuning status == 0x00
>>> tuning status == 0x01
>>> tuning status == 0x01
>>> tuning status == 0x1f
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 818000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
>>> tuning status == 0x00
>>> tuning status == 0x01
>>> tuning status == 0x01
>>> tuning status == 0x1f
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 834000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
>>> tune to: 834000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x01
WARNING: >>> tuning failed!!!
>>> tune to: 842000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
>>> tune to: 842000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
>>> tune to: 850000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
>>> tune to: 850000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
>>> tune to: 858000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
>>> tune to: 858000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
>>> tuning status == 0x00
WARNING: >>> tuning failed!!!
dumping lists (0 services)
Done.

Any idea ?
* I keep on trying things, maybe I post something later...

---

### Post by Jose Catre-Vandis on 2007-02-17
Hi cblanquer

Are you sure you have the updated vl4-dvb kernel stuff installed and working properly.

Run through rosebud's howto again just to be certain, and also check that you have followed my posts regarding setting the right card number for the tuner. Your dmesg should then show you that everything is up and running, before you run a scan.

You might also have to adjust your signal numbers, as rosebud did for Paris, I didn't have to do this for the UK.

Post dmesg here as this will help diagnose the issue :-)

---

### Post by boumry on 2007-05-26
Hello, 
Ihave tried several steps, that you described here and that I found on gentoo-wiki, but still with no luck
my kernel is 2.6.12-10-386

i tried due to post #15 so my files looks like this

modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
saa7134-dvb
saa7134-empress
saa6752hs
tuner
tvaudio
sg
ide-scsi
saa7134-dvb

```

modprobe.conf
```

# sets tv card for both analogue and digital
options saa7134 card=78 tuner=54

```

lsmod
```

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
nvidia               3711364  12
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
ipv6                  217408  6
sch_ingress             4100  1
cls_u32                 7300  5
sch_sfq                 5376  3
sch_cbq                16128  1
joydev                  9280  0
tsdev                   7616  0
parport_pc             31812  1
emu10k1_gp              3712  0
gameport               14472  2 emu10k1_gp
snd_emu10k1            96772  1
snd_rawmidi            22816  1 snd_emu10k1
snd_seq_device          8204  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm                78344  2 snd_emu10k1,snd_ac97_codec
snd_timer              21764  2 snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  1 snd_emu10k1
snd_hwdep               8608  1 snd_emu10k1
snd                    48644  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer,snd_hwdep
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  2 nvidia,intel_agp
dm_mod                 50364  1
ide_scsi               15748  0
sg                     33696  0
tvaudio                21668  0
saa6752hs              10004  0
saa7134_empress         9220  0
saa7134_dvb             5252  0
mt352                   6276  1 saa7134_dvb
firmware_class          9472  1 saa7134_dvb
tuner                  24488  0
evdev                   9088  0
saa7134                98772  2 saa7134_empress,saa7134_dvb
v4l2_common             5888  1 saa7134
v4l1_compat            12420  1 saa7134
soundcore               9184  2 snd,saa7134
ir_common               7428  1 saa7134
videodev                9344  2 saa7134_empress,saa7134
video_buf_dvb           6148  1 saa7134_dvb
dvb_core               72104  1 video_buf_dvb
video_buf              19844  4 saa7134_empress,saa7134_dvb,saa7134,video_buf_dvb
tda1004x               12292  1 saa7134_dvb
i2c_core               19728  7 i2c_acpi_ec,tvaudio,saa6752hs,mt352,tuner,saa7134,tda1004x
psmouse                26116  0
mousedev               10912  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  116232  3
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sd_mod                 17424  5
usbhid                 30688  0
sata_sil                9476  8
libata                 47876  1 sata_sil
scsi_mod              124872  4 ide_scsi,sg,sd_mod,libata
3c59x                  37544  0
mii                     5248  1 3c59x
uhci_hcd               28048  0
usbcore               104316  3 usbhid,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_scsi,ide_cd,ide_generic,piix
unix                   24624  533
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate              8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```


dmesg
```

[4294667.890000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294667.890000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294667.890000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294667.890000] CPU: L2 cache: 256K
[4294667.890000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[4294667.890000] CPU: Intel(R) Celeron(TM) CPU                1200MHz stepping 01
[4294667.890000] Enabling fast FPU save and restore... done.
[4294667.890000] Enabling unmasked SIMD FPU exception support... done.
[4294667.890000] Checking 'hlt' instruction... OK.
[4294667.894000] Checking for popad bug... OK.
[4294667.894000] checking if image is initramfs... it is
[4294668.609000] Freeing initrd memory: 5165k freed
[4294668.615000] ACPI: Looking for DSDT in initrd... not found!
[4294668.724000]  not found!
[4294668.737000] ENABLING IO-APIC IRQs
[4294668.737000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294668.848000] NET: Registered protocol family 16
[4294668.848000] EISA bus registered
[4294668.848000] ACPI: bus type pci registered
[4294668.860000] PCI: PCI BIOS revision 2.10 entry at 0xf9fc0, last bus=2
[4294668.860000] PCI: Using configuration type 1
[4294668.860000] mtrr: v2.0 (20020519)
[4294668.860000] ACPI: Subsystem revision 20050729
[4294668.875000] ACPI: Interpreter enabled
[4294668.875000] ACPI: Using IOAPIC for interrupt routing
[4294668.876000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.876000] PCI: Probing PCI hardware (bus 00)
[4294668.876000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.880000] Boot video device is 0000:01:00.0
[4294668.880000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.906000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.907000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[4294668.908000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294668.908000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294668.909000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[4294668.909000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294668.910000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294668.910000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294668.910000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[4294668.911000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294668.915000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.915000] pnp: PnP ACPI init
[4294668.921000] pnp: PnP ACPI: found 11 devices
[4294668.921000] PnPBIOS: Disabled by ACPI PNP
[4294668.921000] PCI: Using ACPI for IRQ routing
[4294668.921000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.939000] audit: initializing netlink socket (disabled)
[4294668.939000] audit: initialized
[4294668.939000] VFS: Disk quotas dquot_6.5.1
[4294668.939000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.939000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.939000] devfs: boot_options: 0x0
[4294668.939000] Initializing Cryptographic API
[4294668.940000] isapnp: Scanning for PnP cards...
[4294669.293000] isapnp: No Plug & Play device found
[4294669.322000] PNP: No PS/2 controller found. Probing ports directly.
[4294669.324000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.324000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.324000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.325000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.325000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.328000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.329000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.329000] io scheduler noop registered
[4294669.329000] io scheduler anticipatory registered
[4294669.329000] io scheduler deadline registered
[4294669.329000] io scheduler cfq registered
[4294669.329000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.330000] EISA: Probing bus 0 at eisa.0
[4294669.330000] Cannot allocate resource for EISA slot 4
[4294669.330000] Cannot allocate resource for EISA slot 5
[4294669.330000] EISA: Detected 0 cards.
[4294669.330000] NET: Registered protocol family 2
[4294669.340000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294669.340000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294669.341000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.342000] TCP: Hash tables configured (established 32768 bind 32768)
[4294669.342000] NET: Registered protocol family 8
[4294669.342000] NET: Registered protocol family 20
[4294669.342000] ACPI wakeup devices:
[4294669.342000] SLPB PCI0 HUB0 USB0 USB1
[4294669.342000] ACPI: (supports S0 S1 S4 S5)
[4294669.343000] Freeing unused kernel memory: 224k freed
[4294669.375000] vga16fb: initializing
[4294669.375000] vga16fb: mapped to 0xc00a0000
[4294669.528000] Console: switching to colour frame buffer device 80x30
[4294669.528000] fb0: VGA16 VGA frame buffer device
[4294670.696000] Capability LSM initialized
[4294670.719000] NET: Registered protocol family 1
[4294670.743000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.743000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.743000] ACPI: bus type ide registered
[4294670.757000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[4294670.757000] ICH2: chipset revision 17
[4294670.757000] ICH2: not 100% native mode: will probe irqs later
[4294670.757000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[4294670.757000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[4294670.757000] Probing IDE interface ide0...
[4294671.429000] hda: _NEC DVD_RW ND-3540A, ATAPI CD/DVD-ROM drive
[4294672.041000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.041000] Probing IDE interface ide1...
[4294672.560000] Probing IDE interface ide1...
[4294673.079000] Probing IDE interface ide2...
[4294673.591000] Probing IDE interface ide3...
[4294674.103000] Probing IDE interface ide4...
[4294674.615000] Probing IDE interface ide5...
[4294675.137000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294675.137000] Uniform CD-ROM driver Revision: 3.20
[4294675.729000] usbcore: registered new driver usbfs
[4294675.729000] usbcore: registered new driver hub
[4294675.731000] USB Universal Host Controller Interface driver v2.2
[4294675.731000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 19
[4294675.731000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294675.731000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801BA/BAM USB (Hub #1)
[4294675.793000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294675.793000] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000b000
[4294675.793000] hub 1-0:1.0: USB hub found
[4294675.793000] hub 1-0:1.0: 2 ports detected
[4294675.796000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 23
[4294675.796000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[4294675.796000] uhci_hcd 0000:00:1f.4: Intel Corporation 82801BA/BAM USB (Hub #2)
[4294675.858000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[4294675.858000] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000b800
[4294675.858000] hub 2-0:1.0: USB hub found
[4294675.858000] hub 2-0:1.0: 2 ports detected
[4294675.918000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294675.918000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[4294675.918000] 0000:02:01.0: 3Com PCI 3c905B Cyclone 100baseTx at 0x9000. Vers LK1.1.19
[4294675.973000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294675.987000] SCSI subsystem initialized
[4294675.990000] libata version 1.11 loaded.
[4294675.993000] sata_sil version 0.9
[4294675.993000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294675.993000] ata1: SATA max UDMA/100 cmd 0xE087C080 ctl 0xE087C08A bmdma 0xE087C000 irq 16
[4294675.993000] ata2: SATA max UDMA/100 cmd 0xE087C0C0 ctl 0xE087C0CA bmdma 0xE087C008 irq 16
[4294675.993000] ata3: SATA max UDMA/100 cmd 0xE087C280 ctl 0xE087C28A bmdma 0xE087C200 irq 16
[4294675.993000] ata4: SATA max UDMA/100 cmd 0xE087C2C0 ctl 0xE087C2CA bmdma 0xE087C208 irq 16
[4294676.348000] ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4063 85:7c69 86:3e01 87:4063 88:207f
[4294676.348000] ata1: dev 0 ATA, max UDMA/133, 398297088 sectors: lba48
[4294676.349000] ata1: dev 0 configured for UDMA/100
[4294676.349000] scsi0 : sata_sil
[4294676.550000] ata2: no device found (phy stat 00000000)
[4294676.550000] scsi1 : sata_sil
[4294676.751000] ata3: no device found (phy stat 00000000)
[4294676.751000] scsi2 : sata_sil
[4294676.952000] ata4: no device found (phy stat 00000000)
[4294676.952000] scsi3 : sata_sil
[4294676.952000]   Vendor: ATA       Model: Maxtor 6L200M0    Rev: BANC
[4294676.952000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294679.000000] usbcore: registered new driver hiddev
[4294679.017000] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop\uffff 2.10] on usb-0000:00:1f.2-2
[4294679.107000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop\uffff 2.10] on usb-0000:00:1f.2-2
[4294679.107000] usbcore: registered new driver usbhid
[4294679.107000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294679.148000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[4294679.148000] SCSI device sda: drive cache: write back
[4294679.148000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[4294679.148000] SCSI device sda: drive cache: write back
[4294679.148000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 p4
[4294679.179000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294679.914000] ACPI: CPU0 (power states: C1[C1])
[4294679.914000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294680.145000] Attempting manual resume
[4294680.145000] swsusp: Suspend partition has wrong signature?
[4294680.174000] kjournald starting.  Commit interval 5 seconds
[4294680.174000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.026000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.524000] Adding 586364k swap on /dev/sda3.  Priority:-1 extents:1
[4294685.788000] EXT3 FS on sda1, internal journal
[4294690.695000] lp: driver loaded but no devices found
[4294690.774000] mice: PS/2 mouse device common for all mice
[4294691.070000] Linux video capture interface: v1.00
[4294691.120000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4294691.130000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294691.130000] saa7133[0]: found at 0000:02:04.0, rev: 209, irq: 18, latency: 32, mmio: 0xef002000
[4294691.130000] saa7133[0]: subsystem: 1043:4876, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294691.130000] saa7133[0]: board init: gpio is 40000
[4294691.130000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4294691.131000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4294691.303000] saa7133[0]: i2c eeprom 00: 43 10 76 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[4294691.303000] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[4294691.303000] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d5 ff ff ff ff
[4294691.303000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294691.358000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[4294691.358000] tuner 0-004b: tuner: type set to tda8290+75
[4294691.496000] saa7133[0]: registered device video0 [v4l2]
[4294691.498000] saa7133[0]: registered device vbi0
[4294691.818000] tvaudio: TV audio decoder + audio/video mux driver
[4294691.818000] tvaudio: known chips: tda9840,tda9873h,tda9874h/a,tda9850,tda9855,tea6300,tea6320,tea6420,tda8425,pic16c54 (PV951),ta8874z
[4294691.855000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
[4294694.995000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294695.904000] cdrom: open failed.
[4294696.652000] kjournald starting.  Commit interval 5 seconds
[4294696.652000] EXT3 FS on sda4, internal journal
[4294696.652000] EXT3-fs: mounted filesystem with ordered data mode.
[4294696.704000] kjournald starting.  Commit interval 5 seconds
[4294696.704000] EXT3 FS on sda2, internal journal
[4294696.704000] EXT3-fs: mounted filesystem with ordered data mode.
[4294698.225000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.246000] agpgart: Detected an Intel i815 Chipset.
[4294698.285000] agpgart: AGP aperture is 64M @ 0xe8000000
[4294698.455000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294698.482000] shpchp: shpc_init : shpc_cap_offset == 0
[4294698.482000] shpchp: shpc_init : shpc_cap_offset == 0
[4294698.482000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294698.692000] hw_random: RNG not detected
[4294699.860000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294700.685000] gameport: EMU10K1 is pci0000:02:02.1/gameport0, io 0x9800, speed 1125kHz
[4294703.099000] parport: PnPBIOS parport detected.
[4294703.099000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294703.184000] lp0: using parport0 (interrupt-driven).
[4294703.546000] ts: Compaq touchscreen protocol output
[4294705.205000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294705.344000] u32 classifier
[4294705.344000]     OLD policer on
[4294705.388000] Ingress scheduler: Classifier actions prefered over netfilter
[4294707.246000] NET: Registered protocol family 10
[4294707.246000] Disabled Privacy Extensions on device c02eb280(lo)
[4294707.246000] IPv6 over IPv4 tunneling driver
[4294708.711000] ACPI: Power Button (FF) [PWRF]
[4294708.711000] ACPI: Power Button (CM) [PWRB]
[4294708.711000] ACPI: Sleep Button (CM) [SLPB]
[4294708.920000] ibm_acpi: ec object not found
[4294715.189000] nvidia: module license 'NVIDIA' taints kernel.
[4294715.227000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294715.228000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4294715.568000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294715.568000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294715.568000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294716.171000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294716.171000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294716.171000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294717.794000] eth0: no IPv6 routers present
[4294720.484000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294720.484000] apm: overridden by ACPI.
[4294721.634000] Bluetooth: Core ver 2.7
[4294721.634000] NET: Registered protocol family 31
[4294721.634000] Bluetooth: HCI device and connection manager initialized
[4294721.634000] Bluetooth: HCI socket layer initialized
[4294721.740000] Bluetooth: L2CAP ver 2.7
[4294721.740000] Bluetooth: L2CAP socket layer initialized
[4294721.826000] Bluetooth: RFCOMM ver 1.5
[4294721.826000] Bluetooth: RFCOMM socket layer initialized
[4294721.826000] Bluetooth: RFCOMM TTY layer initialized

```

lspci
```

[/0000:02:04.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d1)

```


if I tried kaffein
```

boumry@poc3:~$ kaffeine
kbuildsycoca running...
DVB 0 : No such file or directory
DVB 1 : No such file or directory
DVB 2 : No such file or directory
DVB 3 : No such file or directory

```

any ideas what to do?

---

### Post by Jose Catre-Vandis on 2007-07-26
> **boumry said:**
> Hello, 
Ihave tried several steps, that you described here and that I found on gentoo-wiki, but still with no luck
my kernel is 2.6.12-10-386

i tried due to post #15 so my files looks like this

modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
saa7134-dvb
saa7134-empress
saa6752hs
tuner
tvaudio
sg
ide-scsi
saa7134-dvb

```

modprobe.conf
```

# sets tv card for both analogue and digital
options saa7134 card=78 tuner=54

```

lsmod
```

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
nvidia               3711364  12
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
ipv6                  217408  6
sch_ingress             4100  1
cls_u32                 7300  5
sch_sfq                 5376  3
sch_cbq                16128  1
joydev                  9280  0
tsdev                   7616  0
parport_pc             31812  1
emu10k1_gp              3712  0
gameport               14472  2 emu10k1_gp
snd_emu10k1            96772  1
snd_rawmidi            22816  1 snd_emu10k1
snd_seq_device          8204  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm                78344  2 snd_emu10k1,snd_ac97_codec
snd_timer              21764  2 snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  1 snd_emu10k1
snd_hwdep               8608  1 snd_emu10k1
snd                    48644  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer,snd_hwdep
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  2 nvidia,intel_agp
dm_mod                 50364  1
ide_scsi               15748  0
sg                     33696  0
tvaudio                21668  0
saa6752hs              10004  0
saa7134_empress         9220  0
saa7134_dvb             5252  0
mt352                   6276  1 saa7134_dvb
firmware_class          9472  1 saa7134_dvb
tuner                  24488  0
evdev                   9088  0
saa7134                98772  2 saa7134_empress,saa7134_dvb
v4l2_common             5888  1 saa7134
v4l1_compat            12420  1 saa7134
soundcore               9184  2 snd,saa7134
ir_common               7428  1 saa7134
videodev                9344  2 saa7134_empress,saa7134
video_buf_dvb           6148  1 saa7134_dvb
dvb_core               72104  1 video_buf_dvb
video_buf              19844  4 saa7134_empress,saa7134_dvb,saa7134,video_buf_dvb
tda1004x               12292  1 saa7134_dvb
i2c_core               19728  7 i2c_acpi_ec,tvaudio,saa6752hs,mt352,tuner,saa7134,tda1004x
psmouse                26116  0
mousedev               10912  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  116232  3
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sd_mod                 17424  5
usbhid                 30688  0
sata_sil                9476  8
libata                 47876  1 sata_sil
scsi_mod              124872  4 ide_scsi,sg,sd_mod,libata
3c59x                  37544  0
mii                     5248  1 3c59x
uhci_hcd               28048  0
usbcore               104316  3 usbhid,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_scsi,ide_cd,ide_generic,piix
unix                   24624  533
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate              8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```


dmesg
```

[4294667.890000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294667.890000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[4294667.890000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294667.890000] CPU: L2 cache: 256K
[4294667.890000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[4294667.890000] CPU: Intel(R) Celeron(TM) CPU                1200MHz stepping 01
[4294667.890000] Enabling fast FPU save and restore... done.
[4294667.890000] Enabling unmasked SIMD FPU exception support... done.
[4294667.890000] Checking 'hlt' instruction... OK.
[4294667.894000] Checking for popad bug... OK.
[4294667.894000] checking if image is initramfs... it is
[4294668.609000] Freeing initrd memory: 5165k freed
[4294668.615000] ACPI: Looking for DSDT in initrd... not found!
[4294668.724000]  not found!
[4294668.737000] ENABLING IO-APIC IRQs
[4294668.737000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294668.848000] NET: Registered protocol family 16
[4294668.848000] EISA bus registered
[4294668.848000] ACPI: bus type pci registered
[4294668.860000] PCI: PCI BIOS revision 2.10 entry at 0xf9fc0, last bus=2
[4294668.860000] PCI: Using configuration type 1
[4294668.860000] mtrr: v2.0 (20020519)
[4294668.860000] ACPI: Subsystem revision 20050729
[4294668.875000] ACPI: Interpreter enabled
[4294668.875000] ACPI: Using IOAPIC for interrupt routing
[4294668.876000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.876000] PCI: Probing PCI hardware (bus 00)
[4294668.876000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.880000] Boot video device is 0000:01:00.0
[4294668.880000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.906000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.907000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[4294668.908000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294668.908000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294668.909000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[4294668.909000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294668.910000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294668.910000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294668.910000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[4294668.911000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294668.915000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.915000] pnp: PnP ACPI init
[4294668.921000] pnp: PnP ACPI: found 11 devices
[4294668.921000] PnPBIOS: Disabled by ACPI PNP
[4294668.921000] PCI: Using ACPI for IRQ routing
[4294668.921000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.939000] audit: initializing netlink socket (disabled)
[4294668.939000] audit: initialized
[4294668.939000] VFS: Disk quotas dquot_6.5.1
[4294668.939000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.939000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.939000] devfs: boot_options: 0x0
[4294668.939000] Initializing Cryptographic API
[4294668.940000] isapnp: Scanning for PnP cards...
[4294669.293000] isapnp: No Plug & Play device found
[4294669.322000] PNP: No PS/2 controller found. Probing ports directly.
[4294669.324000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.324000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.324000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.325000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.325000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.328000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.329000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.329000] io scheduler noop registered
[4294669.329000] io scheduler anticipatory registered
[4294669.329000] io scheduler deadline registered
[4294669.329000] io scheduler cfq registered
[4294669.329000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.330000] EISA: Probing bus 0 at eisa.0
[4294669.330000] Cannot allocate resource for EISA slot 4
[4294669.330000] Cannot allocate resource for EISA slot 5
[4294669.330000] EISA: Detected 0 cards.
[4294669.330000] NET: Registered protocol family 2
[4294669.340000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294669.340000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294669.341000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.342000] TCP: Hash tables configured (established 32768 bind 32768)
[4294669.342000] NET: Registered protocol family 8
[4294669.342000] NET: Registered protocol family 20
[4294669.342000] ACPI wakeup devices:
[4294669.342000] SLPB PCI0 HUB0 USB0 USB1
[4294669.342000] ACPI: (supports S0 S1 S4 S5)
[4294669.343000] Freeing unused kernel memory: 224k freed
[4294669.375000] vga16fb: initializing
[4294669.375000] vga16fb: mapped to 0xc00a0000
[4294669.528000] Console: switching to colour frame buffer device 80x30
[4294669.528000] fb0: VGA16 VGA frame buffer device
[4294670.696000] Capability LSM initialized
[4294670.719000] NET: Registered protocol family 1
[4294670.743000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.743000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.743000] ACPI: bus type ide registered
[4294670.757000] ICH2: IDE controller at PCI slot 0000:00:1f.1
[4294670.757000] ICH2: chipset revision 17
[4294670.757000] ICH2: not 100% native mode: will probe irqs later
[4294670.757000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[4294670.757000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[4294670.757000] Probing IDE interface ide0...
[4294671.429000] hda: _NEC DVD_RW ND-3540A, ATAPI CD/DVD-ROM drive
[4294672.041000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.041000] Probing IDE interface ide1...
[4294672.560000] Probing IDE interface ide1...
[4294673.079000] Probing IDE interface ide2...
[4294673.591000] Probing IDE interface ide3...
[4294674.103000] Probing IDE interface ide4...
[4294674.615000] Probing IDE interface ide5...
[4294675.137000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294675.137000] Uniform CD-ROM driver Revision: 3.20
[4294675.729000] usbcore: registered new driver usbfs
[4294675.729000] usbcore: registered new driver hub
[4294675.731000] USB Universal Host Controller Interface driver v2.2
[4294675.731000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 19
[4294675.731000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294675.731000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801BA/BAM USB (Hub #1)
[4294675.793000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294675.793000] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000b000
[4294675.793000] hub 1-0:1.0: USB hub found
[4294675.793000] hub 1-0:1.0: 2 ports detected
[4294675.796000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 23
[4294675.796000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[4294675.796000] uhci_hcd 0000:00:1f.4: Intel Corporation 82801BA/BAM USB (Hub #2)
[4294675.858000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[4294675.858000] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000b800
[4294675.858000] hub 2-0:1.0: USB hub found
[4294675.858000] hub 2-0:1.0: 2 ports detected
[4294675.918000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294675.918000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[4294675.918000] 0000:02:01.0: 3Com PCI 3c905B Cyclone 100baseTx at 0x9000. Vers LK1.1.19
[4294675.973000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294675.987000] SCSI subsystem initialized
[4294675.990000] libata version 1.11 loaded.
[4294675.993000] sata_sil version 0.9
[4294675.993000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294675.993000] ata1: SATA max UDMA/100 cmd 0xE087C080 ctl 0xE087C08A bmdma 0xE087C000 irq 16
[4294675.993000] ata2: SATA max UDMA/100 cmd 0xE087C0C0 ctl 0xE087C0CA bmdma 0xE087C008 irq 16
[4294675.993000] ata3: SATA max UDMA/100 cmd 0xE087C280 ctl 0xE087C28A bmdma 0xE087C200 irq 16
[4294675.993000] ata4: SATA max UDMA/100 cmd 0xE087C2C0 ctl 0xE087C2CA bmdma 0xE087C208 irq 16
[4294676.348000] ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4063 85:7c69 86:3e01 87:4063 88:207f
[4294676.348000] ata1: dev 0 ATA, max UDMA/133, 398297088 sectors: lba48
[4294676.349000] ata1: dev 0 configured for UDMA/100
[4294676.349000] scsi0 : sata_sil
[4294676.550000] ata2: no device found (phy stat 00000000)
[4294676.550000] scsi1 : sata_sil
[4294676.751000] ata3: no device found (phy stat 00000000)
[4294676.751000] scsi2 : sata_sil
[4294676.952000] ata4: no device found (phy stat 00000000)
[4294676.952000] scsi3 : sata_sil
[4294676.952000]   Vendor: ATA       Model: Maxtor 6L200M0    Rev: BANC
[4294676.952000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294679.000000] usbcore: registered new driver hiddev
[4294679.017000] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop\uffff 2.10] on usb-0000:00:1f.2-2
[4294679.107000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop\uffff 2.10] on usb-0000:00:1f.2-2
[4294679.107000] usbcore: registered new driver usbhid
[4294679.107000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294679.148000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[4294679.148000] SCSI device sda: drive cache: write back
[4294679.148000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[4294679.148000] SCSI device sda: drive cache: write back
[4294679.148000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 p4
[4294679.179000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294679.914000] ACPI: CPU0 (power states: C1[C1])
[4294679.914000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294680.145000] Attempting manual resume
[4294680.145000] swsusp: Suspend partition has wrong signature?
[4294680.174000] kjournald starting.  Commit interval 5 seconds
[4294680.174000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.026000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294685.524000] Adding 586364k swap on /dev/sda3.  Priority:-1 extents:1
[4294685.788000] EXT3 FS on sda1, internal journal
[4294690.695000] lp: driver loaded but no devices found
[4294690.774000] mice: PS/2 mouse device common for all mice
[4294691.070000] Linux video capture interface: v1.00
[4294691.120000] saa7130/34: v4l2 driver version 0.2.12 loaded
[4294691.130000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294691.130000] saa7133[0]: found at 0000:02:04.0, rev: 209, irq: 18, latency: 32, mmio: 0xef002000
[4294691.130000] saa7133[0]: subsystem: 1043:4876, board: UNKNOWN/GENERIC [card=0,autodetected]
[4294691.130000] saa7133[0]: board init: gpio is 40000
[4294691.130000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4294691.131000] saa7133[0]: dsp access wait timeout [bit=WRR]
[4294691.303000] saa7133[0]: i2c eeprom 00: 43 10 76 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[4294691.303000] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[4294691.303000] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d5 ff ff ff ff
[4294691.303000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4294691.358000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[4294691.358000] tuner 0-004b: tuner: type set to tda8290+75
[4294691.496000] saa7133[0]: registered device video0 [v4l2]
[4294691.498000] saa7133[0]: registered device vbi0
[4294691.818000] tvaudio: TV audio decoder + audio/video mux driver
[4294691.818000] tvaudio: known chips: tda9840,tda9873h,tda9874h/a,tda9850,tda9855,tea6300,tea6320,tea6420,tda8425,pic16c54 (PV951),ta8874z
[4294691.855000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
[4294694.995000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294695.904000] cdrom: open failed.
[4294696.652000] kjournald starting.  Commit interval 5 seconds
[4294696.652000] EXT3 FS on sda4, internal journal
[4294696.652000] EXT3-fs: mounted filesystem with ordered data mode.
[4294696.704000] kjournald starting.  Commit interval 5 seconds
[4294696.704000] EXT3 FS on sda2, internal journal
[4294696.704000] EXT3-fs: mounted filesystem with ordered data mode.
[4294698.225000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.246000] agpgart: Detected an Intel i815 Chipset.
[4294698.285000] agpgart: AGP aperture is 64M @ 0xe8000000
[4294698.455000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294698.482000] shpchp: shpc_init : shpc_cap_offset == 0
[4294698.482000] shpchp: shpc_init : shpc_cap_offset == 0
[4294698.482000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294698.692000] hw_random: RNG not detected
[4294699.860000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294700.685000] gameport: EMU10K1 is pci0000:02:02.1/gameport0, io 0x9800, speed 1125kHz
[4294703.099000] parport: PnPBIOS parport detected.
[4294703.099000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294703.184000] lp0: using parport0 (interrupt-driven).
[4294703.546000] ts: Compaq touchscreen protocol output
[4294705.205000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294705.344000] u32 classifier
[4294705.344000]     OLD policer on
[4294705.388000] Ingress scheduler: Classifier actions prefered over netfilter
[4294707.246000] NET: Registered protocol family 10
[4294707.246000] Disabled Privacy Extensions on device c02eb280(lo)
[4294707.246000] IPv6 over IPv4 tunneling driver
[4294708.711000] ACPI: Power Button (FF) [PWRF]
[4294708.711000] ACPI: Power Button (CM) [PWRB]
[4294708.711000] ACPI: Sleep Button (CM) [SLPB]
[4294708.920000] ibm_acpi: ec object not found
[4294715.189000] nvidia: module license 'NVIDIA' taints kernel.
[4294715.227000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294715.228000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4294715.568000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294715.568000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294715.568000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294716.171000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294716.171000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4294716.171000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[4294717.794000] eth0: no IPv6 routers present
[4294720.484000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294720.484000] apm: overridden by ACPI.
[4294721.634000] Bluetooth: Core ver 2.7
[4294721.634000] NET: Registered protocol family 31
[4294721.634000] Bluetooth: HCI device and connection manager initialized
[4294721.634000] Bluetooth: HCI socket layer initialized
[4294721.740000] Bluetooth: L2CAP ver 2.7
[4294721.740000] Bluetooth: L2CAP socket layer initialized
[4294721.826000] Bluetooth: RFCOMM ver 1.5
[4294721.826000] Bluetooth: RFCOMM socket layer initialized
[4294721.826000] Bluetooth: RFCOMM TTY layer initialized

```

lspci
```

[/0000:02:04.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d1)

```


if I tried kaffein
```

boumry@poc3:~$ kaffeine
kbuildsycoca running...
DVB 0 : No such file or directory
DVB 1 : No such file or directory
DVB 2 : No such file or directory
DVB 3 : No such file or directory

```

any ideas what to do?

What does 
```
sudo lspci -v
``` give you?
Are you sure you have an ASUS P7131 DUAL ?
Mine gives this:
```
 01:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 4857
        Flags: bus master, medium devsel, latency 32, IRQ 201
        Memory at e8000000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [40] Power Management version 2
```

For some reason your card is not being detected, even with the modprobe.conf options. Try this..
```
sudo rmmod saa7134-dvb
sudo rmmod saa7134-alsa
sudo rmmod saa7134

then

sudo modprobe saa7134 card=78 tuner=54
(you should get a short delay before the prompt returns)

sudo modprobe saa7134-dvb
```

then
```
dmesg
```
and the tail should look like this:
> [17180798.080000] saa7133[0]: subsystem: 1043:4857, board: ASUSTeK P7131 Dual [card=78,insmod option]
[17180798.080000] saa7133[0]: board init: gpio is 0
[17180798.260000] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[17180798.312000] tuner 2-004b: setting tuner address to 61
[17180798.352000] tuner 2-004b: type set to tda8290+75a
[17180798.448000] saa7133[0]: i2c eeprom 00: 43 10 57 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17180798.448000] saa7133[0]: i2c eeprom 10: 00 01 20 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[17180798.448000] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 cb ff ff ff ff
[17180798.448000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180798.448000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 00 ff ff ff ff ff ff
[17180798.448000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180798.448000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180798.448000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180800.876000] saa7133[0]: registered device video0 [v4l2]
[17180800.876000] saa7133[0]: registered device vbi0
[17180800.876000] saa7133[0]: registered device radio0
[17180801.000000] saa7134 ALSA driver for DMA sound loaded
[17180801.000000] saa7133[0]/alsa: saa7133[0] at 0xe8000000 irq 201 registered as card -1
[17180807.436000] DVB: registering new adapter (saa7133[0]).
[17180807.436000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...


---

### Post by sharke on 2007-08-26
I have this card tv works fine with kaffeine shows all local channels. My problem is gnomeradio i cannot set mixer to use shows stations has volume but no sound.

Regards
Sharke

---

### Post by Jose Catre-Vandis on 2007-08-27
Is GnomeRadio showing that it is tuning into stations (i.e. you see "Stereo" with green lines). If so this would most likley be a sound mixer problem. Have a play with settings in your mixer (Right click on sound icon in tray, choose "Open Volume Control") Do this while Gnomeradio is running. Also check in Gnomeradio settings as to which volume control is selected.

If you do not get "Stereo" with green lines, try editing your device from /dev/radio to dev/radio0. (You can check which device is enabled by using dmesg) The device appears to change between Edgy and Fiesty!

---

### Post by Jose Catre-Vandis on 2007-08-27
Please also see my other thread on problems with the later kernel.

[http://ubuntuforums.org/showthread.php?t=529767](http://ubuntuforums.org/showthread.php?t=529767)

I understand that the v4l-dvb kernel was changed to sort out one lot of user problems, which created a second set of issues :)

---

### Post by Jose Catre-Vandis on 2007-10-23
Hey, Gutsy sees this card by default now for an out of the box experience :)

I'm "out of my box"  :)

---

### Post by halitech on 2008-02-12
> **Jose Catre-Vandis said:**
> You problem appears to lie with "Card=0"

You need to tell Ubuntu the card number and tuner number.

The card should be 78

so

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
save and close

Reboot and check dmesg, it should now be different and your card found and dvb up and running.

Hey

I've had this card for a few months now and never been able to get it to work. I followed these instructions and rebooted and the card is now working on Television and Composite input perfectly. Radio doesn't seem to but I'm not worries about that.

Thanks Jose :)

(edit - radio works fine when the antenna is hooked up :( )

---

### Post by bve on 2008-06-02
So do any of you happen to have the remote working with lirc too? I am unable to get lirc to function with the p7131, on hardy.

thanks in advance

---

### Post by mazetas on 2008-07-06
Hey I have used several programs for tv but I have no sound. I use ASUS MyCinema P7131 hybrid and the 8.04 Ubuntu. 
The same sound problem appears in radio. From XP it works but you know, I don't want to betray my linux.

I tried with sox command to change the sound channel but no result.
any suggestions?

---

