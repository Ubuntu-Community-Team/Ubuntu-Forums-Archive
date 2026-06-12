---
title: "Streamzap remote not working on Mythbuntu 9.04?"
date: 2009-04-25
forum: Mythbuntu
---

### Post by andrewc6l on 2009-04-25
I'm running into a problem with my Streamzap PC remote on Mythbuntu 9.04. I'm not sure where I should be looking.

1. The device is there. (sudo cat /dev/lirc0 shows output)

2. I can see pulses (sudo mode2 -d /dev/lirc0 gives me a reasonable output)

3. sudo irw shows nothing.

4. I can't seem to find the right input device in /proc/bus/input/devices:

```

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A03:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=04b3 Product=310c Version=0111
N: Name="USB Optical Mouse"
P: Phys=usb-0000:00:1d.3-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=054c Product=005c Version=0100
N: Name="Sony Computer Entertainment Inc. SCE USB Keyboard"
P: Phys=usb-0000:00:1d.3-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1.1/5-1.1:1.0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

```

5. I think my dmesg looks OK:

```

[ 1768.871084] lirc_dev: IR Remote Control driver registered, major 61 
[ 1768.895637] lirc_streamzap[-1]: Streamzap, Inc. Streamzap Remote Control on usb2:3 attached
[ 1768.895642] lirc_dev: lirc_register_plugin: sample_rate: 0
[ 1768.895757] usbcore: registered new interface driver lirc_streamzap
[ 1768.895764] lirc_streamzap $Revision: 1.27 $ registered
[ 3645.520047] usb 2-1: USB disconnect, address 3
[ 3645.520359] lirc_streamzap[0]: disconnected
[ 3651.948016] usb 2-1: new low speed USB device using uhci_hcd and address 4
[ 3652.127412] usb 2-1: configuration #1 chosen from 1 choice
[ 3652.160398] lirc_streamzap[-1]: Streamzap, Inc. Streamzap Remote Control on usb2:4 attached
[ 3652.160404] lirc_dev: lirc_register_plugin: sample_rate: 0

```

6. And of course, when I run mythfrontend, I can't control it with the remote.

I had this working on 8.04 using the same remote, so I don't think it's hardware. Does anyone have any ideas?

[edit] Running lircd --driver=streamzap results in:
$ lircd --driver=streamzap
Driver `streamzap' not supported.

[edit] ... but my 8.04 box also says streamzap not supported.

---

### Post by andrewc6l on 2009-04-30
On a hunch, I tried recording a new lircd.conf file using irrecord. Success! Now irw is working. I'll post my file here after I tweak it a bit.

---

### Post by andrewc6l on 2009-04-30
:oops: I've discovered my problem, and it's embarrassing. I was using the wrong remote! When I switched to the Streamzap remote, things started working.

I guess the good news is that I learned I can use the Streamzap remote receiver and irrecord to interface to any remote after the buttons wear out on this one.

---

### Post by graysky on 2009-11-27
@Andrew - I think that have the same remote you do (USB Streamzap) trying to get it working properly with lirc, but not under mythbuntu - it's a different distro (Arch). I found this thread from googling.

Is that driver=zapstream needed at all?  I too get that it's not supported:

```
# /etc/rc.d/lircd start
:: Starting LIRC Daemon     [BUSY] 

Driver `streamzap' not supported.
Supported drivers:
	accent
	alsa_usb
	asusdh
	atilibusb
	audio_alsa
	awlibusb
	bte
	bw6130
	commandir
	creative
	creative_infracd
	default
	devinput
	dsp
	dvico
	ea65
	ftdi
	i2cuser
	irlink
	livedrive_midi
	livedrive_seq
	logitech
	macmini
	mp3anywhere
	mplay
	mouseremote
	mouseremote_ps2
	null
	pcmak
	pinsys
	pixelview
	samsung
	sb0540
	silitek
	tira
	udp
	uirt2
	uirt2_raw
	usb_uirt_raw
	usbx          [FAIL]
```

Link to my post: [http://bbs.archlinux.org/viewtopic.php?id=85661](http://bbs.archlinux.org/viewtopic.php?id=85661)

EDIT: turns out this isn't needed at all.  My problem was low batts in the remote.

---

