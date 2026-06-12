---
title: "[SOLVED] PCTV HD Pro Stick and Mythtv"
date: 2008-03-03
forum: Mythbuntu
---

### Post by bawilson2 on 2008-03-03
I got this tuner last week from Woot.  I have things working pretty well.  I have used the scan command to create a list of channels as in the example here: [http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_USB_Stick](http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_USB_Stick)

I have gotten the tuner to work in both Kaffeine and using a "mplayer dvb://<channel>" but I'm having a little trouble getting things setup in MythTV.   Does anybody have any idea what Card Type I would use when going through the Capture Card Setup in MythTV?

I'm pretty sure this is just a MythTV setup or config problem since I have it working in other places.

Thanks for any help!

---

### Post by Nicezia on 2008-03-04
card setup as follows, 

Tuner 1 Analog (use /dev/video0)
Capture 2 (use DVB Samsungblah blah.

now tell me how you got it working with other programs... i haven't gotten it working at all yet

I tried compiling the v4l-dvb, did a make and make install, everything with swimmgly checked my dmesg and got this

[   42.244672] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   42.244748] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected]
[   42.244751] cx88[0]: TV tuner type 76, Radio tuner type -1
[   42.258376] usb 1-2: reset full speed USB device using uhci_hcd and address 5
[   42.258420] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   42.404335] lirc_dev: lirc_register_plugin: sample_rate: 0
[   42.413518] lirc_mceusb2[5]: SMK eHome Infrared Transceiver on usb1:5
[   42.413556] usbcore: registered new interface driver lirc_mceusb2
[   42.738169] tuner' 1-0064: chip found @ 0xc8 (cx88[0])
[   42.738826] xc5000: Successfully identified at address 0x64
[   42.738828] xc5000: Firmware has not been loaded previously
[   42.738831] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   42.780863] xc5000: firmware read 12332 bytes.
[   42.780866] xc5000: firmware upload
[   42.780868] cx88[0]: Calling XC5000 callback
[   42.799624] cx2388x alsa driver version 0.0.6 loaded
[   47.263170] input: cx88 IR (Pinnacle PCTV HD 800i) as /class/input/input4
[   47.263298] cx88[0]/2: cx2388x 8802 Driver Manager
[   47.263319] ACPI: PCI Interrupt 0000:04:04.2[A] -> GSI 17 (level, low) -> IRQ 23
[   47.263327] cx88[0]/2: found at 0000:04:04.2, rev: 5, irq: 23, latency: 64, mmio: 0xdc000000
[   47.263478] ACPI: PCI Interrupt 0000:04:04.0[A] -> GSI 17 (level, low) -> IRQ 23
[   47.263486] cx88[0]/0: found at 0000:04:04.0, rev: 5, irq: 23, latency: 64, mmio: 0xde000000
[   47.263660] cx88[0]/0: registered device video0 [v4l2]
[   47.263788] cx88[0]/0: registered device vbi0
[   47.328061] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   47.328065] cx88/2: registering cx8802 driver, type: dvb access: shared
[   47.328069] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   47.328072] cx88[0]/2: cx2388x based DVB/ATSC card
[   47.381232] xc5000: Successfully identified at address 0x64
[   47.381235] xc5000: Firmware has been loaded previously
[   47.382018] DVB: registering new adapter (cx88[0])
[   47.382021] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   49.352060] ACPI: PCI Interrupt 0000:80:01.0[A] -> GSI 17 (level, low) -> IRQ 23


from the look of everything it should be working correctly

but whenever i tune a channel i get the video for about two seconds, and then it goes out... its starting to frustrate me, it looks as if the channel is demodulating itself right after initializing... whenever i change channels the same thing 1 second of  signal and then  static then nothing

