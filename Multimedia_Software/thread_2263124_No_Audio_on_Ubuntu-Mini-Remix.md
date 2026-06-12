---
title: "No Audio on Ubuntu-Mini-Remix"
date: 2015-01-29
forum: Multimedia Software
---

### Post by dv0dv0 on 2015-01-29
I'm using ubuntu-mini-remix to build a network-booting live OS which loads a remote desktop client and logs users into their virtual desktop environments.

I've gotten everything to work except the audio.

On top of Ubuntu-mini-remix 14.04 I have the following packages installed:

xorg --no-install-recommends
nodm --no-install-recommends
lxde --no-install-recommends
pulseaudio
alsa-base
hptc-manticore_3.2.1_i386
hptc-rdesktop_1.6.0-1.35_i386
vmware-horizon-view-client_2.3.0-_i386-modified

I added the live user 'ubuntu' to the groups audio, pulse, and pulse-access


aplay -l
device_list:286: no soundcards found...

sudo aplay -l
card0: Intel [HDA Intel], device 0: STAC9228 Analog [STAC9228 Analog]
Subdevices: 1/1
Subdevices #0: subdevice #0

card0: Intel [HDA Intel], device 1: STAC9228 Digital [STAC9228 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0


find /lib/modules/`uname -r` | grep snd
finds a ton of modules and

lspci -v | grep -A7 -i "audio"
finds
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
Subsystem: Dell Device 0209
Flags: bus master, fast devsel, latency 0, IRQ 48
Memory at f6ffc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel


both
aplay /usr/share/sounds/alsa/Front_Center.wav
and
sudo aplay /usr/share/sounds/alsa/Front_Center.wav

play nothing

I have everything unmuted and turned up in alsamixer

I don't have a audio system tray icon but I assume I don't need one

Any insight?

I did nearly the same build on lubuntu live 14.04 and the audio worked fine on all of the same hardware, so I figure I'm missing drivers, modules, packages, or something

thanks

---

### Post by dv0dv0 on 2015-02-10
It was a matter of adding the live user to the audio group by editing the /etc/adduser.conf file such that it adds any user created to the audio group.

[COLOR=#333333][FONT=UbuntuRegular]its a simple fix[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]in the unpacked rootfs of the live system, you just need to edit the file /etc/adduser.conf such that the adduser command adds the audio group by default.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]in the file, make sure to add or edit the ADD_EXTRA_GROUPS line such that it reads:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]ADD_EXTRA_GROUPS=1[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]and there may or may not be a line which is commented out which lists the extra groups to be added, you may add whichever groups youd like but for just the audio, edit such that it reads:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]EXTRA_GROUPS="audio"[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]to add multiple groups just separate them with spaces within the quotes, like:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]EXTRA_GROUPS="audio video plugdev"[/FONT][/COLOR]

---

