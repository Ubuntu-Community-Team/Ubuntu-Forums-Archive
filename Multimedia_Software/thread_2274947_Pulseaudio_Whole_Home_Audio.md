---
title: "Pulseaudio Whole Home Audio"
date: 2015-04-23
forum: Multimedia Software
---

### Post by imsherlock on 2015-04-23
Hi All! I've been searching the forums and Google for a couple days now trying to get my whole home audio distribution setup with Pulse. I've used pulse long, long ago but haven't touched it since and some things have changed. What I am trying to do is:

1) I have on PC connected to the network with a  USB audio device to play audio through my home speakers (done)
2) The PC is setup as a pulseaudio source (sink? not sure on the nomenclature here) so another device can send audio to it (not sure how to do this 100%)
3) The second PC I want to connect to the first PC over the network using a tunnel/rtp (not sure which one to use)
4) The second PC has bluetooth to allow connections from remote devices to forward audio to the other PC

I've got some basic configuration done with the first PC pulseaudio defaults.pa here:[INDENT]load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1;192.168.1.0/24 auth-anonymous=1[/INDENT]
[INDENT]load-module module-zeroconf-publish[/INDENT]

And on the second PC default.pa:[INDENT]load-module module-zeroconf-discovery[/INDENT]
[INDENT]load-module module-bluetooth-policy
    load-module module-bluetooth-discover
    load-module module-tunnel-sink sink_name=homeaudio server=pc1 sink="alsa_output.usb-0d8c_C-Media_USB_Audio_Device-00-Device.analog-stereo"[/INDENT]

I was also able to get the second PC to connect my Nexus 7 manually, but I'd like have this happen automatically with any device. Any ideas?
Cheers!

---

### Post by dino99 on 2015-04-23
i'm not sure about what you are glancing at:
- there is specialized ubuntu releases like xbmc and ubuntustudio, which seems to be what you request.
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
[http://manual.ardour.org/setting-up-your-system/platform-specifics/ubuntu-linux/](http://manual.ardour.org/setting-up-your-system/platform-specifics/ubuntu-linux/)
[http://kodi.wiki/view/HOW-TO:Install_XBMC_for_Linux](http://kodi.wiki/view/HOW-TO:Install_XBMC_for_Linux)
[https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio)

---

### Post by imsherlock on 2015-04-23
So both PCs are headless and I'd like them to remain that way otherwise I've got to attach a monitor to each. XBMC is more than what I'm looking for, and one of the systems probably couldn't handle those graphics (I'm reusing old equipment).
Any other suggestions or guides? I think I'm looking more a setup on PulseAudio. So if someone has done either of these things (server or bluetooth client) it would be helpful.

---

