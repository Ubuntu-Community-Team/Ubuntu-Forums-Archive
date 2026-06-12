---
title: "remotes oh I need help on remotes"
date: 2011-02-28
forum: Mythbuntu
---

### Post by Cuppa-Chino on 2011-02-28
Hi

after I had to sell my beloved Antec Veris (as the built in cabinets are too small) I am now pondering what to do about remotes:

I have flying about:
Hauppage HVR 1300 PCI with "grey Hauppauge" remote
Pinnacle PCTV nanoStick 73e SE Solo (without remote)
HP MCE USB receiver and remote

and I cannot get anything to work properly

a) MCE is only recognised by plugging in and out once the computer, then only works partially no idea why
b) HVR remote works fine to turn the computer on when off (well kind off it starts the computer I have no idea what kind of state the "main light on but not moving means" -- again cannot get that to work later on
c) nanostick mine came without the remote and cannot get my harmony remote to contact it

what should I do? I am close to either
a) ordering a remote that actually is a keyboard like those 2.4ghz remotes - but is there one that will allow me turn the computer on? I mean just like a wake up on remote usb keyboard ?
b) ordering the simple veris remote ?

any other ideas as you can see I would consider ordering something new.

also anyone tried the pctv dvb-t2 stick and or the dvb-t2 pci express card?

---

### Post by Cuppa-Chino on 2011-04-20
hi half bump and half update on what is currently in the machine:

I have removed the Hauppauge card, pulled the Pinnacle Stick (now in my laptop) and bought a Peak dual tuner card:

**PEAK DVB-T Dual tuner PCI (221544AGPK) **

which according to the Linux TV wiki is identical to the **KWorld DVB-T PC160-2T** and the **Leadtek DTV2000DS**.

Now the card works right out of the box, both tuners and all. 

I have done a fresh Natty beta 2 install last night and am just trying to get a remote working.

Has anyone been able to configure the remote?

Also I am still struggling with an USB MCE remote receiver I have lying around, it just does not get initialised during bootup, I can get it to work if I plug it in and out while the computer is running but is not much help of course any ideas?

---

### Post by Grenage on 2011-04-20
I assume that myth uses Lirc; is the process running when you turn on the PC?

---

### Post by ian dobson on 2011-04-20
Hi,

What happens if you go to the terminal and run irw then press afew buttons on the remote?

Regards
Ian Dobson

---

### Post by Cuppa-Chino on 2011-05-10
sorry for delay but no dice with IRW now that the mythbox is back on internet let me dump some output here

current setup is installed the Peak Dual Tuner card (which works very reliable) and I still cannot get the remote to work

the MCE remote still only works on when I plug it into the computer after it has booted (note not in the dmesg or lsinput below)

