---
title: "TV card working?"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by usacomp2k3 on 2006-06-03
I have the 878 TV card, philips tuner. I'm trying to get it working with MythTV, but alas, no luck. I also installed TVtime just to make sure the TV card is working first, before trying to configutre mythtv. Anyway, TVtime is telling me that it "cannot open capture device /dev/video0."
I looked at the dmesg, and this is what it said about the tv card:
> [4294692.351000] bttv: `' invalid for parameter `adc_crush'
[4294692.408000] bt878: Unknown symbol bttv_read_gpio
[4294692.408000] bt878: Unknown symbol bttv_write_gpio
[4294692.408000] bt878: Unknown symbol bttv_gpio_enable

I setup the bttv using a previous thread I found, and here's whats in the file /etc/modprobe.d/bttv
> # i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=78 tuner=1 radio=1 pll=1 adc_crush=

Any thoughts. I really don't know what I'm doing, knowing very little about linux, so even pointing me in the right place, I'd be grateful. Thanks.

---

### Post by usacomp2k3 on 2006-06-05
I should also say that the card shows up in the device manager, I don't remember the exact wording, but it's there.

---

### Post by usacomp2k3 on 2006-06-06
Bump.
Do I have this in the wrong section or something?

---

### Post by usacomp2k3 on 2006-06-14
Should I just give up, I'm guessing?

---

### Post by tkman on 2006-06-15
Sorry no one seems to be replying.  I can't figure out why people will try to help one person out yet leave others in the dust.

If I could offer you any suggestions I would.  I know that by having your device classified as bttv you should have a shot at getting it to work.  Seems others have had success with that card type.

---

### Post by ianmac on 2006-06-15
Original poster is probably long gone, but just in case...

the file included was:
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=78 tuner=1 radio=1 pll=1 adc_crush=

The error message was:
[4294692.351000] bttv: `' invalid for parameter `adc_crush'

my guess would be that the blank adc_crush parameter was not appreciated by the bttv module...  taken this parameter out might help things...

Ian

---

### Post by usacomp2k3 on 2006-06-16
[QUOTE=ianmac]Original poster is probably long gone, but just in case...

the file included was:
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=78 tuner=1 radio=1 pll=1 adc_crush=

The error message was:
[4294692.351000] bttv: `' invalid for parameter `adc_crush'

my guess would be that the blank adc_crush parameter was not appreciated by the bttv module...  taken this parameter out might help things...

Ian[/QUOTE]
Thanks for the suggestion. I'll see if that helps things.

---

### Post by usacomp2k3 on 2006-06-16
```
[4294693.502000] bttv0: Bt878 (rev 17) at 0000:00:08.0, irq: 177, latency: 32, mmio: 0xdddfe000
[4294693.502000] bttv0: using: Jetway TV/Capture JW-TV878-FBK, Kworld KW-TV878RF[card=78,insmod option]
[4294693.502000] bttv0: gpio: en=00000000, out=00000000 in=003fffff [init]
[4294693.502000] i2c-algo-bit.o: (0) scl=1, sda=1
[4294693.502000] i2c-algo-bit.o: (1) scl=1, sda=0
[4294693.502000] i2c-algo-bit.o: (2) scl=1, sda=1
[4294693.502000] i2c-algo-bit.o: (3) scl=0, sda=1
[4294693.502000] i2c-algo-bit.o: (4) scl=1, sda=1
[4294693.502000] i2c-algo-bit.o: bt878 #0 [sw] passed test.
[4294693.505000] bttv0: using tuner=1
[4294693.505000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294693.507000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294693.510000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294693.955000] ts: Compaq touchscreen protocol output
[4294694.542000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[4294694.542000] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[4294694.542000] tuner 0-0060: type set to 1 (Philips PAL_I (FI1246 and compatibles))
[4294694.575000] bttv0: registered device video0
[4294694.575000] bttv0: registered device vbi0
[4294694.575000] bttv0: registered device radio0
[4294694.575000] bttv0: PLL: 28636363 => 35468950 .. ok
[4294694.639000] bt878: AUDIO driver version 0.0.0 loaded
[4294694.640000] bt878: Bt878 AUDIO function found (0).
[4294694.640000] ACPI: PCI Interrupt 0000:00:08.1[A] -> GSI 16 (level, low) -> IRQ 177
[4294694.640000] bt878(0): Bt878 (rev 17) at 00:08.1, irq: 177, latency: 32, memory: 0xdddff000

```
that's the dmesg output. I'll check when I get home to see if it shows up any better in the device manager/ITTV (ssh'ing in right now)

---

### Post by usacomp2k3 on 2006-06-19
Well the good news is that I'm now able to get most the channels. However, there are a few problems.
1/ it's in black/white. No color on any of the channels (this is broadcast TV, not cable)
2/ channel 9 shows up as 10, 27 as 28, and so on and so forth. Any clues on that?

---

