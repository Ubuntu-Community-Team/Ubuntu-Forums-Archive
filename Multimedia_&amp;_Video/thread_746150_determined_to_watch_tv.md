---
title: "determined to watch tv"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by Daverobb on 2008-04-05
Too determined i think - i want to run tvtime and have tried quite a few angles to get it running.  All i get is a quick flash of a black screen and it disappears.  Never seen that before without an error message or anything.  Used tvtime on this exact machine for a long time but had a big crash and had to format everything and reinstall (eventually in safe graphics - could that be an issue?) 

Could some one take a look at my dmesg and advise?  

STATE,COMPAT,ECP]
[  824.850777] Linux agpgart interface v0.102 (c) Dave Jones
[  824.852693] agpgart: Detected AMD 761 chipset
[  824.869522] agpgart: AGP aperture is 128M @ 0xc8000000
[  824.927987] parport_pc: VIA parallel port: io=0x378, irq=7
[  825.135258] Linux video capture interface: v2.00
[  825.218983] bttv: driver version 0.9.17 loaded
[  825.218991] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  825.219083] bttv: Bt8xx card found (0).
[  825.219112] PCI: Enabling device 0000:00:0d.0 (0000 -> 0002)
[  825.219122] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 16 (level, low) -> IRQ 19
[  825.219138] bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 19, latency: 132, mmio: 0xc0002000
[  825.219154] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[  825.219159] bttv0: using: Hauppauge (bt878) [card=10,insmod option]
[  825.219197] bttv0: gpio: en=00000000, out=00000000 in=00ffffd3 [init]
[  825.221685] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[  825.221725] bt878 #0 [sw]: Test OK
[  825.248850] tveeprom 1-0050: Hauppauge model 44981, rev E1B2, serial# 9824475
[  825.248856] tveeprom 1-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[  825.248861] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[  825.248865] tveeprom 1-0050: audio processor is None (idx 0)
[  825.248869] tveeprom 1-0050: decoder processor is BT878 (idx 14)
[  825.248873] tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
[  825.248878] bttv0: Hauppauge eeprom indicates model#44981
[  825.248883] bttv0: using tuner=50
[  825.248888] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[  826.088105] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>usbcore: registered new interface driver hiddev
[  826.735923] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input1
[  826.735994] input: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:04.3-2
[  826.881732] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input2
[  826.881840] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:04.3-2
[  826.886478] input: HID 0d8c:000c as /class/input/input3
[  826.886536] input: USB HID v1.00 Device [HID 0d8c:000c] on usb-0000:00:0f.1-1
[  826.886557] usbcore: registered new interface driver usbhid
[  826.886564] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  827.248605] not found
[  827.248616] bttv0: i2c: checking for TDA7432 @ 0x8a... <6>usbcore: registered new interface driver xpad
[  827.276849] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[  827.307290] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x3A02
[  827.307334] usbcore: registered new interface driver usblp
[  827.307341] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[  827.363798] input: PC Speaker as /class/input/input4
[  827.443389] not found
[  828.045371] usbcore: registered new interface driver snd-usb-audio
[  828.153425] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  828.197970] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[  828.198042] tuner 1-0061: type set to 50 (TCL 2002N)
[  828.198047] tuner 1-0061: type set to 50 (TCL 2002N)
[  828.205733] bttv0: registered device video0
[  828.205780] bttv0: registered device vbi0
[  828.205802] bttv0: PLL: 28636363 => 35468950 . ok
[  828.220654] ACPI: PCI Interrupt 0000:00:04.5[C] -> GSI 22 (level, low) -> IRQ 21
[  828.220711] PCI: Setting latency timer of device 0000:00:04.5 to 64
[  828.251561] bt878: AUDIO driver version 0.0.0 loaded
[  828.736904] bt878: Bt878 AUDIO function found (0).
[  828.736926] PCI: Enabling device 0000:00:0d.1 (0000 -> 0002)
[  828.736936] ACPI: PCI Interrupt 0000:00:0d.1[A] -> GSI 16 (level, low) -> IRQ 19
[  828.736947] bt878_probe: card id=[0x13eb0070], Unknown card.
[  828.736949] Exiting..
[  828.736954] ACPI: PCI interrupt for device 0000:00:0d.1 disabled
[  828.736961] bt878: probe of 0000:00:0d.1 failed with error -22
[  828.775922] ACPI: PCI Interrupt 0000:00:0d.1[A] -> GSI 16 (level, low) -> IRQ 19
[  829.719778] lp0: using parport0 (interrupt-driven).
[  829.802457] Adding 3028212k swap on /dev/hdb5.  Priority:-1 extents:1 across:

