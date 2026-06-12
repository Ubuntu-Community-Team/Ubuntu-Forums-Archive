---
title: "C-Media USB Audio Device no sound in or out"
date: 2016-02-15
forum: Multimedia Software
---

### Post by Kilarin on 2016-02-15
I'm running Xubuntu 14.04 (32bit) on a Lenovo ThinkPad Edge E555. Which, instead of having nice seperate headphone and microphone jacks has one of those accursed combo jacks.  In order to get around that I purched a Syba SD-CM-UAUD USB Stereo Audio Adapter, C-Media Chipset.  
This is just a little usb adapter that should allow me to use normal headphones and microphone.  The add specifically said it was linux compatible.

The problem is, I can get the C-Media adapter to show up in my Volume Control menus, but it does NOT send any sound out to the speakers and it does NOT accept any sound from the microphone.  No sound in or out, which makes it pretty useless right now. :(

the device shows up under lsusb as:
Bus 007 Device 004: ID 0d8c:0008 C-Media Electronics, Inc. 

The default settings for snd-usb-audio in alsa-base.conf are:
$ grep snd-usb-audio /etc/modprobe.d/alsa-base.conf
options snd-usb-audio index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

When I plug in the C-Media usb device I see:
```

==> kern.log <==
Feb 15 19:29:03 perelandra kernel: [  705.904093] usb 7-1: new full-speed USB device number 3 using ohci-pci
Feb 15 19:29:03 perelandra kernel: [  706.068473] usb 7-1: New USB device found, idVendor=0d8c, idProduct=0008
Feb 15 19:29:03 perelandra kernel: [  706.068484] usb 7-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Feb 15 19:29:03 perelandra kernel: [  706.068490] usb 7-1: Product: C-Media USB Audio Device
Feb 15 19:29:03 perelandra kernel: [  706.228913] input: C-Media USB Audio Device    as /devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.3/0003:0D8C:0008.0005/input/input17
Feb 15 19:29:03 perelandra kernel: [  706.284314] hid-generic 0003:0D8C:0008.0005: input,hidraw0: USB HID v1.00 Device [C-Media USB Audio Device   ] on usb-0000:00:12.0-1/input3

==> Xorg.0.log <==
[   706.372] (II) config/udev: Adding input device C-Media USB Audio Device    (/dev/input/event5)
[   706.372] (**) C-Media USB Audio Device   : Applying InputClass "evdev keyboard catchall"
[   706.372] (II) Using input driver 'evdev' for 'C-Media USB Audio Device   '
[   706.372] (**) C-Media USB Audio Device   : always reports core events
[   706.372] (**) evdev: C-Media USB Audio Device   : Device: "/dev/input/event5"
[   706.372] (--) evdev: C-Media USB Audio Device   : Vendor 0xd8c Product 0x8
[   706.372] (--) evdev: C-Media USB Audio Device   : Found keys
[   706.372] (II) evdev: C-Media USB Audio Device   : Configuring as keyboard
[   706.372] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.3/0003:0D8C:0008.0005/input/input17/event5"
[   706.372] (II) XINPUT: Adding extended input device "C-Media USB Audio Device   " (type: KEYBOARD, id 12)
[   706.372] (**) Option "xkb_rules" "evdev"
[   706.372] (**) Option "xkb_model" "pc105"
[   706.372] (**) Option "xkb_layout" "us"

```

left click volume control/sound settings
Look in the Output Devices tab, and there it is C-Media USB Audio Device Analog Stereo Port=Speakers
But there is NO sound going out, the bar shows nothing even when the computer is playing sound.  and yes, its is NOT muted. :)
Same story on the input devices tab, except that there the C-Media USB Audio Device Analog Mono Port=Microphone
shows a low flicker in the bar consistant with a noise buzz, but no sound from the microphone is making it to the device.

I found a web page that indicated that you should change options snd-usb-audio index=-2 to be 0, so I did:

sudo sed -i 's/options snd-usb-audio index=-2/options snd-usb-audio index=0/g' /etc/modprobe.d/alsa-base.conf
$ grep snd-usb-audio /etc/modprobe.d/alsa-base.conf
options snd-usb-audio index=0
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=0

reboot (because sudo modprobe -r snd_usb_audio gets an error saying snd_usb_audio is in use)
attach the usb device and I see in the logs:

```

==> kern.log <==
Feb 15 20:13:17 perelandra kernel: [ 2031.256243] usb 7-1: new full-speed USB device number 2 using ohci-pci
Feb 15 20:13:17 perelandra kernel: [ 2031.420791] usb 7-1: New USB device found, idVendor=0d8c, idProduct=0008
Feb 15 20:13:17 perelandra kernel: [ 2031.420804] usb 7-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Feb 15 20:13:17 perelandra kernel: [ 2031.420811] usb 7-1: Product: C-Media USB Audio Device   
Feb 15 20:13:17 perelandra kernel: [ 2031.428796] input: C-Media USB Audio Device    as /devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.3/0003:0D8C:0008.0004/input/input16
Feb 15 20:13:17 perelandra kernel: [ 2031.484620] hid-generic 0003:0D8C:0008.0004: input,hidraw3: USB HID v1.00 Device [C-Media USB Audio Device   ] on usb-0000:00:12.0-1/input3

==> Xorg.0.log <==
[  2031.565] (II) config/udev: Adding input device C-Media USB Audio Device    (/dev/input/event15)
[  2031.565] (**) C-Media USB Audio Device   : Applying InputClass "evdev keyboard catchall"
[  2031.565] (II) Using input driver 'evdev' for 'C-Media USB Audio Device   '
[  2031.566] (**) C-Media USB Audio Device   : always reports core events
[  2031.566] (**) evdev: C-Media USB Audio Device   : Device: "/dev/input/event15"
[  2031.566] (--) evdev: C-Media USB Audio Device   : Vendor 0xd8c Product 0x8
[  2031.566] (--) evdev: C-Media USB Audio Device   : Found keys
[  2031.566] (II) evdev: C-Media USB Audio Device   : Configuring as keyboard
[  2031.566] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.3/0003:0D8C:0008.0004/input/input16/event15"
[  2031.567] (II) XINPUT: Adding extended input device "C-Media USB Audio Device   " (type: KEYBOARD, id 17)
[  2031.567] (**) Option "xkb_rules" "evdev"
[  2031.567] (**) Option "xkb_model" "pc105"
[  2031.567] (**) Option "xkb_layout" "us"

==> kern.log <==
Feb 15 20:13:18 perelandra kernel: [ 2031.602559] snd-usb-audio 7-1:1.0: cannot find the slot for index 0 (range 0-1), error: -16
Feb 15 20:13:18 perelandra kernel: [ 2031.602567] usb 7-1: cannot create card instance 0
Feb 15 20:13:18 perelandra kernel: [ 2031.602575] snd-usb-audio: probe of 7-1:1.0 failed with error -16
Feb 15 20:13:18 perelandra kernel: [ 2031.603176] usbcore: registered new interface driver snd-usb-audio

```

and now the C-Media entries do not appear in the volume control menu anymore.

Someone else said that I needed to use index=1, so trying that:
sudo sed -i 's/options snd-usb-audio index=0/options snd-usb-audio index=1/g' /etc/modprobe.d/alsa-base.conf
sudo modprobe -r snd_usb_audio
sudo modprobe snd_usb_audio
yank the device and reattach it and I see:
```

==> kern.log <==
Feb 15 20:18:54 perelandra kernel: [ 2367.932237] usb 7-1: new full-speed USB device number 3 using ohci-pci
Feb 15 20:18:54 perelandra kernel: [ 2368.096888] usb 7-1: New USB device found, idVendor=0d8c, idProduct=0008
Feb 15 20:18:54 perelandra kernel: [ 2368.096901] usb 7-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Feb 15 20:18:54 perelandra kernel: [ 2368.096908] usb 7-1: Product: C-Media USB Audio Device   
Feb 15 20:18:54 perelandra kernel: [ 2368.099371] snd-usb-audio 7-1:1.0: cannot find the slot for index 1 (range 0-1), error: -16
Feb 15 20:18:54 perelandra kernel: [ 2368.099385] usb 7-1: cannot create card instance 0
Feb 15 20:18:54 perelandra kernel: [ 2368.099401] snd-usb-audio: probe of 7-1:1.0 failed with error -16
Feb 15 20:18:54 perelandra kernel: [ 2368.105032] input: C-Media USB Audio Device    as /devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.3/0003:0D8C:0008.0005/input/input17
Feb 15 20:18:54 perelandra kernel: [ 2368.160730] hid-generic 0003:0D8C:0008.0005: input,hidraw3: USB HID v1.00 Device [C-Media USB Audio Device   ] on usb-0000:00:12.0-1/input3

==> Xorg.0.log <==
[  2368.233] (II) config/udev: Adding input device C-Media USB Audio Device    (/dev/input/event15)
[  2368.233] (**) C-Media USB Audio Device   : Applying InputClass "evdev keyboard catchall"
[  2368.233] (II) Using input driver 'evdev' for 'C-Media USB Audio Device   '
[  2368.233] (**) C-Media USB Audio Device   : always reports core events
[  2368.233] (**) evdev: C-Media USB Audio Device   : Device: "/dev/input/event15"
[  2368.233] (--) evdev: C-Media USB Audio Device   : Vendor 0xd8c Product 0x8
[  2368.233] (--) evdev: C-Media USB Audio Device   : Found keys
[  2368.233] (II) evdev: C-Media USB Audio Device   : Configuring as keyboard
[  2368.233] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.3/0003:0D8C:0008.0005/input/input17/event15"
[  2368.233] (II) XINPUT: Adding extended input device "C-Media USB Audio Device   " (type: KEYBOARD, id 17)
[  2368.233] (**) Option "xkb_rules" "evdev"
[  2368.233] (**) Option "xkb_model" "pc105"
[  2368.233] (**) Option "xkb_layout" "us"

```

