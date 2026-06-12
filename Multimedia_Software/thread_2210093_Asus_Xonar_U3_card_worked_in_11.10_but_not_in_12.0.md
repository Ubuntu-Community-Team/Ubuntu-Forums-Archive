---
title: "Asus Xonar U3 card worked in 11.10 but not in 12.04"
date: 2014-03-08
forum: Multimedia Software
---

### Post by mamboze on 2014-03-08
HI, I've just upgraded from 11.10 to 12.04 and I've found that the Asus Xonar U3 card which worked well under 11.10 doesn't work with 12.04. This is a real disadvantage as I use my laptop, Samsung RV511, to record speech for teaching English. The internal sound chip is pretty poor by comparison with the Xonar. 
It looks like the Xonar is not being recognized by the OS. 
> ~$ lsmod | grep snd
snd_hda_codec_hdmi     40881  1 
snd_hda_codec_realtek    50931  1 
snd_hda_intel          43326  3 
snd_hda_codec         169608  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                94597  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28930  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61270  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
roy@medea:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Samsung Electronics Co Ltd Device c581
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fc800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

> ~$ ^C
roy@medea:~$ lsmod | grep snd
snd_hda_codec_hdmi     40881  1 
snd_hda_codec_realtek    50931  1 
snd_hda_intel          43326  3 
snd_hda_codec         169608  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                94597  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                55716  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28930  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61270  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm

I've had a look at the ALSA Project page  [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio)  but I'm not sure if this is the way to go.

Any help would be much appreciated  TIA

---

### Post by kostkon on 2014-03-09
What do you mean it does not work, you need to be give more details about the problem. Is it not listed in your sound settings? What's the output of
```
aplay -l
```

also, if you just upgraded, then you could delete your *.pulse* folder to reset pulseaudio and get rid of the 11.10 configuration (in nautilus, select View -> Show Hiddent Files or press CTRL+H, then find the folder and delete it, then logout and log back in.)

---

### Post by Yellow Pasque on 2014-03-09
Instead of aplay -l, give entire info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Also, it may be helpful to look at:
```
sudo update-usbids
lsusb -v
sudo modprobe -v snd-usb-audio
```

---

### Post by mamboze on 2014-03-09
Hi,

output of 'aplay -l'

```
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Yeah, I take your point, I should have given more details and I was imprecise:

1. saying 'not working', actually the Xonar is not being recognised.
2. saying  'upgrade'  , I did a clean install of 12.04 not an upgrade, so I guess any 11.10 config details would have been overwritten.

Sorry about that.

---

### Post by mamboze on 2014-03-10
OK    ALSA info @  [http://www.alsa-project.org/db/?f=904bffdf125f144073151f0cd14be7fcdd0a9297](http://www.alsa-project.org/db/?f=904bffdf125f144073151f0cd14be7fcdd0a9297)

```

~$ sudo update-usbids
--2014-03-10 10:53:07--  http://www.linux-usb.org/usb.ids
Resolving www.linux-usb.org (www.linux-usb.org)... 216.34.181.97
Connecting to www.linux-usb.org (www.linux-usb.org)|216.34.181.97|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 514146 (502K) [text/plain]
Saving to: `/var/lib/usbutils/usb.ids.new'

100%[======================================>] 514,146     44.0K/s   in 12s     

2014-03-10 10:53:20 (43.1 KB/s) - `/var/lib/usbutils/usb.ids.new' saved [514146/514146]

Done.

```
I checked usb.ids.new but couldn't find it only usb.ids.old
There was only entry for 'xonar' was '1743  Xonar U1 Audio Station'  - obviously, not the same device. 

lsusb -v gave a very large output >50Kb 

```
~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1005 Silicon Motion WebCam SCB-0385N
Bus 002 Device 003: ID 0a5c:219c Broadcom Corp. 
Bus 002 Device 004: ID 046d:c52f Logitech, Inc. Unifying Receiver

```

```
:~$ sudo modprobe -v snd-usb-audio
[sudo] password for roy: 
insmod /lib/modules/3.11.0-18-generic/kernel/sound/usb/snd-usbmidi-lib.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/sound/usb/snd-usb-audio.ko index=-2 index=-2

```

Where to go from here?  :)

---

### Post by Yellow Pasque on 2014-03-10
Until lsusb recognizes the device, there's not much to do. Remove the card and reinsert it. Then look at end of dmesg to check for errors:
```
dmesg | tail -n 20
```

---

### Post by mamboze on 2014-03-10
OK, here's the output:

```
~$ dmesg | tail -n 20
[   94.924384] audit_printk_skb: 141 callbacks suppressed
[   94.924393] type=1400 audit(1394435966.708:77): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=3365 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  312.119018] usb 2-1.1: USB disconnect, device number 9
[  312.119025] usb 2-1.1.1: USB disconnect, device number 10
[  312.126406] usb 2-1.1.2: USB disconnect, device number 11
[  312.126581] usblp1: removed
[  312.126746] usb 2-1.1.3: USB disconnect, device number 12
[  312.126832] usblp2: removed
[  312.126926] usb 2-1.1.4: USB disconnect, device number 13
[  318.968185] usb 2-1.2: new full-speed USB device number 14 using ehci-pci
[  319.040378] usb 2-1.2: device descriptor read/64, error -32
[  319.216256] usb 2-1.2: device descriptor read/64, error -32
[  319.392130] usb 2-1.2: new full-speed USB device number 15 using ehci-pci
[  319.464115] usb 2-1.2: device descriptor read/64, error -32
[  319.639979] usb 2-1.2: device descriptor read/64, error -32
[  319.815887] usb 2-1.2: new full-speed USB device number 16 using ehci-pci
[  320.223453] usb 2-1.2: device not accepting address 16, error -32
[  320.295637] usb 2-1.2: new full-speed USB device number 17 using ehci-pci
[  320.703200] usb 2-1.2: device not accepting address 17, error -32
[  320.703401] hub 2-1:1.0: unable to enumerate USB device on port 2

```

---

### Post by mamboze on 2014-03-10
Hi,
The Xonar is now working  I checked out online the dmesg error  "device descriptor read/64, error -32". This took me to   [http://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error](http://paulphilippov.com/articles/how-to-fix-device-not-accepting-address-error)   which states that this error indicates USB over-current protection is being triggered. Turning the laptop off and pulling the battery for a while then a restart and, happy day, the Xonar started up. :)

Thanks very much, Temujin for pointing me in the right direction.

There used to be a way of tagging a thread "Solved" but I can't see it.

---

### Post by Yellow Pasque on 2014-03-10
You're welcome (nice googling there). Marking "Solved" is under thread tools menu towards the top.

---