My exact procedure...
installed mythbuntu, went through mythbuntu setup (all except configuring the backend, then i downloaded the v4l-dvb via mercurial, ran a make, ran a make install, downloaded and extracted and copied xc5000 firmware to my firmware library, rebooted my system for good measure, and then  configured my capture cards, my sources, channel grabber (schedulesdirect) , yadda, yadda, and closed the backend server and ran mythfilldatabase... 

ran the frontend and went to watch tv, and boom problems... 

My sysconfig incase anyone is interested

OS: Mythbuntu 32bit
Video: Nvidia Geforce 7300 LE
Audio (Realtek Onboard 5.1 HD Audio Surround Sound)
Processor: AMD Sempron 3600+
Memory: Patriot 1GB 667Mhz DDR2
Tuner: Pinnacle PCTV HD (800i)

Programs that i've tried that suffer trouble with the PCTV HD Tuner:

TvTime : Same as Mythtv
Mplaye: "DVB NOT CONFIGURED
VLC: DVB NOT CONFIGURED
Xine: Same as Mythtv

---

### Post by bawilson2 on 2008-03-04
> **Nicezia said:**
> card setup as follows, 

Tuner 1 Analog (use /dev/video0)
Capture 2 (use DVB Samsungblah blah.

now tell me how you got it working with other programs... i haven't gotten it working at all yet

I tried compiling the v4l-dvb, did a make and make install, everything with swimmgly checked my dmesg and got this

[   42.244672] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   42.244748] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected]
[   42.244751] cx88[0]: TV tuner type 76, Radio tuner type -1
[   42.258376] usb 1-2: reset full speed USB device using uhci_hcd and address 5
[   42.258420] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   42.404335] lirc_dev: lirc_register_plugin: sample_rate: 0
[   42.413518] lirc_mceusb2[5]: SMK eHome Infrared Transceiver on usb1:5
[   42.413556] usbcore: registered new interface driver lirc_mceusb2
[   42.738169] tuner' 1-0064: chip found @ 0xc8 (cx88[0])
[   42.738826] xc5000: Successfully identified at address 0x64
[   42.738828] xc5000: Firmware has not been loaded previously
[   42.738831] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   42.780863] xc5000: firmware read 12332 bytes.
[   42.780866] xc5000: firmware upload
[   42.780868] cx88[0]: Calling XC5000 callback
[   42.799624] cx2388x alsa driver version 0.0.6 loaded
[   47.263170] input: cx88 IR (Pinnacle PCTV HD 800i) as /class/input/input4
[   47.263298] cx88[0]/2: cx2388x 8802 Driver Manager
[   47.263319] ACPI: PCI Interrupt 0000:04:04.2[A] -> GSI 17 (level, low) -> IRQ 23
[   47.263327] cx88[0]/2: found at 0000:04:04.2, rev: 5, irq: 23, latency: 64, mmio: 0xdc000000
[   47.263478] ACPI: PCI Interrupt 0000:04:04.0[A] -> GSI 17 (level, low) -> IRQ 23
[   47.263486] cx88[0]/0: found at 0000:04:04.0, rev: 5, irq: 23, latency: 64, mmio: 0xde000000
[   47.263660] cx88[0]/0: registered device video0 [v4l2]
[   47.263788] cx88[0]/0: registered device vbi0
[   47.328061] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   47.328065] cx88/2: registering cx8802 driver, type: dvb access: shared
[   47.328069] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   47.328072] cx88[0]/2: cx2388x based DVB/ATSC card
[   47.381232] xc5000: Successfully identified at address 0x64
[   47.381235] xc5000: Firmware has been loaded previously
[   47.382018] DVB: registering new adapter (cx88[0])
[   47.382021] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   49.352060] ACPI: PCI Interrupt 0000:80:01.0[A] -> GSI 17 (level, low) -> IRQ 23


from the look of everything it should be working correctly

but whenever i tune a channel i get the video for about two seconds, and then it goes out... its starting to frustrate me, it looks as if the channel is demodulating itself right after initializing... whenever i change channels the same thing 1 second of  signal and then  static then nothing

