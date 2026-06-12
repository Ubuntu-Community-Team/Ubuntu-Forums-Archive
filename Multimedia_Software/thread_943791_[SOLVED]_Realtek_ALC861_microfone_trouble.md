---
title: "[SOLVED] Realtek ALC861 microfone trouble"
date: 2008-10-10
forum: Multimedia Software
---

### Post by orawax on 2008-10-10
There seems to be at least four different unsolved threads on Realtek ALC861 integrated sound card / microfone trouble. The thing is, I can hear my voice from the mic through the headphones, but neither Sound recorder nor Ekiga catches the sound. Editing /etc/modprobe.d/alsa-base as suggested ([http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)) doesn't help. Hardy.

Here are some previous threads on ALC861 / mic:
[http://ubuntuforums.org/showthread.php?t=701317](http://ubuntuforums.org/showthread.php?t=701317)
[http://ubuntuforums.org/showthread.php?t=703456](http://ubuntuforums.org/showthread.php?t=703456)
[http://ubuntuforums.org/showthread.php?t=720114](http://ubuntuforums.org/showthread.php?t=720114)
[http://ubuntuforums.org/showthread.php?t=749603](http://ubuntuforums.org/showthread.php?t=749603)

---

### Post by markbuntu on 2008-10-10
You need to set the capture in the sound mixer to use your mic for recording. If you can hear it, the driver is most likely OK.

---

### Post by orawax on 2008-10-19
I've checked alsamixer, installed many different GUI's for it, tried every possible switch and control, but I can't figure out where the problem might be.

Then I made the mistake to update ALSA, first with module-assistant, which killed the sound totally (there wasn't even that background buzz, and now besides the dead mic, I didn't get any sound out of the machine). Then I compiled Alsa 1.0.18rc3 by hand ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)), using the switch --with-cards=hda-intel when compiling the driver. Now I've got something in there, the background buzz at least. No sound though, and mic still not working.

In Volume Control preferences I have now 8 different devices available through File > Change Device, which is even more confusing. These are:

pcsp (Alsa mixer)
HDA-Intel (Alsa mixer)
PC-Speaker (Oss mixer)
Playback: ALSA PCM on hw:0 (pcsp) via DMA (PulseAudio mixer)
Playback: ALSA PCM on front:1 (ALC861 Analog) via DMA (PulseAudio mixer)
Capture: Monitor Source of ALSA on hw:0 (pcsp) via DMA (PulseAudio mixer)
Capture: Monitor Source of ALSA on front:1 (ALC861 Analog) via DMA (PulseAudio mixer)
Capture: ALSA PCM on front:1 (ALC861 Analog) via DMA (PulseAudio mixer)

The only sound I get out of the machine is when I speak to the microphone, the sound comes through both the internal speakers and headphones. But as I play music on Amarok for instance, I hear no sound, even though PulseAudio Volume Control recognizes the audio stream in Playback tab.

I have made sure that all controls are enabled through Edit > Preferences, device by device, and nothing is muted. The only glider that gives any effect is the Microphone volume in HDA Intel (Alsa mixer) playback tab.

In shell I can access three at least three different devices:
alsamixer takes me to Card: PulseAudio  Chip: Pulseaudio
alsamixer -D hw:0 takes me to Card: pcsp  Chip: PC Speaker and
alsamixer -D hw:1 takes me to Card: HDA Intel  Chip: Realtek ALC861

I also tried to fix PulseAudio as displayed here:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
to no avail.

dmesg gives no mention of snd_ anything, but there's an error like this:

```
[   73.401729] alsactl[4423]: segfault at 00000000 eip b7dce283 esp bff86c0c error 4
[   73.402476] alsactl[4424]: segfault at 00000000 eip b7da2283 esp bfdf527c error 4
[   73.423352] alsactl[4443]: segfault at 00000000 eip b7d33283 esp bf9415bc error 4
[   73.424133] alsactl[4444]: segfault at 00000000 eip b7d0e283 esp bfb2f7ac error 4
[   73.576961] alsactl[4618]: segfault at 00000000 eip b7ddf283 esp bf821c9c error 4
[   73.577720] alsactl[4619]: segfault at 00000000 eip b7cfe283 esp bf921d9c error 4
```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: pcsp [pcsp], device 0: pcspeaker [pcsp]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Fujitsu Siemens Computers Unknown device 10c7
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

Getting a bit tired, dreaming of forests.

---

### Post by orawax on 2008-11-07
_My way to the solution was:_

**Upgrade** to Intrepid Ibex

**Add line** *options snd-hda-intel model=3stack* to the end of file /etc/modprobe.d/alsa-base (remember to save). In terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

(alsa-base options for other models, see [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845))

**Reboot**

**In System** > Preferences > Sound > Sound Conferencing > Sound Capture, select *HDA Intel ALC861 Analog (ALSA)*

Right click the **Volume controller in the desktop panel** and *Open volume control*.

**Select Device:** *HDA Intel (ALSA mixer)* and click Preferences. After upgrade there are now several new switches available.

Set the 'Front Mic Capture' -switch visible and close window. Then select Switches-tab and enable 'Front Mic Capture' switch. Do NOT mess with other devices' (eg. Realtek/OSS) recording settings, as these seem to disable the Front Mic Capture switch.

*Alternatively, it may be enough to upgrade ALSA instead of upgrading the whole system. In this case you should probably add also these lines to */etc/modprobe.d/alsa-base* (they were added by the ubuntu upgrade process):

```
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

Hope this does the trick for you, too!

---

### Post by orawax on 2008-11-07
I guess I should have posted the solution as a new reply instead of editing the recent posting - so just to let you know, in case there's someone waiting for an email notification: Problem solved!

---

### Post by Mikethk on 2008-11-19
It solved the problem for me, you ******* I love you.... I will translate to Dansih to help others from my country. thx alot. :guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