And no C-Media entry in Volume Control.

Just to see what would happen, I also tried setting index=2
sudo sed -i 's/options snd-usb-audio index=1/options snd-usb-audio index=2/g' /etc/modprobe.d/alsa-base.conf
sudo modprobe -r snd_usb_audio
sudo modprobe snd_usb_audio

This time the log shows
==> kern.log <==
Feb 15 20:23:14 perelandra kernel: [ 2628.279143] usbcore: registered new interface driver snd-usb-audio

And C-Media appears in my Volume Control!  
BUT, with the same problem as before, its there, its not muted, all the controls work, but no sound actually goes out or in.

unplug and replug in the device with index=2 results in:
```

==> kern.log <==
Feb 15 20:26:14 perelandra kernel: [ 2808.032232] usb 7-1: new full-speed USB device number 4 using ohci-pci
Feb 15 20:26:14 perelandra kernel: [ 2808.200895] usb 7-1: New USB device found, idVendor=0d8c, idProduct=0008
Feb 15 20:26:14 perelandra kernel: [ 2808.200907] usb 7-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Feb 15 20:26:14 perelandra kernel: [ 2808.200914] usb 7-1: Product: C-Media USB Audio Device   
Feb 15 20:26:14 perelandra kernel: [ 2808.363038] input: C-Media USB Audio Device    as /devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.3/0003:0D8C:0008.0006/input/input18
Feb 15 20:26:14 perelandra kernel: [ 2808.416501] hid-generic 0003:0D8C:0008.0006: input,hidraw3: USB HID v1.00 Device [C-Media USB Audio Device   ] on usb-0000:00:12.0-1/input3

==> Xorg.0.log <==
[  2808.511] (II) config/udev: Adding input device C-Media USB Audio Device    (/dev/input/event15)
[  2808.511] (**) C-Media USB Audio Device   : Applying InputClass "evdev keyboard catchall"
[  2808.513] (II) Using input driver 'evdev' for 'C-Media USB Audio Device   '
[  2808.514] (**) C-Media USB Audio Device   : always reports core events
[  2808.514] (**) evdev: C-Media USB Audio Device   : Device: "/dev/input/event15"
[  2808.514] (--) evdev: C-Media USB Audio Device   : Vendor 0xd8c Product 0x8
[  2808.514] (--) evdev: C-Media USB Audio Device   : Found keys
[  2808.515] (II) evdev: C-Media USB Audio Device   : Configuring as keyboard
[  2808.515] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.3/0003:0D8C:0008.0006/input/input18/event15"
[  2808.515] (II) XINPUT: Adding extended input device "C-Media USB Audio Device   " (type: KEYBOARD, id 17)
[  2808.515] (**) Option "xkb_rules" "evdev"
[  2808.515] (**) Option "xkb_model" "pc105"
[  2808.515] (**) Option "xkb_layout" "us"

```