thanks!

---

### Post by Daverobb on 2008-04-05
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/dave/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

does this help?

---

### Post by xc3RnbFO8P on 2008-04-05
Show the output of **dmesg | grep bttv**
and the output of (in terminal): **tvtime**

---

### Post by Daverobb on 2008-04-05
dmesg | grep bttv
[  825.218983] bttv: driver version 0.9.17 loaded
[  825.218991] bttv: using 8 buffers with 2080k (520 pages) each for capture
[  825.219083] bttv: Bt8xx card found (0).
[  825.219138] bttv0: Bt878 (rev 17) at 0000:00:0d.0, irq: 19, latency: 132, mmio: 0xc0002000
[  825.219154] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[  825.219159] bttv0: using: Hauppauge (bt878) [card=10,insmod option]
[  825.219197] bttv0: gpio: en=00000000, out=00000000 in=00ffffd3 [init]
[  825.221685] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[  825.248878] bttv0: Hauppauge eeprom indicates model#44981
[  825.248883] bttv0: using tuner=50
[  825.248888] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[  826.088105] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>usbcore: registered new interface driver hiddev
[  827.248616] bttv0: i2c: checking for TDA7432 @ 0x8a... <6>usbcore: registered new interface driver xpad
[  828.153425] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  828.205733] bttv0: registered device video0
[  828.205780] bttv0: registered device vbi0
[  828.205802] bttv0: PLL: 28636363 => 35468950 . ok
[ 2855.337411] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW VPRES RISCI
[ 2860.892522] bttv0: reset, reinitialize
[ 2860.892561] bttv0: PLL: 28636363 => 35468950 . ok
[ 2861.409965] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 2875.106016] bttv0: reset, reinitialize
[ 2875.106057] bttv0: PLL: 28636363 => 35468950 . ok
[ 2875.641938] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 2875.946557] bttv0: reset, reinitialize
[ 2875.946597] bttv0: PLL: 28636363 => 35468950 . ok
[ 2876.465447] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 2884.398552] bttv0: reset, reinitialize
[ 2884.398592] bttv0: PLL: 28636363 => 35468950 . ok
[ 2884.936661] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 2885.744731] bttv0: reset, reinitialize
[ 2885.744772] bttv0: PLL: 28636363 => 35468950 . ok
[ 2886.275904] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 2886.785089] bttv0: reset, reinitialize
[ 2886.785131] bttv0: PLL: 28636363 => 35468950 . ok
[ 2887.299335] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 2890.531862] bttv0: reset, reinitialize
[ 2890.531903] bttv0: PLL: 28636363 => 35468950 . ok
[ 2891.045234] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 2892.218706] bttv0: reset, reinitialize
[ 2892.218744] bttv0: PLL: 28636363 => 35468950 . ok
[ 2892.233126] bttv0: PLL can sleep, using XTAL (28636363).
[ 2892.740269] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW VPRES RISCI
[ 2897.095172] bttv0: reset, reinitialize
[ 2897.095211] bttv0: PLL can sleep, using XTAL (28636363).
[ 2899.356514] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: VSYNC HSYNC OFLOW VPRES RISCI
[ 2901.040949] bttv0: reset, reinitialize
[ 2901.040993] bttv0: PLL can sleep, using XTAL (28636363).
[ 2901.539304] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: VSYNC HSYNC OFLOW VPRES RISCI
[ 2920.046800] bttv0: reset, reinitialize
[ 2920.046839] bttv0: PLL can sleep, using XTAL (28636363).
[ 2931.718233] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: VSYNC HSYNC OFLOW VPRES RISCI
[ 2933.864092] bttv0: reset, reinitialize
[ 2933.864133] bttv0: PLL can sleep, using XTAL (28636363).
[ 2934.460683] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: VSYNC HSYNC OFLOW VPRES RISCI
[ 2934.705229] bttv0: reset, reinitialize
[ 2934.705270] bttv0: PLL can sleep, using XTAL (28636363).
[ 2935.288216] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: VSYNC HSYNC OFLOW VPRES RISCI
[ 2935.752277] bttv0: reset, reinitialize
[ 2935.752318] bttv0: PLL can sleep, using XTAL (28636363).
[ 2936.251680] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: VSYNC HSYNC OFLOW RISCI
[ 2936.363259] bttv0: reset, reinitialize
[ 2936.363300] bttv0: PLL can sleep, using XTAL (28636363).
[ 2936.863328] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: VSYNC HSYNC OFLOW VPRES RISCI
[ 2937.714370] bttv0: reset, reinitialize
[ 2937.714410] bttv0: PLL can sleep, using XTAL (28636363).
[ 2939.649752] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: VSYNC HSYNC OFLOW HLOCK VPRES RISCI
[ 2939.744903] bttv0: reset, reinitialize
[ 2939.744942] bttv0: PLL can sleep, using XTAL (28636363).
[ 2951.906827] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: VSYNC HSYNC OFLOW HLOCK VPRES RISCI
[ 2955.493477] bttv0: reset, reinitialize
[ 2955.493518] bttv0: PLL can sleep, using XTAL (28636363).
[ 2955.992545] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: VSYNC HSYNC OFLOW RISCI
[ 2972.864758] bttv0: reset, reinitialize
[ 2972.864800] bttv0: PLL can sleep, using XTAL (28636363).
[ 2973.362738] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: VSYNC HSYNC OFLOW RISCI
[ 2977.014038] bttv0: reset, reinitialize
[ 2977.014079] bttv0: PLL can sleep, using XTAL (28636363).
[ 2977.512377] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: VSYNC HSYNC OFLOW RISCI
[ 3003.331046] bttv0: reset, reinitialize
[ 3003.331085] bttv0: PLL can sleep, using XTAL (28636363).
[ 3003.829494] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: VSYNC HSYNC OFLOW RISCI
[ 3009.673596] bttv0: reset, reinitialize
[ 3009.673714] bttv0: PLL can sleep, using XTAL (28636363).
[ 3010.464997] bttv0: PLL: 28636363 => 35468950 .. ok
[ 3011.141380] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW VPRES RISCI
[ 3028.048128] bttv0: reset, reinitialize
[ 3028.048168] bttv0: PLL: 28636363 => 35468950 . ok
[ 3028.587533] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3031.284332] bttv0: reset, reinitialize
[ 3031.284371] bttv0: PLL: 28636363 => 35468950 . ok
[ 3031.797696] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3032.154272] bttv0: reset, reinitialize
[ 3032.154315] bttv0: PLL: 28636363 => 35468950 . ok
[ 3032.669207] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3064.111582] bttv0: reset, reinitialize
[ 3064.111625] bttv0: PLL: 28636363 => 35468950 . ok
[ 3064.715125] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3248.822861] bttv0: reset, reinitialize
[ 3248.822902] bttv0: PLL: 28636363 => 35468950 . ok
[ 3249.334804] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3253.895908] bttv0: reset, reinitialize
[ 3253.896027] bttv0: PLL: 28636363 => 35468950 . ok
[ 3255.147543] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3255.353758] bttv0: reset, reinitialize
[ 3255.353887] bttv0: PLL: 28636363 => 35468950 . ok
[ 3255.867108] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3258.326401] bttv0: reset, reinitialize
[ 3258.326445] bttv0: PLL: 28636363 => 35468950 . ok
[ 3258.853438] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3274.238490] bttv0: reset, reinitialize
[ 3274.238531] bttv0: PLL: 28636363 => 35468950 . ok
[ 3275.088251] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f03c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3275.669509] bttv0: reset, reinitialize
[ 3275.669549] bttv0: PLL: 28636363 => 35468950 . ok
[ 3276.183633] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3308.925260] bttv0: reset, reinitialize
[ 3308.925303] bttv0: PLL: 28636363 => 35468950 . ok
[ 3309.488818] bttv0: timeout: drop=0 irq=0/0, risc=1fd3f01c, bits: FMTCHG VSYNC HSYNC OFLOW RISCI
[ 3359.048147] bttv0: reset, reinitialize
[ 3359.048552] bttv0: PLL: 28636363 => 35468950 . ok

