---
title: "PVR-150 Installation Issues"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by planetmn on 2006-07-09
Trying to set up my box for MythTV following Hyams guide and the how-to posted on the board here.  I have just finished the steps installing the ivtv drivers, but something doesn't seem to be right.  While I think the drivers are installed, no program (mplayer and xawtv) can get a signal from the card.  If I run:
```
depmod
modprobe ivtv
dmesg
```
I get the following relevant messages:
```
[4294922.455000] ivtv:  ==================== START INIT IVTV =================== =
[4294922.455000] ivtv:  version 0.4.4 (tagged release) loading
[4294922.456000] ivtv:  Linux version: 2.6.15.7-ubuntu1 preempt 486 gcc-4.0
[4294922.456000] ivtv:  In case of problems please include the debug info betwee n
[4294922.456000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294922.456000] ivtv:  any module options, when mailing the ivtv-users mailingl ist.
[4294922.457000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[4294922.457000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 11 (l evel, low) -> IRQ 11
[4294922.502000] tveeprom: ivtv version
[4294922.502000] tveeprom: Hauppauge: model = 26132, rev = G1B2, serial# = 95187 86
[4294922.502000] tveeprom: tuner = <unknown> (idx = 112, type = 4)
[4294922.502000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000 )
[4294922.502000] tveeprom: audio processor = CX25841 (type = 23)
[4294922.503000] tveeprom: decoder processor = CX25841 (type = 1c)
[4294922.503000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294922.512000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver # 0
[4294922.512000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294922.718000] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[4294924.873000] printk: 615 messages suppressed.
[4294924.873000] eth1: Information frame lost.
[4294926.281000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[4294926.342000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294926.349000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294926.362000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294927.288000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294927.504000] ivtv0: Encoder revision: 0x02050032
[4294927.505000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4 096KB total)
[4294927.514000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (20 48KB total)
[4294927.516000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (20 48KB total)
[4294927.517000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer s (2048KB total)
[4294927.519000] tuner: type set to 4 (NoTuner) by ivtv i2c driver #0
[4294928.079000] ivtv0: Initialized WinTV PVR 150, card #0
[4294928.079000] ivtv:  ====================  END INIT IVTV  =================== 
```
Everything looks fine, but the third line from the bottom is where I think there is an issue.  The card is a standard Hauppage PVR-150 card and has a tuner on it.  Does anybody know if this is the problem?  And if so how I can force ivtv to see the tuner?

Thanks,
dave

---

### Post by skattman83 on 2006-08-31
I'm having the same problem.  Did you ever find a solution?

---

### Post by NT4usB on 2006-08-31
When I set mine up, everything was installed correctly and looked ok but they didn't work.
I said ***F*** it, shut down and went to bed.
Next day they worked perfectly.
Turns out, sometimes you need to power down the PC for a while so the card(s) can reset some of their innards.

---

### Post by crispy_420 on 2006-09-01
That is true...

I beat my head against the wall because I had errors in dmesg. And I was getting very frustated. Then I read someone that a shutdown/reboot sometimes works. And what do you know it did. Don't know why or how it suddenly works, but who cares, it works.

---

### Post by Titus A Duxass on 2006-09-01
If you take a look on the ivtv website, they recommend shut down, remove power cable, wait a minimum of 30 seconds and then power up.

30 seconds is a long time, but it does the job.

---

### Post by handband2 on 2006-09-20
I just followed the [Hyams]("http://hyams.webhop.net/mythtv/myth_ubuntu.html") guide and when running:
```
depmod
modprobe ivtv
dmesg
```

I get this:

```
[17179589.132000] ivtv:  ==================== START INIT IVTV ====================
[17179589.132000] ivtv:  version 0.4.6 (tagged release) loading
[17179589.132000] ivtv:  Linux version: 2.6.15-27-386 preempt 486 gcc-4.0
[17179589.132000] ivtv:  In case of problems please include the debug info between
[17179589.132000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179589.132000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179589.276000] hda_codec: Unknown model for AD1988, trying auto-probe from BIOS...
[17179589.500000] **** SET: Misaligned resource pointer: f7f74a02 Type 07 Len 0
[17179589.500000] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[17179589.500000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 130
[17179589.500000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[17179589.500000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179589.524000] ivtv0: Autodetected WinTV PVR 150 card (cx23416 based)
[17179589.524000] **** SET: Misaligned resource pointer: f7f881c2 Type 07 Len 0
[17179589.524000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[17179589.524000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 138
[17179589.524000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179589.616000] tveeprom: ivtv version
[17179589.616000] tveeprom: Hauppauge: model = 26552, rev = G1A3, serial# = 9624859
[17179589.616000] tveeprom: tuner = TCL MFNM05-4 (idx = 103, type = 43)
[17179589.616000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[17179589.616000] tveeprom: audio processor = CX25843 (type = 25)
[17179589.616000] tveeprom: decoder processor = CX25843 (type = 1e)
[17179589.616000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[17179589.688000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17179589.688000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17179589.816000] parport: PnPBIOS parport detected.
[17179589.816000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[17179589.868000] cx25840 0-0044: ivtv driver
[17179589.868000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179590.044000] cx25840 0-0044: unable to open firmware v4l-cx25840.fw
[17179590.096000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17179590.120000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179590.124000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[17179590.136000] tda9887 0-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[17179590.136000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[17179590.756000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17179590.756000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17179590.756000] ivtv0 warning: failed loading encoder firmware
[17179590.756000] ivtv0 warning: Error loading firmware -3!
[17179590.756000] ivtv0: Error -3 initializing firmware.
[17179590.756000] ivtv0: Error -12 on initialization
[17179590.756000] ivtv: probe of 0000:01:07.0 failed with error -12
[17179590.756000] ivtv:  ====================  END INIT IVTV  ====================

```

I'm not sure why the problem is occuring :-k 
Can anyone help?
Thanks!!

---

