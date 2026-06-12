---
title: "Newbie questions about sound in Xubuntu"
date: 2011-12-11
forum: Multimedia Software
---

### Post by D3ltaz on 2011-12-11
Hello, this is my very first post on this forum! :)

So, the thing is i have never really gotten into any ubuntu (or linux) OS. I have only tried it for some hours to then uninstall it and go back to windows. Now, however, i decided that i wanted to use this OS for real.

My problems are: I cant hear sounds from multiple applications at once. If i open up teamspeak3 then i get no sound in firefox (if i open up firefox after ts3) and i get no sound i teamspeak3 if i opened firefox before.

Also gmusicbrowser does not want to work, it gives me 
```
"Playing error : Configured audiosink alsa is not working. at /usr/bin/../share/gmusicbrowser/gmusicbrowser_gstreamer-0.10.pm line 135."
```I suspect that it has to do with the same things, but even if i start it first i get no sound.

aplay -l gives:
```
xxxxxx@xxxxxxlinux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DX [Xonar DX], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: DX [Xonar DX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Intel [HDA Intel], device 1: VT2020 Digital [VT2020 Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia_1 [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia_1 [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia_1 [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: NVidia_1 [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I am using the Xonar DX, and i got it to be my default soundcard by typing this in /etc/asound.conf
```
pcm.!default {

    type plug slave.pcm {
        type hw card 2 device 0 
    } 

} 
```Bonus question: is it possible to hear my line-in from card1 to my xonar dx, so i hear it in my desktop?
Like a "listen to this device" option.

Thanks in advance, and im sorry if these are totally newbie questions, but i have searched google for hours, resolving some of my problems at least! :)

---

### Post by D3ltaz on 2011-12-11
I found out something about Dmix in alsa. Is there any way to see if it is enabled and even enable it if its disabled? It seems to be what i am looking for. Most of the sites i found said that it is supposed to be enabled by default. Do i have to download any extra stuff for that to work? :)

---

### Post by MoreOrLess on 2011-12-11
The problem is that your asound.conf defines the device as type 'hw' which only works for multiple apps if your card has a supported hardware mixer. Delete the asound.conf file you created.

If you need to ensure the Xonar DX is the default device, use this command (and then restart):
```
echo "options snd-virtuoso index=0" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

---

