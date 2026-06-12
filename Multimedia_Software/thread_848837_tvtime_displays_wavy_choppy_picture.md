---
title: "tvtime displays wavy choppy picture"
date: 2008-07-03
forum: Multimedia Software
---

### Post by loneblender on 2008-07-03
I installed a PCI AverMedia TV tuner card on a Dell Inspiron 530 running Ubuntu 8.04.  I believe the tuner card is detected properly, but tvtime doesn't find most channels, and the channels it detects are choppy/intermittent/bad quality (see attached screenshot).

Thanks in advance for any very much appreciated help (hours of Googling has failed me :-)

Some (hopefully useful) system messages are below.

$ lspci -v
...
02:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Avermedia Technologies Inc AverMedia UltraTV PCI 350
	Flags: bus master, medium devsel, latency 16, IRQ 16
	Memory at fddff000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

02:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Avermedia Technologies Inc UltraTV PCI 350
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at fddfe000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

$ dmesg
...
[   38.436981] bttv: driver version 0.9.17 loaded
[   38.436983] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   38.437013] bttv: Bt8xx card found (0).
[   38.437028] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.437036] bttv0: Bt878 (rev 17) at 0000:02:01.0, irq: 16, latency: 16, mmio: 0xfddff000
[   38.437223] bttv0: detected: AVerMedia TVPhone98 [card=41], PCI subsystem ID is 1461:0003
[   38.437225] bttv0: using: AVerMedia TVPhone 98 [card=41,autodetected]
[   38.437245] bttv0: gpio: en=00000000, out=00000000 in=00ecf6c3 [init]
[   38.468105] bttv0: Avermedia eeprom[0x4803]: tuner=2 radio:yes remote control:yes
[   38.468109] bttv0: tuner type=2
[   38.475482] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   38.476076] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   38.476666] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   38.542439] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   38.542451] tuner-simple 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   38.542453] tuner 0-0061: type set to Philips NTSC (FI123
[   38.542455] tuner-simple 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   38.542457] tuner 0-0061: type set to Philips NTSC (FI123
[   38.551390] bttv0: registered device video0
[   38.551402] bttv0: registered device vbi0
[   38.551414] bttv0: registered device radio0
[   38.551434] bttv0: PLL: 28636363 => 35468950 .. ok
[   38.581728] input: bttv IR (card=41) as /devices/pci0000:00/0000:00:1e.0/0000:02:01.0/input/input8
[   38.657416] bt878: AUDIO driver version 0.0.0 loaded
[   38.657435] bt878: Bt878 AUDIO function found (0).
[   38.657450] ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 16 (level, low) -> IRQ 16
[   38.657455] bt878_probe: card id=[0x31461], Unknown card.
[   38.657455] Exiting..
[   38.657458] ACPI: PCI interrupt for device 0000:02:01.1 disabled
[   38.657462] bt878: probe of 0000:02:01.1 failed with error -22
[   38.673882] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   38.673896] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   38.737978] ACPI: PCI Interrupt 0000:02:01.1[A] -> GSI 16 (level, low) -> IRQ 16
[   38.737989] PCI: Setting latency timer of device 0000:02:01.1 to 64
[   38.738071] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/bt87x.c:947: bt87x0: Using board 5, ana
log, digital (rate 48000 Hz)
[   39.059690] lp: driver loaded but no devices found
[   39.104780] it87: Found IT8718F chip at 0x290, revision 3
[   39.104786] it87: in3 is VCC (+5V)
[   39.104787] it87: in7 is VCCH (+5V Stand-By)
...
[  143.731871] bttv0: PLL can sleep, using XTAL (28636363).
[  159.538837] bttv0: IRQ lockup, clearing GPINT from int mask [bits: OFLOW GPINT*]
[ 1311.199788] bttv0: PLL: 28636363 => 35468950 .. ok
[ 1484.313014] bttv0: PLL can sleep, using XTAL (28636363).

---

### Post by 0x656b694d on 2009-05-17
hi.

any luck so far?

same picture here, but tvtime-scanner has found a lot of channels though.

---

### Post by xc3RnbFO8P on 2009-05-17
Do you use outdoor antenna?

---

### Post by 0x656b694d on 2009-05-17
yes, i do. It works fine in Windows, btw.
Looks like the signal is incorrectly decoded.
I use SECAM as do in Windows. And the same frequency table.

