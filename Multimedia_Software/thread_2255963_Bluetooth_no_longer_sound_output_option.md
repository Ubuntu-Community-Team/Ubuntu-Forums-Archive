---
title: "Bluetooth no longer sound output option"
date: 2014-12-08
forum: Multimedia Software
---

### Post by Evil Wayz on 2014-12-08
I switched to Ubuntu because I couldn't get bluetooth to work at all in Mint.  I tried out 14.4 on a stick and bluetooth worked fine, and then I installed it, and it worked fine as well.  The only real problem was i had to re set up the device every time I wanted to use it, because It wouldn't connect unless it was pairing.  Today I did what I usually do, only now it pairs but there is no headset option in sound settings.  Device shows up as paired and connected.  SO if someone could help me figure out what the issue is here I would appreciate it.  Here are the messages I get from various commands:

lsusb
Bus 001 Device 010: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0

hciconfig --all

hci0:	Type: BR/EDR  Bus: USB
	BD Address: 5C:F3:70:60:9A:77  ACL MTU: 1021:8  SCO MTU: 64:1
	UP RUNNING PSCAN ISCAN 
	RX bytes:656387 acl:319 sco:0 events:91698 errors:0
	TX bytes:155539697 acl:182434 sco:0 commands:300 errors:0
	Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'ubuntu-0'
	Class: 0x740100
	Service Classes: Rendering, Object Transfer, Audio, Telephony
	Device Class: Computer, Uncategorized
	HCI Version: 4.0 (0x6)  Revision: 0x1000
	LMP Version: 4.0 (0x6)  Subversion: 0x220e
	Manufacturer: Broadcom Corporation (15)

dmesg | grep -i bluetooth

[   16.118143] Bluetooth: Core ver 2.17
[   16.118201] Bluetooth: HCI device and connection manager initialized
[   16.118582] Bluetooth: HCI socket layer initialized
[   16.118588] Bluetooth: L2CAP socket layer initialized
[   16.118598] Bluetooth: SCO socket layer initialized
[   16.365153] Bluetooth: can't load firmware, may not work correctly
[   19.456142] Bluetooth: RFCOMM TTY layer initialized
[   19.456161] Bluetooth: RFCOMM socket layer initialized
[   19.456171] Bluetooth: RFCOMM ver 1.11
[   19.584375] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.584380] Bluetooth: BNEP filters: protocol multicast
[   19.584395] Bluetooth: BNEP socket layer initialized

---

### Post by Evil Wayz on 2014-12-09
Ok removing blueman seems to have solved hte problem, but I still have to remove and re-add my headset everytime I want to use it.  Anyone know know why blueman would allow the device to pair but fail to stream, or why I can't just reconnect my headset instead of re-adding it everytime?

---

### Post by sandyd on 2014-12-10
Thread moved to *Multimedia*

---

### Post by Evil Wayz on 2014-12-17
I switched to Ubuntu 14.04.1 because I couldn't get Linux Mint 17 to work with my iogear gbu421 with Broadcom  BCM20702A0 chip.  I got a new fun problem though, I can pair my headset (Rocketfish rf-bthp02) and get the audio sink working just fine, until I restart the computer or turn off my headset.  Then, it won't reconnect.  I have to delete it from bluetooth, and add it again.  This is a pain.  I tried using bluetooth manager (blueman) from Ubuntu Software Center since that has a refresh/connect option in it's menu but then bluetooth doesn't work at all, I get a "stream failed" error when I try to start the service.  I then have to remove blueman and start over.  Has anyone experienced this, and if so, what do I do about it?  Or is my headset just too old?

---

### Post by mörgæs on 2014-12-17
Threads merged.
Please don't create multiple threads on the same or a closely related topic.

---

### Post by Evil Wayz on 2014-12-17
Fair enough.

---