My exact procedure...
installed mythbuntu, went through mythbuntu setup (all except configuring the backend, then i downloaded the v4l-dvb via mercurial, ran a make, ran a make install, downloaded and extracted and copied xc5000 firmware to my firmware library, rebooted my system for good measure, and then  configured my capture cards, my sources, channel grabber (schedulesdirect) , yadda, yadda, and closed the backend server and ran mythfilldatabase... 

ran the frontend and went to watch tv, and boom problems... 

My sysconfig incase anyone is interested

OS: Mythbuntu 32bit
Video: Nvidia Geforce 7300 LE
Audio (Realtek Onboard 5.1 HD Audio Surround Sound)
Processor: AMD Sempron 3600+
Memory: Patriot 1GB 667Mhz DDR2
Tuner: Pinnacle PCTV HD (800i)

Programs that i've tried that suffer trouble with the PCTV HD Tuner:

TvTime : Same as Mythtv
Mplaye: "DVB NOT CONFIGURED
VLC: DVB NOT CONFIGURED
Xine: Same as Mythtv

That's a different tuner than what I'm using.  The PCTV HD Pro Stick is using a Xceive xc3028ACQ for FM radio and analog signal and a  LG DT3303 for digital tuning.  I'm afraid I don't know what to do to help you.

---

### Post by teethdood on 2008-04-27
Hardy Heron 8.04.

I have followed the guides (i had to hardlinking some of the header files due to file not found errors), but got stuck with this message at the "make" level:
philip-laptop:/usr/src/v4l-dvb-kernel# make
make -C /usr/src/v4l-dvb-kernel/v4l 
make[1]: Entering directory `/usr/src/v4l-dvb-kernel/v4l'
creating symbolic links...
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/usr/src/v4l-dvb-kernel/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /usr/src/v4l-dvb-kernel/v4l/bttv-driver.o
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c: In function 'show_card':
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:172: warning: initialization from incompatible pointer type
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c: At top level:
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:3887: error: unknown field 'hardware' specified in initializer
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:3887: error: 'VID_HARDWARE_BT848' undeclared here (not in a function)
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:3896: error: unknown field 'hardware' specified in initializer
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:4042: error: unknown field 'hardware' specified in initializer
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c: In function 'bttv_register_video':
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:4637: warning: passing argument 1 of 'class_device_create_file' from incompatible pointer type
make[3]: *** [/usr/src/v4l-dvb-kernel/v4l/bttv-driver.o] Error 1
make[2]: *** [_module_/usr/src/v4l-dvb-kernel/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/v4l-dvb-kernel/v4l'
make: *** [all] Error 2

Any ideas on how to proceed? Thanks

---

### Post by bawilson2 on 2008-04-27
> **teethdood said:**
> Hardy Heron 8.04.

I have followed the guides (i had to hardlinking some of the header files due to file not found errors), but got stuck with this message at the "make" level:
philip-laptop:/usr/src/v4l-dvb-kernel# make
make -C /usr/src/v4l-dvb-kernel/v4l 
make[1]: Entering directory `/usr/src/v4l-dvb-kernel/v4l'
creating symbolic links...
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/usr/src/v4l-dvb-kernel/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /usr/src/v4l-dvb-kernel/v4l/bttv-driver.o
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c: In function 'show_card':
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:172: warning: initialization from incompatible pointer type
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c: At top level:
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:3887: error: unknown field 'hardware' specified in initializer
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:3887: error: 'VID_HARDWARE_BT848' undeclared here (not in a function)
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:3896: error: unknown field 'hardware' specified in initializer
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:4042: error: unknown field 'hardware' specified in initializer
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c: In function 'bttv_register_video':
/usr/src/v4l-dvb-kernel/v4l/bttv-driver.c:4637: warning: passing argument 1 of 'class_device_create_file' from incompatible pointer type
make[3]: *** [/usr/src/v4l-dvb-kernel/v4l/bttv-driver.o] Error 1
make[2]: *** [_module_/usr/src/v4l-dvb-kernel/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/v4l-dvb-kernel/v4l'
make: *** [all] Error 2

Any ideas on how to proceed? Thanks

I tried doing the hard linking first and got similar errors.  I was able to get it to work using the patch described in this thread:

[http://ubuntuforums.org/showthread.php?t=740473](http://ubuntuforums.org/showthread.php?t=740473)

It adds an include path line to the v4l Makefile.  For what it's worth, the HVR-950 is the same digital tuner. You can use that other guide to get thing mostly working.  Good luck!

---

