---
title: "Asus Xonar stx Soundcard"
date: 2013-01-12
forum: Multimedia Software
---

### Post by MacOsX74 on 2013-01-12
Hi!

Need help with this.
Have an Xonar stx card  and Ubuntu server 12.04.
The card works fine in xbmc but not in Spotify or Rhythmbox. No sound from the web either.
I have removed Pulse audio because it messed up xbmc. My onboard ALC892 card works fine in both Spotify and xbmc.
Any suggestions?


It shows up in Gnome alsa mixer but i cant get any working test tone in Gstreamer properties

---

### Post by eddier on 2013-01-12
Try installing Mudita24 from the repositories.

 Start it up and select the "Analog Volume" tab,then push the volume sliders all the way up.

Thats what I have to do whenever I Install/Reinstall a tryout Distro. I am using an MAudio Audiophile 24/96,with onboard sound disabled in the bios.

No messing with Pulse etc. all default installs.

eddie

---

### Post by MacOsX74 on 2013-01-13
> **eddier said:**
> Try installing Mudita24 from the repositories.

 Start it up and select the "Analog Volume" tab,then push the volume sliders all the way up.

Thats what I have to do whenever I Install/Reinstall a tryout Distro. I am using an MAudio Audiophile 24/96,with onboard sound disabled in the bios.

No messing with Pulse etc. all default installs.

eddie

That app dosent start on my system. Something special I have to do?

Dosent support my card. thats why it dosent start.

---

### Post by Yellow Pasque on 2013-01-13
Since you've removed pulseaudio, you have to tell ALSA which soundcard you want to be the default. The easy/lazy way to do it is to disable your onboard sound in the BIOS. The more complex (but still fairly easy) way to do it so to add a line like:
```
options snd-oxygen index=0
```
to /etc/modprobe.d/alsa-base.conf
(Note: it may be snd-virtuoso instead of snd-oxygen. Look at 'sudo lspci -v' and see which kernel module it lists for your Xonar).

---

### Post by MacOsX74 on 2013-01-14
> **Temüjin said:**
> Since you've removed pulseaudio, you have to tell ALSA which soundcard you want to be the default. The easy/lazy way to do it is to disable your onboard sound in the BIOS. The more complex (but still fairly easy) way to do it so to add a line like:
```
options snd-oxygen index=0
```to /etc/modprobe.d/alsa-base.conf
(Note: it may be snd-virtuoso instead of snd-oxygen. Look at 'sudo lspci -v' and see which kernel module it lists for your Xonar).

Gonna try this this weekend when I get back home.
I´m getting back with results.
Thanks!

---

### Post by MacOsX74 on 2013-01-17
That didnt seem to work or i did something wrong.
Now i dont hear the soundcard click when i reboot. I did that before.
And now it dosent show in aplay -l anymore.

I added 
options snd-virtuoso index=0 to /etc/modprobe.d/alsa-base.conf

This is from sudo lspci -v

03:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
    Subsystem: ASUSTeK Computer Inc. Virtuoso 100 (Xonar Essence STX)
    Flags: bus master, medium devsel, latency 32, IRQ 10
    I/O ports at d000 [size=256]
    Capabilities: [c0] Power Management version 2
    Kernel modules: snd-virtuoso

This is from aplay -l

```
xbmc@xbmc-server:~$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: PCH [HDA Intel PCH], enhet 0: ALC892 Analog [ALC892 Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: PCH [HDA Intel PCH], enhet 1: ALC892 Digital [ALC892 Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 3: HDMI 0 [HDMI 0]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 7: HDMI 0 [HDMI 0]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 8: HDMI 0 [HDMI 0]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: NVidia [HDA NVidia], enhet 9: HDMI 0 [HDMI 0]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
xbmc@xbmc-server:~$ 

```My onboard audio works just like before
Any more thoughts?

Removed options snd-virtuoso index=0 to /etc/modprobe.d/alsa-base.conf and now it shows in aplay -l but no sound.

---