dmesg:
```
[    2.310280] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    2.440338] firewire_core: created device fw0: GUID 001e8c00018b9668, S400
[    2.600311] input: 2.4G USB RF KeyBoard as /devices/pci0000:00/0000:00:02.0/usb4/4-2/4-2:1.0/input/input2
[    2.600417] generic-usb 0003:05AF:0408.0001: input,hidraw0: USB HID v1.10 Keyboard [2.4G USB RF KeyBoard] on usb-0000:00:02.0-2/input0
[    2.607743] input: 2.4G USB RF KeyBoard as /devices/pci0000:00/0000:00:02.0/usb4/4-2/4-2:1.1/input/input3
[    2.607858] generic-usb 0003:05AF:0408.0002: input,hidraw1: USB HID v1.10 Mouse [2.4G USB RF KeyBoard] on usb-0000:00:02.0-2/input1
[    2.623581] input: 2.4G USB RF KeyBoard as /devices/pci0000:00/0000:00:02.0/usb4/4-2/4-2:1.2/input/input4
[    2.623740] generic-usb 0003:05AF:0408.0003: input,hiddev0,hidraw2: USB HID v1.10 Device [2.4G USB RF KeyBoard] on usb-0000:00:02.0-2/input2
[    2.623762] usbcore: registered new interface driver usbhid
[    2.623764] usbhid: USB HID core driver
[    2.680238] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    2.775424] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.302957] scsi 8:0:0:0: Direct-Access     Generic                   6000 PQ: 0 ANSI: 0 CCS
[    3.303553] sd 8:0:0:0: Attached scsi generic sg3 type 0
[    3.306438] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[   11.611974] Adding 5455868k swap on /dev/sda6.  Priority:-1 extents:1 across:5455868k 
[   11.647117] <30>udev[430]: starting version 167
[   11.708105] lp: driver loaded but no devices found
[   11.757444] i2c i2c-0: nForce2 SMBus adapter at 0x600
[   11.757450] ACPI: resource nForce2_smbus [io  0x0700-0x073f] conflicts with ACPI region SM00 [io 0x700-0x73f]
[   11.757452] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.833373] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[   11.835312] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:12/LNXVIDEO:00/input/input5
[   11.835413] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
...
[   11.954257] MCE: In-kernel MCE decoding enabled.
...
[   12.257419] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   12.257424] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   12.735197] IR NEC protocol handler initialized
[   12.737682] IR RC5(x) protocol handler initialized
[   12.740231] IR RC6 protocol handler initialized
[   12.742877] IR JVC protocol handler initialized
[   12.745427] IR Sony protocol handler initialized
[   12.749675] lirc_dev: IR Remote Control driver registered, major 249 
[   12.751768] IR LIRC bridge handler initialized
[   12.950499] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   12.950506] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   12.950515] nvidia 0000:02:00.0: setting latency timer to 64
...
[   13.548354] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in cold state, will try to load a firmware
[   13.588840] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   13.697270] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in warm state.
[   13.697864] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.698241] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
[   13.814196] af9013: firmware version:4.95.0.0
[   13.822887] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   13.911686] Ending clean XFS mount for filesystem: sda7
[   13.946694] tda18271 1-00c0: creating new instance
[   13.954528] TDA18271HD/C2 detected @ 1-00c0
[   14.052549] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   14.318573] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   14.319117] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
...
[   15.062118] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   15.065466] af9013: firmware version:4.95.0.0
[   15.076851] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
[   15.077845] tda18271 2-00c0: creating new instance
[   15.082711] TDA18271HD/C2 detected @ 2-00c0
[   15.479329] Registered IR keymap rc-empty
[   15.479434] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:07.2/usb3/3-1/rc/rc0/input6
[   15.479510] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:07.2/usb3/3-1/rc/rc0
[   15.479513] dvb-usb: schedule remote query interval to 500 msecs.
[   15.479517] dvb-usb: KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T) successfully initialized and connected.
[   15.489105] usbcore: registered new interface driver dvb_usb_af9015
...
[   22.100949] tda18271: performing RF tracking filter calibration
[   27.441668] tda18271: RF tracking filter calibration complete
[   28.155009] tda18271: performing RF tracking filter calibration
[   34.791797] tda18271: RF tracking filter calibration complete

```

lsinput:
```
sudo lsinput
[sudo] password for xxx: 
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_USB
   vendor  : 0x5af
   product : 0x408
   version : 272
   name    : "2.4G USB RF KeyBoard"
   phys    : "usb-0000:00:02.0-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event3
   bustype : BUS_USB
   vendor  : 0x5af
   product : 0x408
   version : 272
   name    : "2.4G USB RF KeyBoard"
   phys    : "usb-0000:00:02.0-2/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_MSC

/dev/input/event4
   bustype : BUS_USB
   vendor  : 0x5af
   product : 0x408
   version : 272
   name    : "2.4G USB RF KeyBoard"
   phys    : "usb-0000:00:02.0-2/input2"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC

/dev/input/event5
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event6
   bustype : BUS_USB
   vendor  : 0x1b80
   product : 0xc160
   version : 512
   name    : "IR-receiver inside an USB DVB re"
   phys    : "usb-0000:01:07.2-1/ir0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_REP

```

lsmod
```
lsmod
Module                  Size  Used by
vesafb                 13761  1 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
tda18271               58548  2 
af9013                 27812  2 
dvb_usb_af9015         35242  52 
dvb_usb                24290  1 dvb_usb_af9015
dvb_core              110487  1 dvb_usb
xfs                   823190  2 
exportfs               12998  1 xfs
ir_lirc_codec          12898  0 
lirc_dev               19232  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
ir_nec_decoder         12546  0 
rc_core                26918  9 dvb_usb_af9015,dvb_usb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
nvidia              10709116  50 
snd_hda_intel          33211  0 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
psmouse                73535  0 
k8temp                 13016  0 
serio_raw              13166  0 
edac_core              53845  0 
edac_mce_amd           23464  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 37297  0 
video                  19438  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
asus_atk0110           17976  0 
i2c_nforce2            13058  0 
lp                     17825  0 
parport                46458  1 lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  5 
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
floppy                 74120  0 
r8169                  48022  0 
forcedeth              63555  0 
libahci                26642  1 ahci
crc_itu_t              12707  1 firewire_core
pata_amd               14130  0
```

