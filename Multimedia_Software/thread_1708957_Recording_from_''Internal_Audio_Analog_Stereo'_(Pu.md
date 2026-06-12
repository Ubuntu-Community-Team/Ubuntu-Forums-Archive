---
title: "Recording from ''Internal Audio Analog Stereo' (Pulse+Alsa)"
date: 2011-03-17
forum: Multimedia Software
---

### Post by Blutorange on 2011-03-17
[Ubuntu 10.10]

Hello,

I am experiencing troubles recording from Internal Audio Analog Stereo in pavucontrol. There is microphone 1 (external) and microphone 2 (built-in notebook internal). I am certain I have chosen the correct input port in pavucontrol, have chosen the correct input device under Recording for the application I am using, and unmuted the microphone. AI can record from both "Monitor of Internal Audio Analog Stereo" and "Monitor of RV710/730 Digital Stereo (HDMI)". It works with both Skype and Audacity. Audio playback works perfectly fine as well. Unmuting the microphone under playback with alsamixer, what the microphone records gets outputted to the speakers, so I can confirm the microphone itself works.

"arecord -D hw:0,2 -r 48000 -c 2 -f S16_LE" reports:
> arecord: pcm_read:1692: read error: Input/output error
Recording from the mic with audacity does not work as well.

Recording from Internal Audio Analog Stereo did work previously, then stopped working. I think my problem may be related to misconfiguration (perhaps having both pulse+alsa, I do not know much about this), or wrong access permission (my user am added to the pulse-access group, however). Being able to select output for every application with pavucontrol is very convenient, so I would like not to uninstall pulse.

Output of various commands:
aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci -v (nonrelevant devices removed)
> 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Acer Incorporated [ALI] Device 0294
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.1 Audio device: ATI Technologies Inc RV710/730
	Subsystem: Acer Incorporated [ALI] Device 0294
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at cfeec000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


cat /proc/asound/pcm
> 00-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1
00-01: ALC888 Digital : ALC888 Digital : playback 1
00-02: ALC888 Analog : ALC888 Analog : capture 1
01-03: ATI HDMI : ATI HDMI : playback 1

cat /proc/asound/version
> Advanced Linux Sound Architecture Driver Version 1.0.23.
cat /proc/asound/modules
>  0 snd_hda_intel
 1 snd_hda_intel
cat /proc/asound/devices
>   2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0- 1]: hardware dependent
  9: [ 0- 0]: hardware dependent
 10: [ 0]   : control
 11: [ 1- 3]: digital audio playback
 12: [ 1- 0]: hardware dependent
 13: [ 1]   : control

cat /proc/asound/cards
>  0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf0400000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfeec000 irq 43

cat /proc/asound/card?/codec#* | grep Codec
> Codec: Realtek ALC888
Codec: LSI ID 1040
Codec: ATI R6xx HDMI
dpkg --get-selections | grep alsa
> alsa-base					install
alsa-oss					install
alsa-utils					install
alsamixergui					install
gnome-alsamixer					install
gstreamer0.10-alsa				install
libclalsadrv1					deinstall
libsox-fmt-alsa					install
linux-alsa-driver-modules-2.6.32-23-generic-pae	install
linux-backports-modules-alsa-2.6.32-23-generic	deinstall
linux-backports-modules-alsa-2.6.32-24-generic	install
linux-backports-modules-alsa-2.6.32-25-generic	install
linux-backports-modules-alsa-lucid-generic	install

dpkg --get-selections | grep pulse
> gstreamer0.10-pulseaudio			install
libpulse-browse0				install
libpulse-dev					install
libpulse-mainloop-glib0				install
libpulse0					install
libsdl1.2debian-pulseaudio			install
libsox-fmt-pulse				install
projectm-pulseaudio				install
pulseaudio					install
pulseaudio-dbg					install
pulseaudio-esound-compat			install
pulseaudio-esound-compat-dbg			install
pulseaudio-module-bluetooth			install
pulseaudio-module-bluetooth-dbg			install
pulseaudio-module-gconf				install
pulseaudio-module-gconf-dbg			install
pulseaudio-module-jack				install
pulseaudio-module-jack-dbg			install
pulseaudio-module-lirc				install
pulseaudio-module-lirc-dbg			install
pulseaudio-module-raop				install
pulseaudio-module-raop-dbg			install
pulseaudio-module-x11				install
pulseaudio-module-x11-dbg			install
pulseaudio-module-zeroconf			install
pulseaudio-module-zeroconf-dbg			install
pulseaudio-utils				install
pulseaudio-utils-dbg				install
vlc-plugin-pulse				install

dpkg --get-selections | grep oss
> alsa-oss					install
krosspython					install
libkrosscore4					install
libkrossui4					install
libossp-uuid-perl				install
libossp-uuid16					install
libqca2-plugin-ossl				install
libsox-fmt-oss					install

dpkg --get-selections | grep jack
> jacksum						install
libjack-dev					install
libjack0					install
pulseaudio-module-jack				install
pulseaudio-module-jack-dbg			install


sudo /sbin/alsa-utils restart
> * Shutting down ALSA...                                                                                                                                                                                                  [ OK ] 
 * Setting up ALSA...                                                                                                                                                                                                             * warning: 'alsactl restore' failed with error message 'alsactl: set_control:1388: **Cannot write control '2:0:0:IEC958 Playback Default:0' : Operation not permitted'**...                                                         amixer: Invalid command!
   ...done.

If you need further output from some command, please let me know. Thank you for reading and helping.

~Blutorange

---

### Post by partyk1d24 on 2011-10-07
Did you ever figure this out? I am trying to use sound recorder to record from the stream. First I start VLC and start Sound recorder. I open pavucontrol and start VLC. I see VLC show up in the Volume manager but the sound level isn't working, but I try anyway. I set the sound recorder to record and in the recording tab select sound recorder to record from Monitor of internal audio analog stereo. But Sound recorder doesn't record anything.

---