### Post by mc4man on 2014-12-19
I see something similar with a hk speaker though it's not every time.  But happens enough to be unfortunate. At the moment the only solution when it occurs (shows as paired but really isn't), is to remove,  then re-add the device.
The reason I say 'really isn't' is my speaker gives an audio beep/visual confirmation  when truly paired & that doesn't happen in these cases even though the indicator says otherwise. And it doesn't show in sound settings as an output option.

I'm going to test this in a gnome-session for a bit to see if unity-control-center is somehow involved. Otherwise one could put up with it when it occurs or for me use android or windows which work fine all the time.

---

### Post by Evil Wayz on 2014-12-20
I use gnome-flashback, so I don't think it's Unity.

---

### Post by Evil Wayz on 2015-01-01
Aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaand now I have no bluetooth audio again.  Device pairs just fine, but when I try to test the sound in either headset or audio mode I get nothing.  Also Ad2p thinks it should be in mono mode. Seriously, what is the deal with this.

---

### Post by Evil Wayz on 2015-01-01
Ok my bluetooth audio quit working, no idea why.  So I thought I'd try some low tech, plugging headphones into the front audio jack.  Well that don't work neither.  I downloaded and installed a tool called alsa-tools-gui, but the override doesn't work either.  Anyone have any ideas how to get the front audio jack work in an hp xw4400 workstation with trusty on it?

---

### Post by Rob Sayer on 2015-01-02
Need more info than the make/model number, which isn't generally 100% useful.

This ...

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

... will tell you how to find out what your sound card is.  And also some steps.  Post what the terminal gives you.

Actually, once you have that kind of info it's usually faster to search here or askubuntu for any problems.  That's what I usually do now.  Even in Mint.

---

### Post by Evil Wayz on 2015-01-02
Noticed something troubling on the very first step :

```
 sudo aplay -l
[sudo] password for wolf: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
**** List of PLAYBACK Hardware Devices ****
Home directory not accessible: Permission denied
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0



```

I don't know what leaking memory means but it can't be good. 

Heres the rest.

```
 find /lib/modules/`uname -r` | grep snd
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-analog.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-ca0110.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-cmedia.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-ca0132.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-realtek.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-cirrus.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-generic.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-intel.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-controller.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-idt.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-conexant.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-si3054.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-hdmi.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-via.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-compress.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.13.0-41-generic/kernel/sound/spi/snd-at73c213.ko
/lib/modules/3.13.0-41-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.13.0-41-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.13.0-41-generic/kernel/sound/soc/atmel/snd-soc-atmel-pcm.ko
/lib/modules/3.13.0-41-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/3.13.0-41-generic/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/3.13.0-41-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-dice.ko
/lib/modules/3.13.0-41-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.13.0-41-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
wolf@shaitan:~$ 
wolf@shaitan:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-analog.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-ca0110.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-cmedia.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-ca0132.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-realtek.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-cirrus.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-generic.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-intel.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-controller.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-idt.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-conexant.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-si3054.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-hdmi.ko
/lib/modules/3.13.0-41-generic/updates/dkms/snd-hda-codec-via.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.13.0-41-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-timer.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-compress.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.13.0-41-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.13.0-41-generic/kernel/sound/spi/snd-at73c213.ko
/lib/modules/3.13.0-41-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.13.0-41-generic/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.13.0-41-generic/kernel/sound/soc/atmel/snd-soc-atmel-pcm.ko
/lib/modules/3.13.0-41-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/3.13.0-41-generic/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/3.13.0-41-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-scs1x.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.13.0-41-generic/kernel/sound/firewire/snd-dice.ko
/lib/modules/3.13.0-41-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.13.0-41-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.13.0-41-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
```

```
 lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 280c
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at e0a00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])

```

I ignored the rest of the tutorial because I'm pretty sure it's outdated. We use Pulseaudio now don't we?

---

### Post by raffi_1970 on 2015-05-08
I was having similar problems with my headset. It worked fine for months and then it would pair but not show up as a device in the sound settings. I tried all kinds of things. And then I tried the obvious solution--- uninstall the headset and reinstall. And for whatever reason it worked....for now!

---

