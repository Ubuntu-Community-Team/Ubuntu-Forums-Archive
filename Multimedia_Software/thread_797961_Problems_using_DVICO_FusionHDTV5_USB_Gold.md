---
title: "Problems using DVICO FusionHDTV5 USB Gold"
date: 2008-05-17
forum: Multimedia Software
---

### Post by toddk111 on 2008-05-17
Hello,

I already posted this issue a while ago but since then I have re-installed Ubuntu.  I have an AMD 64x2 4200+ with 3GB RAM running Ubuntu 8.04 64 with Kaffeine 0.86. I have 2 DVICO FusionHDTV5 USB Gold tuners. I'm using a QAM ATSC cable source and I'm able to tune channels with Kaffeine but they pixelate a lot and the recorded files show a lot of errors when I run them through stream fix in VideoRedo. 

In Windows 2000, I don't have any picture quality problems and I don't get errors in my recorded files so I don't think it is a problem with my tuners or my signal. Would please tell me what I can do to improve the quality of my recordings? Are there any settings that I need to change? Is there a better application for simple multi-tuner timed recordings? (I don't want to use a big application like MythTV).


Previously, I was told I need to add:
> options cx23885 card=4

to /etc/modprobe.d/options.

But my encoder is a Conexant CX25843.  I would appreciate any ideas on how to get this working smoothly.

Thanks,
Todd

P.S. When I type dmesg, I get:

> [   39.105812] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'

[   39.169464] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in cold state, will try to load a firmware

[   39.171129] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'

[   39.201932] usb 2-3: USB disconnect, address 3

[   39.201977] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.

[   39.328028] usb 2-4: USB disconnect, address 4

[   39.332044] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.

[   39.459949] usbcore: registered new interface driver dvb_usb_cxusb

[   40.114533] loop: module loaded

[   40.141235] lp0: using parport0 (interrupt-driven).

[   40.247852] Adding 3903784k swap on /dev/sda2.  Priority:-1 extents:1 across:3903784k

[   40.787998] EXT3 FS on sda4, internal journal

[   40.989660] usb 2-3: new high speed USB device using ehci_hcd and address 7

[   41.123027] usb 2-3: configuration #1 chosen from 1 choice

[   41.124781] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in warm state.

[   41.124961] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.

[   41.155944] DVB: registering new adapter (DViCO FusionHDTV5 USB Gold)

[   41.206884] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...

[   41.225925] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:02.1/usb2/2-3/input/input7

[   41.262466] dvb-usb: schedule remote query interval to 100 msecs.

[   41.262472] dvb-usb: DViCO FusionHDTV5 USB Gold successfully initialized and connected.

[   41.502277] usb 2-4: new high speed USB device using ehci_hcd and address 8

[   41.635510] usb 2-4: configuration #1 chosen from 1 choice

[   41.635919] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in warm state.

[   41.636061] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.

[   41.667035] DVB: registering new adapter (DViCO FusionHDTV5 USB Gold)

[   41.668888] DVB: registering frontend 1 (LG Electronics LGDT3303 VSB/QAM Frontend)...

[   41.670208] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:02.1/usb2/2-4/input/input8

[   41.726098] dvb-usb: schedule remote query interval to 100 msecs.

[   41.726106] dvb-usb: DViCO FusionHDTV5 USB Gold successfully initialized and connected.

[   42.055807] ip_tables: (C) 2000-2006 Netfilter Core Team

[   42.450502] No dock devices found.


When I type lsusb, I get:
> Bus 002 Device 008: ID 0fe9:d501 DVICO 
Bus 002 Device 007: ID 0fe9:d501 DVICO 
Bus 002 Device 006: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 001 Device 002: ID 046e:5250 Behavior Tech. Computer Corp. 
Bus 001 Device 001: ID 0000:0000  

---

### Post by toddk111 on 2008-05-23
I'm still having this problem.  Does anyone have any ideas of what I can do?

Thanks,
Todd

---

### Post by Erlander on 2008-05-23
I have a DVICO usb DVb tuner.  Not the same as yours but similar.  Looking at you dmesg I think it is OK.

When having the sort of problems you are experiencing I look at video card drivers.  The display card really has to work hard to render tv footage.  A good high performance card is needed with up to date drivers.

My NVidia 8600GT with the NVidia restricted drivers struggles for a few seconds when I switch to a high definition channel.

Hope this is of help.

Rob

---

### Post by toddk111 on 2008-05-24
Thanks for the response Erlander!
Unfortunately, I don't think that the video rendering is the problem because the recordings are made via timer.  So I'm not even watching it (or having the video card render the picture) when it records.  Any other ideas would be greatly appreciated.
Thanks,
Todd

---

### Post by Erlander on 2008-05-24
I'm no expert on this but for others to help you will need to give more detail on your hardware and whether you are capturing NTSC or DVB etc.

With DVB the actual recording of the video stream uses very little of the pc's resources.  Its the playback that requires a good graphics card and video acceleration so it still could be your card or drivers.

Rob

---

### Post by xc3RnbFO8P on 2008-05-24
Did you try to tune direct, without the QAM ATSC cable source?

---

### Post by toddk111 on 2008-06-07
My video card is on board nvidia 6150SE.  I'm recording ATSC QAM and we can't pick up any over the air signals in my area so its not possible to test record an ATSC OTA signal.  Any thoughts would be appreciated.
Thanks,
Todd

---