Other information that may be of use:  (these are with index=2)
```

$  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: CX20751/2 Analog [CX20751/2 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Device [C-Media USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```
~$ lsmod
Module                  Size  Used by
snd_usb_audio         143360  4 
snd_usbmidi_lib        28672  1 snd_usb_audio
ctr                    16384  1 
ccm                    20480  1 
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               307200  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   20480  2 
rfcomm                 61440  12 
dm_crypt               24576  0 
binfmt_misc            20480  1 
fglrx               11927552  110 
uvcvideo               73728  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              139264  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
kvm                   413696  0 
crc32_pclmul           16384  0 
aesni_intel            20480  1394 
aes_i586               20480  1 aesni_intel
xts                    16384  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  2 lrw,xts
ablk_helper            16384  1 aesni_intel
cryptd                 16384  696 ablk_helper
btusb                  36864  0 
bluetooth             430080  22 bnep,btusb,rfcomm
joydev                 20480  0 
serio_raw              16384  0 
edac_core              49152  0 
edac_mce_amd           24576  0 
snd_hda_codec_conexant    20480  1 
fam15h_power           16384  0 
snd_hda_codec_generic    65536  1 snd_hda_codec_conexant
snd_hda_codec_hdmi     49152  1 
k10temp                16384  0 
snd_hda_intel          32768  16 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
arc4                   16384  2 
snd_hda_codec         122880  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
rtl8723be              86016  0 
btcoexist              49152  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
snd_pcm                94208  10 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
rtlwifi                65536  2 rtl_pci,rtl8723be
i2c_piix4              20480  0 
snd_seq_midi           16384  0 
mac80211              618496  3 rtl_pci,rtlwifi,rtl8723be
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  2 snd_usbmidi_lib,snd_seq_midi
rtsx_pci_ms            20480  0 
memstick               16384  1 rtsx_pci_ms
cfg80211              450560  2 mac80211,rtlwifi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
thinkpad_acpi          73728  1 
nvram                  16384  1 thinkpad_acpi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28672  2 snd_pcm,snd_seq
parport_pc             32768  0 
mac_hid                16384  0 
shpchp                 32768  0 
ppdev                  20480  0 
snd                    69632  47 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
lp                     16384  0 
parport                40960  3 lp,ppdev,parport_pc
nls_iso8859_1          16384  1 
soundcore              16384  2 snd,snd_hda_codec
hid_generic            16384  0 
usbhid                 49152  0 
hid                    98304  2 hid_generic,usbhid
uas                    24576  0 
usb_storage            57344  4 uas
rtsx_pci_sdmmc         24576  0 
psmouse               102400  0 
ahci                   28672  1 
libahci                32768  1 ahci
r8169                  73728  0 
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc
mii                    16384  1 r8169
wmi                    20480  0 
video                  20480  0 

```

```

$ pacmd
Welcome to PulseAudio! Use "help" for usage information.
>>> list-sinks
3 sink(s) available.
    index: 0
	name: <alsa_output.pci-0000_00_01.1.hdmi-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: IDLE
	suspend cause: 
	priority: 9950
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: yes
	current latency: 71.93 ms
	max request: 13 KiB
	max rewind: 64 KiB
	monitor source: 0
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 1
	configured latency: 76.00 ms; range is 76.00 .. 371.52 ms
	card: 0 <alsa_card.pci-0000_00_01.1>
	module: 5
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "HDMI 0"
		alsa.id = "HDMI 0"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "3"
		alsa.card = "0"
		alsa.card_name = "HDA ATI HDMI"
		alsa.long_card_name = "HDA ATI HDMI at 0xf0b40000 irq 40"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:01.1"
		sysfs.path = "/devices/pci0000:00/0000:00:01.1/sound/card0"
		device.bus = "pci"
		device.vendor.id = "1002"
		device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
		device.product.id = "1308"
		device.form_factor = "internal"
		device.string = "hdmi:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "hdmi-stereo"
		device.profile.description = "Digital Stereo (HDMI)"
		device.description = "Built-in Audio Digital Stereo (HDMI)"
		alsa.mixer_name = "ATI R6xx HDMI"
		alsa.components = "HDA:1002aa01,00aa0100,00100500"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: yes)
			properties:
				device.icon_name = "video-display"
				device.product.name = "G257HL"
	active port: <hdmi-output-0>
  * index: 1
	name: <alsa_output.pci-0000_00_14.2.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: IDLE
	suspend cause: 
	priority: 9959
	volume: 0:  67% 1:  67%
	        0: -10.51 dB 1: -10.62 dB
	        balance -0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: yes
	current latency: 71.47 ms
	max request: 13 KiB
	max rewind: 64 KiB
	monitor source: 1
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 1
	configured latency: 76.00 ms; range is 76.00 .. 371.52 ms
	card: 1 <alsa_card.pci-0000_00_14.2>
	module: 6
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "CX20751/2 Analog"
		alsa.id = "CX20751/2 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "1"
		alsa.card_name = "HD-Audio Generic"
		alsa.long_card_name = "HD-Audio Generic at 0xf0b44000 irq 16"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:14.2"
		sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card1"
		device.bus = "pci"
		device.vendor.id = "1022"
		device.vendor.name = "Advanced Micro Devices, Inc. [AMD]"
		device.product.id = "780d"
		device.product.name = "FCH Azalia Controller"
		device.form_factor = "internal"
		device.string = "front:1"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Built-in Audio Analog Stereo"
		alsa.mixer_name = "Conexant CX20751/2"
		alsa.components = "HDA:14f1510f,17aa5111,00100100"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-speakers"
		analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: yes)
			properties:
				device.icon_name = "audio-headphones"
	active port: <analog-output-headphones>
    index: 3
	name: <alsa_output.usb-0d8c_C-Media_USB_Audio_Device-00-Device.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: IDLE
	suspend cause: 
	priority: 9049
	volume: 0: 100% 1: 100%
	        0: 0.00 dB 1: 0.00 dB
	        balance 0.00
	base volume: 100%
	             0.06 dB
	volume steps: 65537
	muted: no
	current latency: 80.96 ms
	max request: 13 KiB
	max rewind: 344 KiB
	monitor source: 5
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 1
	configured latency: 76.00 ms; range is 76.00 .. 2000.00 ms
	card: 3 <alsa_card.usb-0d8c_C-Media_USB_Audio_Device-00-Device>
	module: 23
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "USB Audio"
		alsa.id = "USB Audio"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "2"
		alsa.card_name = "C-Media USB Audio Device"
		alsa.long_card_name = "C-Media USB Audio Device at usb-0000:00:12.0-1, full speed"
		alsa.driver_name = "snd_usb_audio"
		device.bus_path = "pci-0000:00:12.0-usb-0:1:1.0"
		sysfs.path = "/devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.0/sound/card2"
		udev.id = "usb-0d8c_C-Media_USB_Audio_Device-00-Device"
		device.bus = "usb"
		device.vendor.id = "0d8c"
		device.vendor.name = "C-Media Electronics, Inc."
		device.product.id = "0008"
		device.product.name = "C-Media USB Audio Device   "
		device.serial = "0d8c_C-Media_USB_Audio_Device"
		device.string = "hw:2"
		device.buffering.buffer_size = "352800"
		device.buffering.fragment_size = "176400"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "C-Media USB Audio Device    Analog Stereo"
		alsa.mixer_name = "USB Mixer"
		alsa.components = "USB0d8c:0008"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-usb"
	ports:
		analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
			properties:
				device.icon_name = "audio-speakers"
	active port: <analog-output-speaker>
