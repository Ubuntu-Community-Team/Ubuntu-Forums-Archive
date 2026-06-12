---
title: "IVTV installation failure"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by e1jones on 2006-12-05
Ubuntu with a PVR-500.  dmesg outut below.... apparently a bunch of junk got mixed in.  any help would be appreciated :)

[17179592.988000] ivtv:  ==================== START INIT IVTV ====================
[17179592.988000] ivtv:  version 0.7.0 (tagged release) loading
[17179592.988000] ivtv:  Linux version: 2.6.17-10-386 mod_unload 486 REGPARM gcc-4.1
[17179592.988000] ivtv:  In case of problems please include the debug info between
[17179592.988000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179592.988000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179593.100000] NET: Registered protocol family 17
[17179593.280000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179593.360000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179593.360000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179593.360000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179593.360000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17179593.360000] wifi0: mac 7.9 phy 4.5 radio 5.6
[17179593.360000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17179593.360000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17179593.360000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17179593.360000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17179593.360000] wifi0: Use hw queue 8 for CAB traffic
[17179593.360000] wifi0: Use hw queue 9 for beacons
[17179593.468000] ts: Compaq touchscreen protocol output
[17179593.472000] wifi0: Atheros 5212: mem=0xfdce0000, irq=58
[17179593.472000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[17179593.472000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 217
[17179593.472000] PCI: Setting latency timer of device 0000:00:10.2 to 64
[17179593.796000] intel8x0_measure_ac97_clock: measured 54965 usecs
[17179593.796000] intel8x0: clocking to 46973
[17179593.796000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179593.796000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[17179593.796000] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 66
[17179593.796000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179593.892000] tveeprom 0-0050: Hauppauge model 23552, rev E687, serial# 10025028
[17179593.892000] tveeprom 0-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[17179593.892000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179593.892000] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[17179593.892000] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[17179593.892000] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[17179593.892000] tveeprom 0-0050: has radio, has no IR remote
[17179593.892000] ivtv0: This is the first unit of a PVR500
[17179593.900000] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[17179593.900000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 66
[17179593.900000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179593.976000] tuner 0-0060: TEA5767 detected.
[17179593.976000] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[17179593.976000] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[17179593.976000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179594.284000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179594.332000] cx25840 0-0044: unable to open firmware v4l-cx25840.fw
[17179594.444000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179595.120000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17179595.120000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17179595.120000] ivtv0 warning: failed loading encoder firmware
[17179595.120000] ivtv0 warning: Error loading firmware -3!
[17179595.120000] ivtv0: Error -3 initializing firmware.
[17179595.120000] ivtv0: Error -12 on initialization
[17179595.120000] ivtv: probe of 0000:05:08.0 failed with error -12
[17179595.120000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179595.392000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179595.392000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[17179595.392000] ACPI: PCI Interrupt 0000:05:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 74
[17179595.392000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179595.472000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179595.736000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179595.768000] cx25840 0-0044: unable to open firmware v4l-cx25840.fw
[17179595.868000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179595.940000] tveeprom 0-0050: Hauppauge model 23552, rev E687, serial# 10025028
[17179595.940000] tveeprom 0-0050: tuner model is Samsung TCPN 2121P30A (idx 87, type 70)
[17179595.940000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179595.940000] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[17179595.940000] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[17179595.940000] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[17179595.940000] tveeprom 0-0050: has radio, has no IR remote
[17179595.940000] ivtv0: This is the second unit of a PVR500
[17179595.940000] ivtv0: Correcting tveeprom data: no radio present on second unit
[17179596.632000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw
[17179596.632000] ivtv0: did you put the firmware in the hotplug firmware directory?
[17179596.632000] ivtv0 warning: failed loading encoder firmware
[17179596.632000] ivtv0 warning: Error loading firmware -3!
[17179596.632000] ivtv0: Error -3 initializing firmware.
[17179596.632000] ivtv0: Error -12 on initialization
[17179596.632000] ivtv: probe of 0000:05:09.0 failed with error -12
[17179596.632000] ivtv:  ====================  END INIT IVTV  ====================

---

### Post by moma on 2006-12-06
I have no direct answer to your question, but I just installed ivtv driver and firmware files for my Hauppauge 350 TV-card. It works like a dream.

Scribbled down some lines about it. 

EDIT: Sorry, wrong link. 
The correct link is: [http://www.futuredesktop.org/hauppauge_350-2.html](http://www.futuredesktop.org/hauppauge_350-2.html)

PVR-500 is basically 2 PVR-150 cards.
Where did you put your firmware files?

---

### Post by trubblemaker on 2006-12-06
from your dmesg:
> [17179595.120000] ivtv0: unable to open firmware v4l-cx2341x-enc.fw


you having issues loading the firmware, there's some trouble shooting steps at the bottom of the [edgy howto]("https://help.ubuntu.com/community/Install_IVTV_Edgy#head-9d062fae8631f715fb10eb73624cae061fe61f69")

> I had issues with the firmware trying to be load, turned out the softlinks in /lib/firmware needed to be actual copies of the file (if they are softlinks for you).

sudo cp v4l-cx2341x-dec.fw ivtv-fw-dec.bin


---

