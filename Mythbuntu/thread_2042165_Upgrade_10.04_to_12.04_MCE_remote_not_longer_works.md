---
title: "Upgrade 10.04 to 12.04 MCE remote not longer works"
date: 2012-08-14
forum: Mythbuntu
---

### Post by s_g_robertson on 2012-08-14
Hello,

I've recently upgraded from 10.04 to 12.04 (By going through each intermediate update as I had wrong option set) and my remote has stopped working.  This was working in 10.04 both for Myth and irexec to allow (re)starting of the frontend.

Some useful(??) outputs below.

Any suggestions?  
Thanks
Stephen

There is no output from irw

stephen@bressay:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Loading LIRC modules                                                  [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ]


dmesg output:
[   29.798688] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.9 loaded
[   29.800334] cx88[0]: subsystem: 0070:9002, board: Hauppauge Nova-T DVB-T [card=18,autodetected], frontend(s): 1
[   29.800336] cx88[0]: TV tuner type 4, Radio tuner type -1
[   29.805820] cx88/0: cx2388x v4l2 driver version 0.0.9 loaded
[   29.958660] tveeprom 1-0050: Hauppauge model 90002, rev C176, serial# 47854
[   29.958664] tveeprom 1-0050: MAC address is 00:0d:fe:00:ba:ee
[   29.958666] tveeprom 1-0050: tuner model is Thompson DTT7592 (idx 76, type 4)
[   29.958668] tveeprom 1-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   29.958670] tveeprom 1-0050: audio processor is None (idx 0)
[   29.958672] tveeprom 1-0050: decoder processor is CX882 (idx 25)
[   29.958674] tveeprom 1-0050: has no radio, has IR receiver, has no IR transmitter
[   29.958675] cx88[0]: hauppauge eeprom: model=90002
[   30.119139] IR NEC protocol handler initialized
[   30.271676] IR RC5(x) protocol handler initialized
[   30.307584] cx2388x alsa driver version 0.0.9 loaded
[   30.549584] IR RC6 protocol handler initialized
[   30.582367] IR JVC protocol handler initialized
[   31.022711] FS-Cache: Netfs 'nfs' registered for caching
[   31.051941] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   31.051985] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   31.052014] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   31.146156] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   31.146262] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   31.146350] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   31.146437] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   31.146529] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   31.260009] Registered IR keymap rc-hauppauge
[   31.260151] input: cx88 IR (Hauppauge Nova-T DVB-T as /devices/pci0000:00/0000:00:1e.0/0000:04:00.2/rc/rc0/input10
[   31.260206] rc0: cx88 IR (Hauppauge Nova-T DVB-T as /devices/pci0000:00/0000:00:1e.0/0000:04:00.2/rc/rc0
[   31.260230] cx88[0]/2: cx2388x 8802 Driver Manager
[   31.260241] cx88-mpeg driver manager 0000:04:00.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   31.260248] cx88[0]/2: found at 0000:04:00.2, rev: 5, irq: 19, latency: 64, mmio: 0xfc000000
[   31.261843] cx88[1]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   31.261845] cx88[1]: TV tuner type -1, Radio tuner type -1
[   31.319858] IR Sony protocol handler initialized
[   31.362636] input: MCE IR Keyboard/Mouse (cx88xx) as /devices/virtual/input/input11
[   31.362700] IR MCE Keyboard/mouse protocol handler initialized
[   31.757728] lirc_dev: IR Remote Control driver registered, major 250 
[   31.765596] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
[   31.765598] IR LIRC bridge handler initialized
[   31.816983] i2c-core: driver [tuner] using legacy suspend method
[   31.816985] i2c-core: driver [tuner] using legacy resume method
[   31.871664] tveeprom 2-0050: Hauppauge model 69100, rev B2C3, serial# 6222880
[   31.871667] tveeprom 2-0050: MAC address is 00:0d:fe:5e:f4:20
[   31.871669] tveeprom 2-0050: tuner model is Conexant CX24118A (idx 123, type 4)
[   31.871671] tveeprom 2-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   31.871673] tveeprom 2-0050: audio processor is None (idx 0)
[   31.871675] tveeprom 2-0050: decoder processor is CX882 (idx 25)
[   31.871677] tveeprom 2-0050: has no radio, has IR receiver, has no IR transmitter
[   31.871678] cx88[1]: hauppauge eeprom: model=69100
[   31.874031] Registered IR keymap rc-hauppauge
[   31.874347] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:1e.0/0000:04:02.2/rc/rc1/input12
[   31.874925] rc1: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:1e.0/0000:04:02.2/rc/rc1
[   31.876079] input: MCE IR Keyboard/Mouse (cx88xx) as /devices/virtual/input/input13
[   31.877244] rc rc1: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 1
[   31.877247] cx88[1]/2: cx2388x 8802 Driver Manager
[   31.877266] cx88-mpeg driver manager 0000:04:02.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   31.877273] cx88[1]/2: found at 0000:04:02.2, rev: 5, irq: 17, latency: 64, mmio: 0xf9000000
[   31.877320] cx8800 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   31.877325] cx88[0]/0: found at 0000:04:00.0, rev: 5, irq: 19, latency: 64, mmio: 0xfb000000
[   31.877443] cx88[0]/0: registered device video0 [v4l2]
[   31.877519] cx88[0]/0: registered device vbi0
[   31.877531] cx8800 0000:04:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   31.877535] cx88[1]/0: found at 0000:04:02.0, rev: 5, irq: 17, latency: 64, mmio: 0xf7000000
[   31.877664] cx88[1]/0: registered device video1 [v4l2]
[   31.878015] cx88[1]/0: registered device vbi1
[   31.878061] cx88_audio 0000:04:02.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   31.878083] cx88[1]/1: CX88x/0: ALSA support for cx2388x boards
[   31.995923] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   32.388017] Registered IR keymap rc-rc6-mce
[   32.388156] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/rc/rc2/input14
[   32.388210] rc2: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/rc/rc2
[   32.388282] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input15
[   32.388364] rc rc2: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 2
[   32.612026] mceusb 2-2:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[   32.612031] mceusb 2-2:1.0: 2 tx ports (0x1 cabled) and 2 rx sensors (0x1 active)
[   32.612074] usbcore: registered new interface driver mceusb


# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
REMOTE_SOCKET=""
TRANSMITTER_SOCKET=""

---

### Post by Lester_Burnham on 2012-08-14
Hi,

Does running irw in a terminal and pressing a few buttons give you anything?
If so, I'd go to mythbuntu control centre and re-select your remote, then tick the option to generate mappings and see what happens.
Otherwise you will need to look at your ~/.lirc/mythtv file and confirm button names are correct in conjunction with irw..

Lester

---

### Post by s_g_robertson on 2012-08-14
No I don't get anything from irw.

I'm wondering whether it is something to do with there being three potential receivers detected and the wrong one is being piped to lirc?

Stephen

---

### Post by Lester_Burnham on 2012-08-14
Hi,

Yeah, looking above, there are a few. Looks like they're all using kernel IR, as listed at the end of your dmesg.
Ir keymap rc-rc6-mce

You need to wait for the smart people,  I'm pretty sure there is an easy fix, possibly made harder by 3 devices.

Lester

---