the peak / kworld is supposedly identical to the leadtek and I have tried following these instructions [http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS#Remote_Control_Support_.282.29]("http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS#Remote_Control_Support_.282.29")

---

### Post by Cuppa-Chino on 2011-05-14
Cannot seem to get the peak card ir to work so have gone back to fiddling with the mce usb:

essentially this happens (tried it on a laptop running 11.04, desktop running 10.10 or 11.04)

MCE plugged during bootup lsusb does not show it
```
laptop:~$ lsusb 
Bus 002 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 0c45:6409 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

as soon as I unplug and replug the receiver it is recognised and works
```
laptop:~$ lsusb 
**Bus 002 Device 008: ID 0471:060c Philips (or NXP) Consumer Infrared Transceiver (HP)**
Bus 002 Device 007: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 0c45:6409 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

dmesg shows the "late recognition"
```
dmesg | grep usbcore
[    1.652044] usbcore: registered new interface driver usbfs
[    1.652052] usbcore: registered new interface driver hub
[    1.652073] usbcore: registered new device driver usb
[   14.514652] usbcore: registered new interface driver uvcvideo
[   14.705569] usbcore: registered new interface driver usbhid
[   15.019994] usbcore: registered new interface driver btusb
[ 1046.954294] usbcore: registered new interface driver mceusb

```


Ok now done another run of plugging unplugging:
dmesg


```
~$ dmesg | grep usb
[    1.652103] usbcore: registered new interface driver usbfs
[    1.652111] usbcore: registered new interface driver hub
[    1.652131] usbcore: registered new device driver usb
[    6.325674] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    6.595146] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    6.824818] usb 1-1.2: new high speed USB device using ehci_hcd and address 3
[    7.044391] usb 1-1.6: new full speed USB device using ehci_hcd and address 4
[    7.234028] usb 2-1.2: new full speed USB device using ehci_hcd and address 3
[B][    7.313860] usb 2-1.2: device descriptor read/64, error -32
[    7.503525] usb 2-1.2: device descriptor read/64, error -32
[    7.693142] usb 2-1.2: new full speed USB device using ehci_hcd and address 4
[    7.773040] usb 2-1.2: device descriptor read/64, error -32
[    7.962675] usb 2-1.2: device descriptor read/64, error -32
[    8.162240] usb 2-1.2: new full speed USB device using ehci_hcd and address 5
[    8.581249] usb 2-1.2: device not accepting address 5, error -32
[    8.661289] usb 2-1.2: new full speed USB device using ehci_hcd and address 6
[    9.080293] usb 2-1.2: device not accepting address 6, error -32[/B]
[    9.160314] usb 2-1.5: new full speed USB device using ehci_hcd and address 7
[   20.728066] usbcore: registered new interface driver btusb
[   20.829334] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input6
[   20.829537] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input7
[   20.829552] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.5/input0
[   20.829756] usbcore: registered new interface driver uvcvideo
[   20.831703] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/input/input8
[   20.831991] generic-usb 0003:046D:C52B.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.5/input1
[   20.834809] generic-usb 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.5/input2
[   20.834834] usbcore: registered new interface driver usbhid
[   20.834836] usbhid: USB HID core driver
[  431.138291] usbcore: registered new interface driver mceusb
[COLOR="Blue"][B][  704.811297] usb 2-1.2: new full speed USB device using ehci_hcd and address 8
[  704.980950] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:060c) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/rc/rc0/input13
[  704.981045] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:060c) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/rc/rc0
[  704.981192] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[  704.981642] mceusb 2-1.2:1.0: Registered   BB+ Dongle(e.d) on usb2:8[/B][/COLOR]

```

I think its the "device descriptor" that is preventing it to be booted up right....

I am still

---

