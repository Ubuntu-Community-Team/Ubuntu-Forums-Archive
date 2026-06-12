---
title: "no sound for .mkv files"
date: 2010-05-20
forum: Multimedia Software
---

### Post by [A]madeus on 2010-05-20
Dear experts,
i have a strange situation.
My Totem can play any mkv files just only with an internal sound card. When i connected an external speaker (Bose USB Audio), the sound of the playing mkv file suddenly mute.
Then i used Rhythmbox to check sound for the external speaker, 
it plays well.
(Also for any other video formats e.g. AVI)

My laptop has two sound cards as following
```
amadeus@amadeus-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [Bose USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And output of my kernel version.
```
amadeus@amadeus-laptop:~$ uname -a
Linux amadeus-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

amadeus@amadeus-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).

amadeus@amadeus-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Analog Devices AD1981

```

Below is system message when i was trying to play the mkv file with Bose USB Audio.
```
May 20 21:50:24 amadeus-laptop kernel: [16722.273062] usb 2-1: new full speed USB device using uhci_hcd and address 9
May 20 21:50:24 amadeus-laptop kernel: [16722.467943] usb 2-1: configuration #1 chosen from 1 choice
May 20 21:50:24 amadeus-laptop kernel: [16722.481073] ALSA usbaudio.c:1293: 9:1:1: cannot get freq at ep 0x1
May 20 21:50:24 amadeus-laptop kernel: [16722.521264] generic-usb 0003:05A7:1020.000A: hiddev96,hidraw0: USB HID v1.10 Device [Bose Corporation Bose USB Audio] on usb-0000:00:1d.0-1/input2
May 20 21:50:24 amadeus-laptop pulseaudio[5278]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/sound/card1 (alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio) more often than 5 times in 10s
May 20 21:51:11 amadeus-laptop kernel: [16769.681089] usb 2-1: USB disconnect, address 9
May 20 21:51:15 amadeus-laptop kernel: [16773.528046] usb 2-1: new full speed USB device using uhci_hcd and address 10
May 20 21:51:15 amadeus-laptop kernel: [16773.719227] usb 2-1: configuration #1 chosen from 1 choice
May 20 21:51:15 amadeus-laptop kernel: [16773.738074] ALSA usbaudio.c:1293: 10:1:1: cannot get freq at ep 0x1
May 20 21:51:15 amadeus-laptop kernel: [16773.768247] generic-usb 0003:05A7:1020.000B: hiddev96,hidraw0: USB HID v1.10 Device [Bose Corporation Bose USB Audio] on usb-0000:00:1d.0-1/input2
May 20 21:51:16 amadeus-laptop pulseaudio[5278]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/sound/card1 (alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio) more often than 5 times in 10s
May 20 21:51:27 amadeus-laptop kernel: [16785.556106] usb 2-1: USB disconnect, address 10
May 20 21:51:29 amadeus-laptop kernel: [16787.860104] usb 2-1: new full speed USB device using uhci_hcd and address 11
May 20 21:51:29 amadeus-laptop kernel: [16788.044653] usb 2-1: configuration #1 chosen from 1 choice
May 20 21:51:30 amadeus-laptop kernel: [16788.060445] ALSA usbaudio.c:1293: 11:1:1: cannot get freq at ep 0x1
May 20 21:51:30 amadeus-laptop kernel: [16788.095631] generic-usb 0003:05A7:1020.000C: hiddev96,hidraw0: USB HID v1.10 Device [Bose Corporation Bose USB Audio] on usb-0000:00:1d.0-1/input2
May 20 21:51:30 amadeus-laptop pulseaudio[5278]: module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/sound/card1 (alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio) more often than 5 times in 10s
May 20 21:51:40 amadeus-laptop kernel: [16798.879442] ALSA usbaudio.c:1293: 11:1:1: cannot get freq at ep 0x1
May 20 21:51:40 amadeus-laptop kernel: [16798.892465] ALSA usbaudio.c:1293: 11:1:1: cannot get freq at ep 0x1
May 20 21:51:40 amadeus-laptop kernel: [16798.904466] ALSA usbaudio.c:1293: 11:1:1: cannot get freq at ep 0x1
May 20 21:51:40 amadeus-laptop kernel: [16798.974466] ALSA usbaudio.c:1293: 11:1:1: cannot get freq at ep 0x1
May 20 21:51:40 amadeus-laptop pulseaudio[12193]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.

```

Please note that it used to work with Karmic Koala before.

Kindly let me know should i need to provide further log to you.
i'm a newbie for Ubuntu; please bear with me.
:oops:

---

### Post by Wolvenreign on 2010-09-23
I'm not sure if this will fix your specific problem, but when I couldn't play sound in MKV files in Ubuntu, I used this...

```
sudo apt-get install mkvtoolunix
```

It worked.

Good luck!

---

### Post by szekelygobe on 2012-01-14
> 
```
sudo apt-get install mkvtoolunix
```

This is wrong the correct line is (no U in mkvtoolUnix)
```
sudo apt-get install mkvtoolnix
```

---

### Post by coffeecat on 2012-01-14
@szekelygobe, thanks for the clarification, but this is an old thread.

Thread closed.

---

