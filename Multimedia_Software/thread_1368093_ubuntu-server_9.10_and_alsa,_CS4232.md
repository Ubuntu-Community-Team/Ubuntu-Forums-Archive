---
title: "ubuntu-server 9.10 and alsa, CS4232"
date: 2009-12-30
forum: Multimedia Software
---

### Post by e-San on 2009-12-30
Hi!

I am sick today, so it is possible i will write something... stupid.

I have very old laptop HP Ominbook 5000c:
```
Pentium I 90MHz
64 MB ram
815 MB Hdd
```
and beacose it is not high power consuming computer i decided to make him my musik box. Beacose of small disk i decided to put music on mylocal server and mount it as ftp source. Anyway nevermind.

First of all i am trying to set audio on it.
I had to recompile kernel beacose i first wanted to connect to it via ssh. Setting PCMCIA Xircom is done by now but sound does not work.

Drivers are compiled into kernel. And looks like working:

```
san@ubuntu:~$ lspnp
[...]
01:01.00 CSC0000 Crystal PnP audio system CODEC
01:01.01 CSC0001 Crystal PnP audio system joystick
01:01.02 CSC0002 Crystal PnP audio system control registers
01:01.03 CSC0003 Crystal PnP audio system MPU-401 compatible

san@ubuntu:~$ lspnp 01:01.03
01:01.03 CSC0003 Crystal PnP audio system MPU-401 compatible
san@ubuntu:~$ lspnp -vv 01:01.03
01:01.03 CSC0003 Crystal PnP audio system MPU-401 compatible
    state = active
    allocated resources:
	irq 9
	io 0x330-0x331
    possible resources:
	Dependent: 00 - Priority preferred
	  irq 2/9 High-Edge
	  port 0x330-0x330, align 0x0, size 0x2, 10-bit address decoding
	Dependent: 01 - Priority acceptable
	  irq 5,7,2/9,15 High-Edge
	  port 0x100-0x3f8, align 0x7, size 0x2, 10-bit address decoding
    compatible devices:
	PNPb006 MPU401 compatible 
san@ubuntu:~$ lspnp -vv 01:01.00
01:01.00 CSC0000 Crystal PnP audio system CODEC
    state = active
    allocated resources:
	dma 1
	dma 3
	irq 5
	io 0x534-0x537
	io 0x388-0x38b
	io 0x220-0x22f
    possible resources:
	Dependent: 00 - Priority preferred
	  dma 1 8-bit byte-count compatible
	  dma 0,3 8-bit byte-count compatible
	  irq 5 High-Edge
	  port 0x534-0x534, align 0x3, size 0x4, 16-bit address decoding
	  port 0x388-0x388, align 0x0, size 0x4, 10-bit address decoding
	  port 0x220-0x220, align 0x0, size 0x10, 10-bit address decoding
	Dependent: 01 - Priority acceptable
	  dma 0,1,3 8-bit byte-count compatible
	  irq 5,7,2/9,15 High-Edge
	  port 0x534-0x534, align 0x3, size 0x4, 16-bit address decoding
	  port 0x388-0x388, align 0x0, size 0x4, 10-bit address decoding
	  port 0x220-0x220, align 0x0, size 0x10, 10-bit address decoding
    compatible devices:
	PNPb007 Microsoft Windows Sound System-compatible sound device
	PNPb020 Yamaha OPL3-compatible FM synthesizer device
	PNPb002 Sound Blaster Pro sound device
san@ubuntu:/proc/asound$ cat cards
 0 [CS4232         ]: CS4232 - CS4232
                      CS4232 at 0x534, irq 5, dma 1&3
san@ubuntu:/proc/asound$ dmesg
[...]
[    0.754324] isapnp: Scanning for PnP cards...
[    0.859117]  01:01: card 'CS4232'
[    0.859427] isapnp: 1 Plug & Play card detected total
[...]
[    2.969879] Advanced Linux Sound Architecture Driver Version 1.0.20.
[    2.982288] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    3.028588] cs423x-pnpbios 01:01.00: activated
[    3.031410] cs423x-pnpbios 01:01.00: disabled
[    3.031843] cs423x-pnpbios: probe of 01:01.00 failed with error -2
[    3.037839] cs4232_isapnp 01:01.00: activated
[    3.038193] isapnp WSS: wss port=0x534, fm port=0x388, sb port=0x220
[    3.038527] isapnp WSS: irq=5, dma1=1, dma2=3
[    3.041527] cs4232_isapnp 01:01.02: activated
[    3.041850] isapnp CTRL: control port=0x538
[    3.045293] cs4232_isapnp 01:01.03: activated
[    3.045634] isapnp MPU: port=0x330, irq=9
[    3.046203] codec out - reg 0xc = 0x40
[    3.046504] wss: port = 0x534, id = 0xa
[    3.046775] CS4231: VERSION (I25) = 0xa2
[    3.047068] codec out - reg 0x0 = 0x0
[    3.047334] codec out - reg 0x1 = 0x0
[    3.047600] codec out - reg 0x2 = 0x9f
[    3.047868] codec out - reg 0x3 = 0x9f
[    3.048136] codec out - reg 0x4 = 0x9f
[    3.048401] codec out - reg 0x5 = 0x9f
[    3.048449] codec out - reg 0x6 = 0xbf
[    3.048449] codec out - reg 0x7 = 0xbf
[    3.048449] codec out - reg 0x8 = 0x20
[    3.048449] codec out - reg 0x9 = 0x8
[    3.048449] codec out - reg 0xa = 0x0
[    3.048449] codec out - reg 0xb = 0x0
[    3.048449] codec out - reg 0xc = 0x40
[    3.048449] codec out - reg 0xd = 0xfc
[    3.048449] codec out - reg 0xe = 0x0
[    3.048449] codec out - reg 0xf = 0x0
[    3.048449] codec out - reg 0x10 = 0x80
[    3.048449] codec out - reg 0x11 = 0x1
[    3.048449] codec out - reg 0x12 = 0x9f
[    3.048449] codec out - reg 0x13 = 0x9f
[    3.048449] codec out - reg 0x14 = 0x0
[    3.048449] codec out - reg 0x15 = 0x0
[    3.048449] codec out - reg 0x16 = 0x0
[    3.048449] codec out - reg 0x17 = 0x0
[    3.048449] codec out - reg 0x18 = 0x0
[    3.048449] codec out - reg 0x19 = 0x0
[    3.048449] codec out - reg 0x1a = 0xcf
[    3.048449] codec out - reg 0x1b = 0x0
[    3.048449] codec out - reg 0x1c = 0x20
[    3.048449] codec out - reg 0x1d = 0x0
[    3.048449] codec out - reg 0x1e = 0x0
[    3.048449] codec out - reg 0x1f = 0x0
[    3.064770] (1) jiffies = 4294893060
[    3.065068] (2) jiffies = 4294893060
[    3.065327] (3) jiffies = 4294893060
[    3.065580] mce_down - exit = 0xb
[    3.067923] codec out - reg 0x49 = 0x8
[    3.072639] (1) jiffies = 4294893062
[    3.088702] (2) jiffies = 4294893066
[    3.088995] (3) jiffies = 4294893066
[    3.089248] mce_down - exit = 0xb
[    3.089519] codec out - reg 0x49 = 0x0
[    3.089792] codec out - reg 0x50 = 0x80
[    3.096622] (1) jiffies = 4294893068
[    3.096917] (2) jiffies = 4294893068
[    3.097177] (3) jiffies = 4294893068
[    3.097430] mce_down - exit = 0xb
[    3.097690] codec out - reg 0x11 = 0x1
[    3.097972] codec out - reg 0x48 = 0x20
[    3.104619] (1) jiffies = 4294893070
[    3.104919] (2) jiffies = 4294893070
[    3.105177] (3) jiffies = 4294893070
[    3.105429] mce_down - exit = 0xb
[    3.105701] codec out - reg 0x5c = 0x20
[    3.112623] (1) jiffies = 4294893072
[    3.112927] (2) jiffies = 4294893072
[    3.113187] (3) jiffies = 4294893072
[    3.113437] mce_down - exit = 0xb
[    3.143393] ALSA device list:
[    3.143703]   #0: CS4232 at 0x534, irq 5, dma 1&3
[...]
[   27.007311] codec out - reg 0x6 = 0xbf
[   27.007417] codec out - reg 0x7 = 0xbf
[   27.008444] codec out - reg 0x6 = 0xbf
[   27.008548] codec out - reg 0x7 = 0xbf
[   27.009052] codec out - reg 0x12 = 0x9f
[   27.009152] codec out - reg 0x13 = 0x9f
[   27.009853] codec out - reg 0x12 = 0x9f
[   27.009959] codec out - reg 0x13 = 0x9f
[   27.010473] codec out - reg 0x2 = 0x9f
[   27.010570] codec out - reg 0x3 = 0x9f
[   27.011269] codec out - reg 0x2 = 0x9f
[   27.011370] codec out - reg 0x3 = 0x9f
[   27.011876] codec out - reg 0x4 = 0x9f
[   27.011976] codec out - reg 0x5 = 0x9f
[   27.013001] codec out - reg 0x4 = 0x9f
[   27.013109] codec out - reg 0x5 = 0x9f
[   27.013568] codec out - reg 0x1a = 0xcf
[   27.014273] codec out - reg 0x1a = 0xcf
[   27.014780] codec out - reg 0x1a = 0xcf
[   27.015267] codec out - reg 0x1a = 0xcf
[   27.056394] codec out - reg 0x0 = 0x0
[   27.056498] codec out - reg 0x1 = 0x0
[   27.057193] codec out - reg 0x0 = 0x0
[   27.057293] codec out - reg 0x1 = 0x0
[   27.057801] codec out - reg 0x0 = 0x0
[   27.057900] codec out - reg 0x1 = 0x0
[   27.058383] codec out - reg 0xd = 0xfc
[   27.059130] codec out - reg 0xd = 0xfc

```

I belive it is quite complete informaton about sound card hardware and I belive it all means it works.

But, in the end:
```
san@ubuntu:/proc/asound$ aplay -l
aplay: device_list:223: no soundcards found...

```

Please, help.
Regards.

edit.
```
san@ubuntu:/dev/snd$ cat ../sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.20 emulation code)
Kernel: Linux ubuntu 2.6.31.5-hp5k-0v1.5 #23 Sat Dec 19 16:44:41 CET 2009 i586
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
CS4232 at 0x534, irq 5, dma 1&3

Audio devices:
0: CS4232 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: CS4232 MIDI

Timers:
31: system timer

Mixers:
0: CS4232
```

---