---

### Post by xc3RnbFO8P on 2009-05-17
Show the output of /home/your folder/.tvtime/tvtime.xml

---

### Post by 0x656b694d on 2009-05-17
i did the following:
```

$ tvtime-configure -f custom -x /dev/mixer:video -n SECAM -A

```

So got the following config file:
```

<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="Widescreen" value="0"/>
  <option name="Fullscreen" value="0"/>
  <option name="Verbose" value="0"/>
  <option name="WindowGeometry" value="0x576"/>
  <option name="InputWidth" value="720"/>
  <option name="V4LDevice" value="/dev/video0"/>
  <option name="VBIDevice" value="/dev/vbi0"/>
  <option name="V4LInput" value="0"/>
  <option name="Norm" value="SECAM"/>
  <option name="Frequencies" value="custom"/>
  <option name="MixerDevice" value="/dev/mixer:video"/>
  <option name="XMLTVFile" value="none"/>
  <option name="XMLTVLanguage" value="none"/>
  <option name="ProcessPriority" value="-10"/>
<option name="Channel" value="7"/><option name="DefaultBrightness" value="-1"/><option name="DefaultContrast" value="-1"/><option name="DefaultSaturation" value="-1"/><option name="DefaultHue" value="-1"/><option name="PrevChannel" value="6"/><option name="FramerateMode" value="0"/><option name="OverScan" value="3.5"/><option name="CheckForSignal" value="1"/><option name="AudioBoost" value="-1"/><option name="AlwaysOnTop" value="0"/><option name="QuietScreenshots" value="0"/><option name="UnmuteVolume" value="0"/><option name="Muted" value="1"/><option name="AudioMode" value="stereo"/><option name="PalDKMode" value="0"/></tvtime>

```

// ubuntu 9.04, nvidia 96.43.11, tvtime v1.0.2

verbose run:
```

$ tvtime -v
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/mikhail/.tvtime/tvtime.xml
cpuinfo: CPU Intel(R) Pentium(R) 4 CPU 1.60GHz, family 15, model 2, stepping 4.
cpuinfo: CPU measured at 1607.236MHz.
xcommon: Display :0.0, vendor The X.Org Foundation, vendor release 10600000
xfullscreen: Using XINERAMA for dual-head information.
xfullscreen: Pixels are square.
xfullscreen: Number of displays is 1.
xfullscreen: Head 0 at 0,0 with size 1280x1024.
xcommon: Have XTest, will use it to ping the screensaver.
xcommon: Pixel aspect ratio 1:1.
xcommon: Pixel aspect ratio 1:1.
xcommon: Window manager is compiz and is EWMH compliant.
xcommon: Using EWMH state fullscreen property.
xcommon: Using EWMH state above property.
xcommon: Using EWMH state below property.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xvoutput: Using XVIDEO adaptor 306: NV17 Video Texture.
speedycode: Using MMXEXT optimized functions.
station: Reading stationlist from /home/mikhail/.tvtime/stationlist.xml
videoinput: Using video4linux2 driver 'saa7134', card 'Beholder BeholdTV 507 FM/RDS / ' (bus PCI:0000:02:0c.0).
videoinput: Version is 526, capabilities 5010015.
videoinput: Maximum input width: 720 pixels.
tvtime: Sampling input at 720 pixels per scanline.
xcommon: Pixel aspect ratio 1:1.
xcommon: Displaying in a 768x576 window inside 768x576 space.
xcommon: Received a map, marking window as visible (61).
tvtime: Cleaning up.
Thank you for using tvtime.

```

thanks.

---

### Post by xc3RnbFO8P on 2009-05-17
I am not sure what your problem is, but read this:
[http://debianletters.blogspot.com/2008/01/tv-tuner-beholder-beholdtv-409fm-in.html]("http://debianletters.blogspot.com/2008/01/tv-tuner-beholder-beholdtv-409fm-in.html")

---

### Post by 0x656b694d on 2009-05-17
Thanks a lot, Ringi!

I just added a file:
```

$ cat /etc/modprobe.d/beholder.conf 
options tuner secam=d
options tda9887 secam=d

```
Don't know what does this thing do though. I think for new kernels only first line of the file really needed.

now it works cool!

Regards,
-Mike

---