---

### Post by xc3RnbFO8P on 2008-04-05
tvtime requires hardware YUY2 overlay support from your video card
ati or nvidia?

---

### Post by Daverobb on 2008-04-05
i think its a raedeon

---

### Post by Daverobb on 2008-04-05
yes - ATI

---

### Post by xc3RnbFO8P on 2008-04-05
Do have restricted driver installed?

---

### Post by Daverobb on 2008-04-05
the ATI accelerated graphics driver was enabled (tvtime didn't work) and i did disabled it (it is nowdisabled) and tvtime still didn't work - right now disabled.

---

### Post by xc3RnbFO8P on 2008-04-05
show output of : **lspci**

---

### Post by Daverobb on 2008-04-05
lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 14)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1d)
00:04.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:04.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:0e.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0f.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0f.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0f.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:05.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

---

### Post by xc3RnbFO8P on 2008-04-05
Did you get this update to day  **Kernel 2.6.24-15** (if you are using ubuntu 7.10)?
The reason I ask is that it is causing problem to some.
I was going to suggest that you use Envy to install video driver, but I think if you haven't got this update, you may run in to some problem.  [http://ubuntuforums.org/showthread.php?t=745508]("http://ubuntuforums.org/showthread.php?t=745508")
Otherwise you can wait until you got this update and if it do not solve your problem, you may decide  to use Envy.
Read this first:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu")
 Download Envy from here: [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb")

---

### Post by Daverobb on 2008-04-05
no update today - how do i check the kernel?

---

### Post by xc3RnbFO8P on 2008-04-05
dpkg --list | grep linux-image

---

### Post by Daverobb on 2008-04-05
yeah, i have 2.6.22.14 so i'll wait

THANKS

---

### Post by Daverobb on 2008-04-05
tried the envy download anyway and now tvtime does stay on screen - there is a darker blue screen on top of the actual picture - i can see the channels beneath it when i resize the screen - there is no sound but i cannot get at the configuration (right click) options to see if i can play around with anything.

any advice?

---

### Post by Daverobb on 2008-04-05
actually hit a bunch of buttons and got it into full screen mode and it works perfectly - volume is fine and have access to the options

the only remaining issue is that the problem detailed above - ie. a dark blue screen blocking the picture exists in non-fullscreen mode - any suggestions on that?

---

### Post by xc3RnbFO8P on 2008-04-05
How did you install Envy?

---

### Post by Daverobb on 2008-04-05
using the launcher and then following the instructions through the app

---

### Post by xc3RnbFO8P on 2008-04-05
In the instruction you should do this in terminal:
> cd /home/ what ever you downloaded Envy <return>
> sudo dpkg -i envy*.deb **Done.**

You need this:
2) Enable Ubuntu's "universe" and "multiverse" repositories. (in Settings, Synaptic Package Manager)
> sudo apt-get install -f

---

### Post by Daverobb on 2008-04-05
Yes, I had done that already - when i ran envy it prompted me to add a few more and did this itself.  TVTime actually does work perfectly in FS mode (hit keyboard 'f') but has that dark blue screen issue in minimized mode -- the picture is there, behind the screen - can be seen when the window is moved/resized.

---

### Post by xc3RnbFO8P on 2008-04-05
You could try to reinstall Tvtime, otherwise I don't know how to solve this.

---

### Post by Daverobb on 2008-04-05
:)

still no small mode picture but perfect in fs mode

---

