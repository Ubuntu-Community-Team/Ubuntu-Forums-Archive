---
title: "M1 Active 320 USB speakers"
date: 2009-06-18
forum: Multimedia Software
---

### Post by bubbhasdance on 2009-06-18
I have recently switched from Windows Vista SP2 to Ubuntu 9.04 and am loving the change so far. I had some problems with my wireless, but all is well, except for one thing...I can't seem to get my speakers to work using Songbird, or any other program for that matter. I imagine that it is a driver problem, but know next to nothing about Linux yet, so some help would be greatly appreciated. 

Using lsusb I get this:
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 005: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 006 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

And I believe Bus 006 are the speakers.

---

### Post by kostkon on 2009-06-19
I suppose that's them:
```
Bus 006 Device 005: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
```
Open a terminal and give:
```
aplay -l
```
and check if you can see them listed in the output of this command.

The next step would be to install the *PulseAudio Device Chooser* (using *Synaptic*). You need to run it, left-click on its icon in your system tray and select the *Volume Control*.

Next, you will need to select the *Output Devices* tab, right-click on your speaker's entry there and enable the *Default* option to set them as the default output device in your system.

Or if don't want to set them as the default device, you can just sent the sound of an application to these speakers on-the-fly in the Playback tab.

For more info, check [this helpful thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by bubbhasdance on 2009-06-19
Your post and the helpful link worked perfectly, my sound is playing clear as can be. Thanks so much!

---

### Post by cristina.hatcher on 2011-04-30
Hello,
I have done all steps but I have a problem, my system doesn't recognise M1 Active Usb like output device, it does like input device.
I cant see the device in Volume Control -> output devices
When I send alplay -l command I receive this:
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC861 Analog [ALC861 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 1: default [USB Audio CODEC ], dispositivo 0: USB Audio [USB Audio]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
What can I do? Thanks,
C

---

### Post by cristina.hatcher on 2011-04-30
I have it solved now. I have changed, in volume control config tab, the perfil for PCM29000 Device  it as a output device, I had it like input source!
Thanks anyway! Have a nice day

---

### Post by cristina.hatcher on 2011-05-01
I

---

### Post by cristina.hatcher on 2011-05-01
I have another problem now. Im using Spotify with Wine, it works fine  until another Linux program uses the sound, then spotify stops. If I  reboot Spotify then I can heard 2 seconds and then it stops again. There  are any solution?
Thanks in advance

---

