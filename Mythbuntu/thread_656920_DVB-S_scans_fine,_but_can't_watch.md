---
title: "DVB-S scans fine, but can't watch"
date: 2008-01-03
forum: Mythbuntu
---

### Post by huntercj on 2008-01-03
I can watch analogue TV fine, but not satellite. I'm using a Hauppauge Nova-S Plus. After a lot of fiddling I can get it to scan the channels fine in MythSetup, but get no EPG and cannot view. I have tried command line and Kaffeine with the same results, I can scan the channels, but I can't watch.

I have added v4l-dvb and modprobed cx88-dvb. This changed the dmesg output, but still the same results. Here is some of the relevant output.

[   45.544982] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   45.545425] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   45.545434] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   45.545465] cx88[0]: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37,autodetected]
[   45.545467] cx88[0]: TV tuner type 4, Radio tuner type -1
[   45.557193] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   45.627834] lirc_dev: IR Remote Control driver registered, at major 61 
[   45.701884] tveeprom 2-0050: Hauppauge model 92001, rev C1B1, serial# 1852626
[   45.701889] tveeprom 2-0050: MAC address is 00-0D-FE-1C-44-D2
[   45.701891] tveeprom 2-0050: tuner model is Conexant_CX24109 (idx 111, type 4)
[   45.701894] tveeprom 2-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   45.701896] tveeprom 2-0050: audio processor is CX883 (idx 32)
[   45.701898] tveeprom 2-0050: decoder processor is CX883 (idx 22)
[   45.701900] tveeprom 2-0050: has no radio, has IR receiver, has no IR transmitter
[   45.701902] cx88[0]: hauppauge eeprom: model=92001
[   45.701968] input: cx88 IR (Hauppauge Nova-S-Plus  as /class/input/input4
[   45.701991] cx88[0]/0: found at 0000:01:07.0, rev: 5, irq: 17, latency: 32, mmio: 0xe9000000
[   45.702035] cx88[0]/0: registered device video0 [v4l2]
[   45.702050] cx88[0]/0: registered device vbi0
[   45.703464] cx88[0]/2: cx2388x 8802 Driver Manager
[   45.703483] ACPI: PCI Interrupt 0000:01:07.2[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   45.703491] cx88[0]/2: found at 0000:01:07.2, rev: 5, irq: 17, latency: 32, mmio: 0xeb000000
[   45.707226] saa7130/34: v4l2 driver version 0.2.14 loaded
[   45.707687] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   45.707726] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   45.707733] saa7133[0]: found at 0000:01:08.0, rev: 209, irq: 18, latency: 32, mmio: 0xedffe000
[   45.707738] saa7133[0]: subsystem: 5168:5214, board: LifeView FlyTV Platinum FM / Gold [card=54,a

and...

[   45.989356] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   45.989360] cx88/2: registering cx8802 driver, type: dvb access: shared
[   45.989363] cx88[0]/2: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37]
[   45.989366] cx88[0]/2: cx2388x based DVB/ATSC card
[   46.134264] tuner' 3-004b: chip found @ 0x96 (saa7133[0])
[   46.214110] tda8290 3-004b: setting tuner address to 61
[   46.277995] tda8290 3-004b: type set to tda8290+75a
[   46.293395] DVB: registering new adapter (cx88[0])
[   46.293399] DVB: registering frontend 0 (Conexant CX24123/CX24109)...

I'm at a bit of a loss now. Channel scanning is working, SNR is >90%, BER is 0, but no picture.

I kind of suspect the NVidia display driver or X config, but Analogue TV is fine, so is there a subtle difference between how analogue and DVB stream?

I have seen mention of problems with horizontal polarisation (which all NZ channels on Optus D1 are), but why would I be able to scan and yet not watch?

Any help gratefully received.

Cheers,

Colin.

---

### Post by huntercj on 2008-01-03
Some further info,

