---
title: "ivtv installation on edgy for PVR150"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by Beezleblub on 2007-03-08
Hiya,
am new to linux, trying to set up mythtv.
3 Nights of reading forums and ivtv how-to's  but I 'm still in the dark on how to get ivtv to work on my edgy installation.

installation is ubuntu edgy,  2.6.17.11 generic kernel. (uname -a)

DMA settinf in the Bios are OK, Cold start is no help either... :(

the main problem I guess is : 

ivtv0: i2c hardware 0x00000001 not found for command 0xc008561c!

dmesg says :

dirk@meemee:/etc$ dmesg |grep initialized
[17179570.356000] Security Framework v1.0.0 initialized
[17179571.764000] audit(1173354012.764:1): initialized
[17179572.152000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.228000] Capability LSM initialized
[17179575.120000] SCSI subsystem initialized
[17179597.468000] Bluetooth: HCI device and connection manager initialized
[17179597.468000] Bluetooth: HCI socket layer initialized
[17179597.488000] Bluetooth: L2CAP socket layer initialized
[17179597.488000] Bluetooth: RFCOMM socket layer initialized
[17179597.488000] Bluetooth: RFCOMM TTY layer initialized
dirk@meemee:/etc$ 

that means ivtv is not loaded ?

ivtv block in dmesg :
[17179583.960000] ivtv:  ==================== START INIT IVTV ====================
[17179583.960000] ivtv:  version 0.7.4 (tagged release) loading
[17179583.960000] ivtv:  Linux version: 2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179583.960000] ivtv:  In case of problems please include the debug info between
[17179583.960000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179583.960000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179583.960000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179583.964000] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 17 (level, low) -> IRQ 217
[17179583.964000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179583.972000] drivers/usb/input/hid-core.c: couldn't find an input interrupt endpoint
[17179583.992000] ts: Compaq touchscreen protocol output
[17179583.996000] input: Shuttle Inc VFD Module as /class/input/input4
[17179583.996000] input: USB HID v1.11 Device [Shuttle Inc VFD Module] on usb-0000:00:1d.2-2
[17179583.996000] usbcore: registered new driver usbhid
[17179583.996000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179584.036000] tveeprom 0-0050: The eeprom says no radio is present, but the tuner type
[17179584.036000] tveeprom 0-0050: indicates otherwise. I will assume that radio is present.
[17179584.036000] tveeprom 0-0050: Hauppauge model 26159, rev G1A5, serial# 10016257
[17179584.036000] tveeprom 0-0050: tuner model is TCL MPE05-2 (idx 105, type 38)
[17179584.036000] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[17179584.036000] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[17179584.036000] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[17179584.036000] tveeprom 0-0050: has radio, has IR remote
[17179584.064000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179584.176000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179584.176000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179584.564000] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[17179585.076000] NET: Registered protocol family 17
[17179585.316000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[17179585.532000] ivtv0: Encoder revision: 0x02060039
[17179585.532000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179585.532000] ivtv0: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2048KB total)
[17179585.532000] ivtv0: Allocate DMA encoder VBI stream: 80 x 26208 buffers (2048KB total)
[17179585.532000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179585.532000] ivtv0: Create encoder radio stream
[17179585.532000] ivtv0: i2c hardware 0x00000001 not found for command 0xc008561c!
[17179585.532000] ivtv0: i2c addr 0x44 not found for command 0x4008646f!
[17179585.532000] ivtv0: i2c hardware 0x00000020 not found for command 0x4008646d!
[17179585.532000] ivtv0: i2c hardware 0x00000001 not found for command 0x4008646d!
[17179585.532000] ivtv0: i2c hardware 0x00000001 not found for command 0xc008561c!
[17179585.532000] ivtv0: i2c hardware 0x00000001 not found for command 0xc008561c!
[17179585.540000] ivtv0: i2c hardware 0x00000001 not found for command 0xc008561c!
[17179585.540000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[17179585.540000] ivtv:  ====================  END INIT IVTV  ====================


Now I have see similar pages in forums, but non of the solutions worked for me so far.
Any advise on what's next ? 
Thanks.

---

### Post by Beezleblub on 2007-03-08
So I skipped ivtv and moved on to lirc...

followed how-to page for pvr150, cvs drivers...

All goes well, until I do : dmesg, and it says 'kernel tainted' 
What does that mean ?  is it related to my ivtv problem ?

 dmesg | tail
[17179629.920000] Bluetooth: RFCOMM ver 1.7
[17179646.624000] cdrom: hda: mrw address space DMA selected
[17179646.768000] cdrom: hda: mrw address space DMA selected
[17179646.844000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179646.952000] ISOFS: changing to secondary root
[17182066.560000] lirc_dev: IR Remote Control driver registered, at major 61 
[17182066.560000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17182066.580000] bttv: driver version 0.9.16 loaded
[17182066.580000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17182066.620000] cx2388x v4l2 driver version 0.0.5 loaded

---

### Post by ravalox on 2007-03-09
This may help you: [https://help.ubuntu.com/community/Install_IVTV_Edgy#head-9d062fae8631f715fb10eb73624cae061fe61f69](https://help.ubuntu.com/community/Install_IVTV_Edgy#head-9d062fae8631f715fb10eb73624cae061fe61f69)

---

### Post by Beezleblub on 2007-03-09
Thanks. 

That is the guide I have followed.
Yesteday I started from scratch, new Ubuntu edgy Install, then followed this link again.
ivtv is working now :-)  no ideay what the heck I did different the first time.. :confused: 

anyway, on with lirc now :)... am stuck again already, irw exits back to terminal imediatly. will check the forum for this first :) 

Cheers :)

---

### Post by Beezleblub on 2007-03-10
Humm... Still no luck with Lirc.. 
irw always crashes out to terminal. 

Now I think I messed up , too many lirc files / driver versions loaded :( 

ls -l /dev/lirc* gives me :

/dev/lirc
/dev/lirc0
/dev/lircm

how do I clean up such multi-versio installation ? 

Anyone good ideas on what the pvr150 need to get the ir to work ?

Thanks.

---

