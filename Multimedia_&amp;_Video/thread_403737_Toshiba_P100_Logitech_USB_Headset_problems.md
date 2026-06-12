---
title: "Toshiba P100 Logitech USB Headset problems"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by kombinator on 2007-04-07
I'm running Kubuntu Feisty on a Toshiba P100 PSPA3C-SD300E with the kernel patched with custom DSDT so sound works with ACPI.  ALSA is the latest dev release, 1.0.14-rc3.

My sound is simply brilliant, but when I plug in my Logitech headset, it detects as a USB device and shows up on the device manager as Logitech USB Headset but is essentially nonfunctioning.  lsusb produces the following:

```

ding@chavez-Xpress:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 006: ID 046d:0a01 Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

However, when I try to record, nothing happens, the sound doesn't come out of the headset and instead continues to come out of my speakers.

So, investigating further, cat /proc/asound/cards produces only:

```

ding@chavez-Xpress:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2500000 irq 21

```

and aplay -l merely:

```

ding@chavez-Xpress:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Truly a puzzlement: it detects perfectly fine as a USB device (indeed, as a USB headset no less), but ALSA refuses to utilize or detect it.  Anyone care to hypothesize on a solution for me?  ](*,)

---

### Post by kombinator on 2007-04-13
I see everyone is stumped (or just ignoring me :D ).  I'm guessing it has something to do with my ALSA compile, since I followed the instructions on how to compile ALSA to improve the HD Intel sound quality after fixing the broken DSDT.

EDIT:  Aaaand...after RTFM, I suddenly realized I didn't compile with the usb-audio module.  Simple problem, simple solution.  I can't get it to record under Sound Recorder but if I unmute the mic in volume control I can hear it fine.

I guess Toshiba just needs a tad more tweaking than a regular stock Ubuntu system.  Oh well.

---

### Post by gogogadget on 2007-09-14
I have the same problem. I am running an Intel PC desktop that I built.

My configuration differs but the results are the same

andrew@SERVER:~$ lsusb
Bus 004 Device 009: ID 046d:c283 Logitech, Inc. WingMan Force 3D
Bus 004 Device 008: ID 04b4:5500 Cypress Semiconductor Corp. HID->COM RS232 Adapter
Bus 004 Device 007: ID 04b4:5203 Cypress Semiconductor Corp. 
Bus 004 Device 006: ID 05e3:0606 Genesys Logic, Inc. 
Bus 004 Device 013: ID 046d:0a01 Logitech, Inc. 
Bus 004 Device 012: ID 0830:0061 Palm, Inc. 
Bus 004 Device 014: ID 04b4:5203 Cypress Semiconductor Corp. 
Bus 004 Device 018: ID 04b4:5a9b Cypress Semiconductor Corp. 
Bus 004 Device 017: ID 04b4:5a9b Cypress Semiconductor Corp. 
Bus 004 Device 016: ID 04b4:5203 Cypress Semiconductor Corp. 
Bus 004 Device 015: ID 04b4:5a9b Cypress Semiconductor Corp. 
Bus 004 Device 011: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 004 Device 010: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 004 Device 004: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 002: ID 05e3:0606 Genesys Logic, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
andrew@SERVER:~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with ALC650E at 0xfc001000, irq 21
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10
 2 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.7-1.4.2, full speed
andrew@SERVER:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
andrew@SERVER:~$

---