erik@cottage:~$ dvbtune -f 1183000 -s 22500 -p h -m 2
Using DVB card "Conexant CX24123/CX24109"
tuning DVB-S to L-Band:0, Pol:H Srate=22500000, 22kHz=off
ERROR setting tone
: Invalid argument
polling....
Getting frontend event
FE_STATUS:
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL
polling....
Getting frontend event
FE_STATUS: FE_HAS_SIGNAL FE_HAS_LOCK FE_HAS_CARRIER FE_HAS_VITERBI FE_HAS_SYNC
Bit error rate: 0
Signal strength: 60416
SNR: 65382
FE_STATUS: FE_HAS_SIGNAL FE_HAS_LOCK FE_HAS_CARRIER FE_HAS_VITERBI FE_HAS_SYNC
FE READ UNCORRECTED BLOCKS: : Operation not supported
Signal=60416, Verror=0, SNR=65387dB, BlockErrors=0, (S|L|C|V|SY|)
FE READ UNCORRECTED BLOCKS: : Operation not supported
Signal=60416, Verror=0, SNR=65382dB, BlockErrors=0, (S|L|C|V|SY|)
FE READ UNCORRECTED BLOCKS: : Operation not supported
Signal=60416, Verror=0, SNR=65425dB, BlockErrors=0, (S|L|C|V|SY|)
FE READ UNCORRECTED BLOCKS: : Operation not supported
Signal=60416, Verror=0, SNR=65464dB, BlockErrors=0, (S|L|C|V|SY|)

and...

erik@cottage:~$ scan -c -U
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
0x0000 0x0401: pmt_pid 0x010a Maori Television Service -- Maori TV (running)
0x0000 0x040b: pmt_pid 0x010d Television New Zealand -- TV ONE (running)
0x0000 0x040c: pmt_pid 0x010e Television New Zealand -- TV2 (running)
0x0000 0x040d: pmt_pid 0x010f TVNZ -- Reserved 6 (not running)
0x0000 0x040e: pmt_pid 0x0110 TVNZ -- Reserved 7 (not running)
0x0000 0x076d: pmt_pid 0x0111 TVNZ -- Reserved 5 (not running)
0x0000 0x076e: pmt_pid 0x010c TVNZ -- Reserved 4 (not running)
0x0000 0x076f: pmt_pid 0x0112 Television New Zealand -- TVNZ SPORT EXTRA (running)
0x0000 0x0770: pmt_pid 0x010b Television New Zealand -- TVNZ 6 (running)
0x0000 0x6590: pmt_pid 0x0000 Television New Zealand -- 27M SSU (running)
0x0000 0x6640: pmt_pid 0x0000 Television New Zealand -- SSU-ZW (running)
dumping lists (11 services)
Maori TV                 (0x0401) 01: PCR == V   V 0x0202 A 0x028c      
TV ONE                   (0x040b) 01: PCR == V   V 0x0203 A 0x028d       TT 0x0243
TV2                      (0x040c) 01: PCR == V   V 0x0204 A 0x028e       TT 0x0244
Reserved 6               (0x040d) 01: PCR == V   V 0x0205 A 0x028f       TT 0x0243
Reserved 7               (0x040e) 01: PCR == V   V 0x0206 A 0x0290       TT 0x0243
Reserved 5               (0x076d) 01: PCR == V   V 0x0201 A 0x028b      
Reserved 4               (0x076e) 01: PCR == V   V 0x0207 A 0x0291      
TVNZ SPORT EXTRA         (0x076f) 01: PCR == V   V 0x0208 A 0x0292      
TVNZ 6                   (0x0770) 01: PCR == V   V 0x0200 A 0x028a       TT 0x0245
27M SSU                  (0x6590) 0c:                    
SSU-ZW                   (0x6640) 0c:                    
Done.

All of this information looks good to my less than expert eyes.

Cheers,

Colin.

---

### Post by huntercj on 2008-01-04
OK, I can now watch DVB-S in Kaffeine. I had to change the nVidia GeForce 6200 LE resolution from 1024 x 768 to 800 x 600. Not sure if it was the resolution or the refresh rate, but it solved the problem.

However, still no joy with Mythbuntu. It still shows the MythTV graphic at the bottom of the screen which states that the signal is >90%. However, it reports a very low S/N which I know is wrong as dvbtune reports a very high SNR and Kaffeine reports a high SNR during channel scanning. Clearly Myth is not correctly using the DVB-S driver. I'll check the config files, but any help would be gratefully received.

I've also attached an image of the Myth 'Watch TV' screen illustrating what's described above. In addition I get no EPG, which I do through Kaffeine.

Cheers,

Colin.

---

### Post by huntercj on 2008-01-04
Bugger it!! Just rebooted and now Kaffeine is back to showing a crappy jumbled green screen again. That's enough for today - back to where i started...

---

