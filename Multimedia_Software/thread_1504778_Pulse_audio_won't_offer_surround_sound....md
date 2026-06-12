---
title: "Pulse audio won't offer surround sound..."
date: 2010-06-08
forum: Multimedia Software
---

### Post by Beanmonster on 2010-06-08
Hi guys :)

All hardware independently tested and working, first of all.

[B]daemon.conf
[/B]```
default-sample-channels = 6
default-channel-map = front-left,front-right,front-center,rear-left,rear-right,lfe
```

All levels in **alsamixer -c 0** are fine and unmuted.

[B]asound.conf:
[/B]```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
ctl.!default {
    type pulse
}
```

Tried **speakertest -c6**, only front two channels active

[SIZE=3][B]How do I select "Analog Surround 5.1" as a profile under configuration?

[/B][IMG]http://img3.imageshack.us/img3/740/screenshotvolumecontrolc.png[/IMG]
[/SIZE]
Any advice would greatly be appreciated

---

### Post by Beanmonster on 2010-06-10
Still no luck on finding a solution...

I have a ICE1724 PCI multichannel sound cards (VIA ENVY24)

---

### Post by lidex on 2010-06-13
Can you post this output please:
```
sudo lshw -C multimedia
```

Also these:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
 
```

---

### Post by Beanmonster on 2010-06-18
Sorry for the delayed response, had internet problems.

[B]sudo lshw -C multimedia
[/B]```
*-multimedia            
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ICE1724 latency=64
       resources: irq:19 ioport:ec00(size=32) ioport:e880(size=128)
```[B]

uname -a[/B]
```
Linux bean-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

```[B]
aplay -l
[/B]```
**** List of PLAYBACK Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICE1724 [ICEnsemble ICE1724], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```[B]dpkg -l | grep "alsa"
[/B]```
ii  alsa-base                              1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                             1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                             4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                     0.10.28-1                                       GStreamer plugin for ALSA

```

Thank you for your support

---

### Post by lidex on 2010-06-18
Try this.
Using a Terminal="Applications->Accessories->Terminal"
First backup config files:
```
mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/

```
Now remove:
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.
Then
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

---

### Post by lidex on 2010-06-18
Any of these sound familiar:
            ```

                        * MidiMan M Audio Revolution 5.1
			* MidiMan M Audio Revolution 7.1
			* MidiMan M Audio Audiophile 192
			* AMP Ltd AUDIO2000
			* TerraTec Aureon 5.1 Sky
			* TerraTec Aureon 7.1 Space
			* TerraTec Aureon 7.1 Universe
			* TerraTec Phase 22
			* TerraTec Phase 28
			* AudioTrak Prodigy 7.1
			* AudioTrak Prodigy 7.1 LT
			* AudioTrak Prodigy 7.1 XT
			* AudioTrak Prodigy 7.1 HIFI
			* AudioTrak Prodigy 7.1 HD2
			* AudioTrak Prodigy 192
			* Pontis MS300
			* Albatron K8X800 Pro II 
			* Chaintech ZNF3-150
			* Chaintech ZNF3-250
			* Chaintech 9CJS
			* Chaintech AV-710
			* Shuttle SN25P
			* Onkyo SE-90PCI
			* Onkyo SE-200PCI
			* ESI Juli@
			* ESI Maya44
			* Hercules Fortissimo IV
			* EGO-SYS WaveTerminal 192M
```

---

### Post by Beanmonster on 2010-06-20
Tried the above to no avail, thanks for the effort tho! :)

Yeah, Its an AudioTrak Maya 5.1 MK-II

---

### Post by lidex on 2010-06-21
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-ice1724 model=maya44 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Beanmonster on 2010-09-07
> **lidex said:**
> Any of these sound familiar:
            ```

			...
			* AudioTrak Prodigy 7.1
			* AudioTrak Prodigy 7.1 LT
			* AudioTrak Prodigy 7.1 XT
			* AudioTrak Prodigy 7.1 HIFI
			* AudioTrak Prodigy 7.1 HD2
			* AudioTrak Prodigy 192
			...

```

I have an AudioTrak Prodigy 5.1, have tried a lot of things since June but still no luck :(

---

