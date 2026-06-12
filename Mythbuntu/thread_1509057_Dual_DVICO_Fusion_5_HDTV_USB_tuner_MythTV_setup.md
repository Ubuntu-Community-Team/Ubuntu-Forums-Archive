---
title: "Dual DVICO Fusion 5 HDTV USB tuner MythTV setup"
date: 2010-06-13
forum: Mythbuntu
---

### Post by flamaest on 2010-06-13
Hi All,

I was wondering if someone could review the Ubuntu 10.04 dmesg and lsmod output below to see if you spot anything wrong with my DViCO FusionHDTV5 USB Gold tuners.

I am running Mythbuntu 10.04 and have tried setting it up very carefully using multiple setup instructions on wiki's, forums, and websites. This is my first time using MythTV.

It appears both my DVICO tuners are loading OK since I can see the blue lights turned on from the bottom.

Issue: I cannot get MythTV to scan for any channels or watch TV.

I tried scanning channels with both tuners, multiple cable lines, selecting multiple cable signal fomrats, nothing. If I plug in the cable line into a TV, all is well on the TV.

My zipcode is 95023 running on Charter cable. Any Myth cable settings help would be appreciated.

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

Module Size Used by
videodev 34361 0
v4l1_compat 13251 1 videodev
tuner_simple 13577 2
tuner_types 14233 1 tuner_simple
lgdt330x 7570 2
dvb_usb_cxusb 36437 0
dib7000p 15988 1 dvb_usb_cxusb
dibx000_common 2974 1 dib7000p
dvb_usb 14457 1 dvb_usb_cxusb
dvb_core 86142 3 lgdt330x,dib7000p,dvb_usb
dib0070 7653 1 dvb_usb_cxusb
fbcon 35102 71
tileblit 2031 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
vga16fb 11385 0
vgastate 8961 1 vga16fb
i915 282354 2
drm_kms_helper 29297 1 i915
drm 162471 3 i915,drm_kms_helper
i2c_algo_bit 5028 1 i915
lp 7028 0
video 17375 1 i915
parport 32635 1 lp
output 1871 1 video
intel_agp 24177 2 i915
joydev 8708 0
psmouse 63245 0
serio_raw 3978 0
agpgart 31724 2 drm,intel_agp
usbhid 36110 0
hid 67032 1 usbhid
usb_storage 39425 1
ahci 32008 2
e1000e 119856 0

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