>>> 

```

I also ran:
wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh
with output:
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Tue Feb 16 02:47:02 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu 14.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.3 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      20DH002QUS
Product Version:   ThinkPad E555
Firmware Version:  HTET46WW (1.18 )


!!Kernel Information
!!------------------

Kernel release:    3.19.0-49-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.19.0-49-generic
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf0b40000 irq 40
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0b44000 irq 16
 2 [Device         ]: USB-Audio - C-Media USB Audio Device
                      C-Media USB Audio Device at usb-0000:00:12.0-1, full speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1308
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:01.1 0403: 1002:1308
	Subsystem: 17aa:5110
--
00:14.2 0403: 1022:780d (rev 01)
	Subsystem: 17aa:5110


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : -1

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : -1

!!Module: snd_usb_audio
	autoclock : Y
	device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	ignore_ctl_error : N
	index : 2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: ATI R6xx HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100500
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel
  Digital category: 0x2
  IEC Coding Type: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 1
     0x02
Node 0x04 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c
Node 0x0e [Audio Output] wcaps 0x221: Stereo Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
Node 0x0f [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x585600f0: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0e
Codec: Conexant CX20751/2
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x14f1510f
Subsystem Id: 0x17aa5111
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 D3cold S3D3cold CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=3, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x10 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="CX20751/2 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0xbf 0xbf]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Audio Output] wcaps 0xc1d: Stereo Amp-Out R/L
  Control: name="Speaker Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Speaker Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-Out vals:  [0x80 0x80]
  Converter: stream=5, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x12 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Control: name="Beep Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="Beep Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x07, nsteps=0x07, stepsize=0x0f, mute=0
  Amp-Out vals:  [0x03]
Node 0x13 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Device: name="CX20751/2 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80] [0xd0 0xd0] [0xd0 0xd0]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 3
     0x18 0x1a* 0x19
Node 0x14 [Audio Input] wcaps 0x100d1b: Stereo Amp-In R/L
  Amp-In caps: ofs=0x4a, nsteps=0x50, stepsize=0x03, mute=1
  Amp-In vals:  [0x4a 0x4a] [0x4a 0x4a] [0x4a 0x4a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 3
     0x19* 0x1a 0x15
Node 0x15 [Audio Mixer] wcaps 0x20050b: Stereo Amp-In
  Amp-In caps: ofs=0x4a, nsteps=0x4a, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11
Node 0x16 [Pin Complex] wcaps 0x400581: Stereo
  Control: name="Headphone Jack", index=0, device=0
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x04211040: [Jack] HP Out at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x10* 0x11
Node 0x17 [Pin Complex] wcaps 0x400501: Stereo
  Control: name="Speaker Phantom Jack", index=0, device=0
  Pincap 0x00000010: OUT
  Pin Default 0x90170110: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 2
     0x10 0x11*
Node 0x18 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001124: IN Detect
    Vref caps: HIZ 80
  Pin Default 0x40f001f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x19 [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00001124: IN Detect
    Vref caps: HIZ 80
  Pin Default 0x04a11030: [Jack] Mic at Ext Right
    Conn = 1/8, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1a [Pin Complex] wcaps 0x40048b: Stereo Amp-In
  Control: name="Internal Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Internal Mic Phantom Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x2f, mute=0
  Amp-In vals:  [0x03 0x03]
  Pincap 0x00000020: IN
  Pin Default 0x95a70120: [Fixed] Mic at Int Top
    Conn = Analog, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1c [Vendor Defined Widget] wcaps 0xf00000: Mono
--endcollapse--


!!USB Mixer information
!!---------------------
--startcollapse--

USB Mixer: usb_id=0x0d8c0008, ctrlif=0, ctlerr=0
Card: C-Media USB Audio Device at usb-0000:00:12.0-1, full speed
  Unit: 9
    Control: name="Speaker Playback Volume", index=0
    Info: id=9, control=2, cmask=0x3, channels=2, type="S16"
    Volume: min=-7264, max=-16, dBmin=-2837, dBmax=-6
  Unit: 9
    Control: name="Speaker Playback Switch", index=0
    Info: id=9, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 10
    Control: name="Auto Gain Control", index=0
    Info: id=10, control=7, cmask=0x0, channels=1, type="BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 10
    Control: name="Mic Capture Volume", index=0
    Info: id=10, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=0, max=6096, dBmin=0, dBmax=2381
  Unit: 10
    Control: name="Mic Capture Switch", index=0
    Info: id=10, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 13
    Control: name="Mic Playback Volume", index=0
    Info: id=13, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=0, max=12240, dBmin=0, dBmax=4781
  Unit: 13
    Control: name="Mic Playback Switch", index=0
    Info: id=13, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  2 Feb 15 19:39 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  5 Feb 15 19:39 /dev/snd/controlC1
crw-rw----+ 1 root audio 116,  9 Feb 15 20:26 /dev/snd/controlC2
crw-rw----+ 1 root audio 116,  4 Feb 15 19:39 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  8 Feb 15 19:39 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  3 Feb 15 20:20 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  7 Feb 15 20:20 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  6 Feb 15 20:20 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116, 11 Feb 15 20:26 /dev/snd/pcmC2D0c
crw-rw----+ 1 root audio 116, 10 Feb 15 20:26 /dev/snd/pcmC2D0p
crw-rw----+ 1 root audio 116,  1 Feb 15 19:39 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Feb 15 19:39 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Feb 15 20:26 .
drwxr-xr-x 4 root root 320 Feb 15 20:26 ..
lrwxrwxrwx 1 root root  12 Feb 15 20:26 usb-0d8c_C-Media_USB_Audio_Device-00 -> ../controlC2

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 100 Feb 15 20:26 .
drwxr-xr-x 4 root root 320 Feb 15 20:26 ..
lrwxrwxrwx 1 root root  12 Feb 15 19:39 pci-0000:00:01.1 -> ../controlC0
lrwxrwxrwx 1 root root  12 Feb 15 20:26 pci-0000:00:12.0-usb-0:1:1.0 -> ../controlC2
lrwxrwxrwx 1 root root  12 Feb 15 19:39 pci-0000:00:14.2 -> ../controlC1


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: CX20751/2 Analog [CX20751/2 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Device [C-Media USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: Generic [HD-Audio Generic], device 0: CX20751/2 Analog [CX20751/2 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Device [C-Media USB Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [HDMI]

Card hw:0 'HDMI'/'HDA ATI HDMI at 0xf0b40000 irq 40'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100500'
  Controls      : 7
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [Generic]

Card hw:1 'Generic'/'HD-Audio Generic at 0xf0b44000 irq 16'
  Mixer name	: 'Conexant CX20751/2'
  Components	: 'HDA:14f1510f,17aa5111,00100100'
  Controls      : 20
  Simple ctrls  : 9
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 74
  Mono: Playback 63 [85%] [-11.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [off]
  Front Right: Playback 74 [100%] [0.00dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 0 [0%] [-74.00dB] [off]
  Front Right: Playback 0 [0%] [-74.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 3 [43%] [-16.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB] [off]
  Front Right: Capture 80 [100%] [6.00dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [36.00dB]
  Front Right: 3 [100%] [36.00dB]

!!-------Mixer controls for card 2 [Device]

Card hw:2 'Device'/'C-Media USB Audio Device at usb-0000:00:12.0-1, full speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB0d8c:0008'
  Controls      : 9
  Simple ctrls  : 3
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 151
  Mono:
  Front Left: Playback 151 [100%] [-0.06dB] [on]
  Front Right: Playback 151 [100%] [-0.06dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined cvolume cvolume-joined pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: Playback 0 - 32 Capture 0 - 16
  Mono: Playback 23 [72%] [34.36dB] [off] Capture 16 [100%] [23.81dB] [on]
Simple mixer control 'Auto Gain Control',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]


!!Alsactl output
!!--------------

--startcollapse--
state.HDMI {
	control.1 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write locked'
			type IEC958
			count 1
		}
	}
	control.5 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface PCM
		device 3
		name ELD
		value '100007000710000102000000080000000472150447323537484c000907070000'
		comment {
			access 'read volatile'
			type BYTES
			count 32
		}
	}
	control.7 {
		iface PCM
		device 3
		name 'Playback Channel Map'
		value.0 3
		value.1 4
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
}
state.Generic {
	control.1 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 74
		value.1 74
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 74'
			dbmin -7400
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 74'
			dbmin -7400
			dbmax 0
			dbvalue.0 -7400
			dbvalue.1 -7400
		}
	}
	control.4 {
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.6 {
		iface MIXER
		name 'Capture Volume'
		value.0 80
		value.1 80
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 80'
			dbmin -7400
			dbmax 600
			dbvalue.0 600
			dbvalue.1 600
		}
	}
	control.7 {
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.8 {
		iface MIXER
		name 'Internal Mic Boost Volume'
		value.0 3
		value.1 3
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3600
			dbvalue.0 3600
			dbvalue.1 3600
		}
	}
	control.9 {
		iface MIXER
		name 'Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3600
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.10 {
		iface MIXER
		name 'Master Playback Volume'
		value 63
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 74'
			dbmin -7400
			dbmax 0
			dbvalue.0 -1100
		}
	}
	control.11 {
		iface MIXER
		name 'Master Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface CARD
		name 'Internal Mic Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.13 {
		iface CARD
		name 'Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface CARD
		name 'Headphone Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.15 {
		iface CARD
		name 'Speaker Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.16 {
		iface MIXER
		name 'Beep Playback Volume'
		value 3
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 7'
			dbmin -2800
			dbmax 0
			dbvalue.0 -1600
		}
	}
	control.17 {
		iface MIXER
		name 'Beep Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.18 {
		iface PCM
		name 'Playback Channel Map'
		value.0 3
		value.1 4
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.19 {
		iface PCM
		name 'Capture Channel Map'
		value.0 3
		value.1 4
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.20 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
state.Device {
	control.1 {
		iface PCM
		name 'Playback Channel Map'
		value.0 3
		value.1 4
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.2 {
		iface PCM
		name 'Capture Channel Map'
		value 2
		comment {
			access read
			type INTEGER
			count 1
			range '0 - 36'
		}
	}
	control.3 {
		iface MIXER
		name 'Mic Playback Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'Mic Playback Volume'
		value 23
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 32'
			dbmin 0
			dbmax 4781
			dbvalue.0 3436
		}
	}
	control.5 {
		iface MIXER
		name 'Speaker Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 151
		value.1 151
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 151'
			dbmin -2837
			dbmax -6
			dbvalue.0 -6
			dbvalue.1 -6
		}
	}
	control.7 {
		iface MIXER
		name 'Mic Capture Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'Mic Capture Volume'
		value 16
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 16'
			dbmin 0
			dbmax 2381
			dbvalue.0 2381
		}
	}
	control.9 {
		iface MIXER
		name 'Auto Gain Control'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_usb_audio
snd_usbmidi_lib
ctr
ccm
pci_stub
vboxpci
vboxnetadp
vboxnetflt
vboxdrv
bnep
rfcomm
dm_crypt
binfmt_misc
fglrx
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
v4l2_common
videodev
media
kvm
crc32_pclmul
aesni_intel
aes_i586
xts
lrw
gf128mul
ablk_helper
cryptd
btusb
bluetooth
joydev
serio_raw
edac_core
edac_mce_amd
snd_hda_codec_conexant
fam15h_power
snd_hda_codec_generic
snd_hda_codec_hdmi
k10temp
snd_hda_intel
snd_hda_controller
arc4
snd_hda_codec
snd_hwdep
rtl8723be
btcoexist
rtl8723_common
rtl_pci
snd_pcm
rtlwifi
i2c_piix4
snd_seq_midi
mac80211
snd_seq_midi_event
snd_rawmidi
rtsx_pci_ms
memstick
cfg80211
snd_seq
thinkpad_acpi
nvram
snd_seq_device
snd_timer
parport_pc
mac_hid
shpchp
ppdev
snd
lp
parport
nls_iso8859_1
soundcore
hid_generic
usbhid
hid
uas
usb_storage
rtsx_pci_sdmmc
psmouse
ahci
libahci
r8169
rtsx_pci
mii
wmi
video


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x03 0x185600f0
0x05 0x585600f0
0x07 0x585600f0
0x09 0x585600f0
0x0b 0x585600f0
0x0d 0x585600f0
0x0f 0x585600f0

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC1D0/init_pin_configs:
0x16 0x04211040
0x17 0x90170110
0x18 0x40f001f0
0x19 0x04a11030
0x1a 0x95a70120

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D0/hints:


!!ALSA/HDA dmesg
!!--------------

[ 2031.575221] init: Handling module-device-added event
[ 2031.602559] snd-usb-audio 7-1:1.0: cannot find the slot for index 0 (range 0-1), error: -16
[ 2031.602567] usb 7-1: cannot create card instance 0
[ 2031.602575] snd-usb-audio: probe of 7-1:1.0 failed with error -16
[ 2031.602763] init: Handling module-device-added event
[ 2031.603176] usbcore: registered new interface driver snd-usb-audio
[ 2031.606816] init: Handling drivers-device-added event
[ 2031.607169] init: Handling usb-device-added event
[ 2198.159071] usbcore: deregistering interface driver snd-usb-audio
[ 2198.175563] init: Handling drivers-device-removed event
--
[ 2209.901542] init: Handling module-device-added event
[ 2209.910000] snd-usb-audio 7-1:1.0: cannot find the slot for index 1 (range 0-1), error: -16
[ 2209.910010] usb 7-1: cannot create card instance 0
[ 2209.910020] snd-usb-audio: probe of 7-1:1.0 failed with error -16
[ 2209.910050] usbcore: registered new interface driver snd-usb-audio
[ 2209.913180] init: Handling module-device-added event
--
[ 2368.096908] usb 7-1: Product: C-Media USB Audio Device
[ 2368.099371] snd-usb-audio 7-1:1.0: cannot find the slot for index 1 (range 0-1), error: -16
[ 2368.099385] usb 7-1: cannot create card instance 0
[ 2368.099401] snd-usb-audio: probe of 7-1:1.0 failed with error -16
[ 2368.105032] input: C-Media USB Audio Device    as /devices/pci0000:00/0000:00:12.0/usb7/7-1/7-1:1.3/0003:0D8C:0008.0005/input/input17
--
[ 2368.224435] init: Handling hidraw-device-added event
[ 2627.076304] usbcore: deregistering interface driver snd-usb-audio
[ 2627.096499] init: Handling drivers-device-removed event
--
[ 2628.126389] init: Handling module-device-added event
[ 2628.277516] init: Handling sound-device-added event
[ 2628.279143] usbcore: registered new interface driver snd-usb-audio
[ 2628.285293] init: Handling drivers-device-added event
[ 2628.289083] init: Handling sound-device-added event
[ 2628.297960] init: Handling sound-device-added event
[ 2628.322257] init: Handling sound-device-added event
[ 2628.334432] init: Handling sound-device-changed event
[ 2797.953579] usb 7-1: USB disconnect, device number 3
[ 2797.958598] init: Handling sound-device-removed event
[ 2797.962649] init: Handling sound-device-removed event
[ 2797.969674] init: Handling usb-device-removed event
[ 2797.972595] init: Handling sound-device-removed event
[ 2797.976600] init: Handling sound-device-removed event
[ 2797.982020] init: Handling usb-device-removed event
--
[ 2808.452944] init: Handling usb-device-added event
[ 2808.453358] init: Handling sound-device-added event
[ 2808.471004] init: Handling sound-device-added event
[ 2808.473507] init: Handling sound-device-added event
[ 2808.476400] init: Handling usb-device-added event
--
[ 2808.511201] init: Handling input-device-added event
[ 2808.530473] init: Handling sound-device-added event
[ 2808.532705] init: Handling sound-device-changed event
[ 3935.978333] perf interrupt took too long (2609 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

```

That is a lot of information, but it doesn't tell my ignorant self anything.

Any advice would be much appreciated.  Thank you.

---