### Post by xc3RnbFO8P on 2008-06-07
This pixelate and error is pointing to a weak signal,
I would check the cable from  ATSC QAM to your tuner, if you haven't.
How long is this cabel?

---

### Post by toddk111 on 2008-06-07
My signal is strong.  It shows as 99% in DVICO's Windows application and I have no errors or problems recording in Windows but I'd like to use Linux instead.

---

### Post by xc3RnbFO8P on 2008-06-07
Lets say signal is OK.
Sometimes this happens when USB tuner get to warm.

---

### Post by toddk111 on 2008-06-12
If we agree that the signal is OK...then do you have any ideas of what the problem would be?

---

### Post by flamaest on 2010-06-12
Hi All,

I was wondering if someone could review the Ubuntu dmesg and lsmod output below to see if you spot anything wrong with my DViCO FusionHDTV5 USB Gold tuners. 

I am running Mythbuntu 10.04 and have tried setting it up very carefully using multiple setup instructions on wiki's, forums, and websites. This is my first time using MythTV.

It appears both my DVICO tuners are loading OK since I can see the blue lights turned on from the bottom. 

Issue: I cannot get MythTV to scan for any channels or watch TV.

I tried scanning channels with both tuners, multiple cable lines, selecting multiple cable signal fomrats, nothing. If I plug in the cable line into a TV, all is well on the TV.

Does anything jump out at you from below?

please help, thanks.


DMESG:


[ 5264.788028] usb 2-4: new high speed USB device using ehci_hcd and address 9
[ 5264.920618] usb 2-4: configuration #1 chosen from 1 choice
[ 5264.920941] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in cold state, will try to load a firmware
[ 5264.920955] usb 2-4: firmware: requesting dvb-usb-bluebird-01.fw
[ 5264.924937] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'
[ 5265.027223] usb 2-4: USB disconnect, address 9
[ 5265.027336] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[ 5266.812028] usb 2-4: new high speed USB device using ehci_hcd and address 10
[ 5266.945650] usb 2-4: configuration #1 chosen from 1 choice
[ 5266.945951] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in warm state.
[ 5266.946434] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 5266.977149] DVB: registering new adapter (DViCO FusionHDTV5 USB Gold)
[ 5266.982721] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[ 5266.983955] tuner-simple 1-0061: creating new instance
[ 5266.983967] tuner-simple 1-0061: type set to 64 (LG TDVS-H06xF)
[ 5266.984707] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/input/input7
[ 5266.984874] dvb-usb: schedule remote query interval to 100 msecs.
[ 5266.984888] dvb-usb: DViCO FusionHDTV5 USB Gold successfully initialized and connected.
[ 5302.796028] usb 2-3: new high speed USB device using ehci_hcd and address 11
[ 5302.928659] usb 2-3: configuration #1 chosen from 1 choice
[ 5302.928942] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in cold state, will try to load a firmware
[ 5302.928954] usb 2-3: firmware: requesting dvb-usb-bluebird-01.fw
[ 5302.932864] dvb-usb: downloading firmware from file 'dvb-usb-bluebird-01.fw'
[ 5303.033739] usb 2-3: USB disconnect, address 11
[ 5303.036972] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[ 5304.820027] usb 2-3: new high speed USB device using ehci_hcd and address 12
[ 5304.953660] usb 2-3: configuration #1 chosen from 1 choice
[ 5304.953972] dvb-usb: found a 'DViCO FusionHDTV5 USB Gold' in warm state.
[ 5304.954457] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 5304.985142] DVB: registering new adapter (DViCO FusionHDTV5 USB Gold)
[ 5304.989216] DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[ 5304.990469] tuner-simple 2-0061: creating new instance
[ 5304.990482] tuner-simple 2-0061: type set to 64 (LG TDVS-H06xF)
[ 5304.991189] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/input/input8
[ 5304.991412] dvb-usb: schedule remote query interval to 100 msecs.
[ 5304.991426] dvb-usb: DViCO FusionHDTV5 USB Gold successfully initialized and connected.





LSMOD:

Module                  Size  Used by
videodev               34361  0 
v4l1_compat            13251  1 videodev
tuner_simple           13577  2 
tuner_types            14233  1 tuner_simple
lgdt330x                7570  2 
dvb_usb_cxusb          36437  0 
dib7000p               15988  1 dvb_usb_cxusb
dibx000_common          2974  1 dib7000p
dvb_usb                14457  1 dvb_usb_cxusb
dvb_core               86142  3 lgdt330x,dib7000p,dvb_usb
dib0070                 7653  1 dvb_usb_cxusb
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  282354  2 
drm_kms_helper         29297  1 i915
drm                   162471  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
lp                      7028  0 
video                  17375  1 i915
parport                32635  1 lp
output                  1871  1 video
intel_agp              24177  2 i915
joydev                  8708  0 
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
usbhid                 36110  0 
hid                    67032  1 usbhid
usb_storage            39425  1 
ahci                   32008  2 
e1000e                119856  0 

LSUSB:

Bus 008 Device 003: ID 062a:6728 Creative Labs 
Bus 008 Device 002: ID 413c:2101 Dell Computer Corp. SmartCard Reader Keyboard
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 012: ID 0fe9:d501 DVICO 
Bus 002 Device 010: ID 0fe9:d501 DVICO 
Bus 002 Device 002: ID 1005:b155 Apacer Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Thanks,
Fabian.

---

