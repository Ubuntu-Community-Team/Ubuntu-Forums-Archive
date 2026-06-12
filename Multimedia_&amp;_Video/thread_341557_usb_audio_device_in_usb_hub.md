---
title: "usb audio device in usb hub?"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by elektronaut on 2007-01-18
Hi,

I've got a laptop with only two usb ports. When I come home I put it into a docking station that blocks the sound jacks. So I bought a usb audio device, which works (not for all applications, but that's another story...) as long as it is plugged directly into the laptop. As I need to connect the laptop with more than two usb devices, I'm using a hub. 
The problem is that neither my bluetooth stick nor the usb audio stick seem to work in the hub, but I can only plug in one of them directly, as I need the other usb port for the hub.

In order to get the usb audio stick working in the first place (directly plugged into the laptop), I edited '/etc/modprobe.d/alsa-base', now the last section is:
```
# Prevent abnormal drivers from grabbing index 0
options snd-hda-intel index=0
options snd-usb-audio index=1

```

The usb audio device (in the hub) is recognized:
```
$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC883 Analog [ALC883 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 6: Si3054 Modem [Si3054 Modem]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: default [C-Media USB Headphone Set  ], Gerät 0: USB Audio [USB Audio]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

```
But if I go to the Gnome menu and choose System -> Settings -> Audio and try to test the usb device, an error shows up: ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Couldn't neither read the settings from the resource nor write to the resource.
```[I](translated from german)
[/I]

So is there a possibility to get a usb audio device working in a hub?

---

### Post by haiku99 on 2007-01-18
is your hub powered??  Some USB devices pull too much current to work in a non-powerd hub.  Also, FWIW there is some good info on switching between onboard and USB audio in this thread:
[http://ubuntuforums.org/showthread.php?t=312040](http://ubuntuforums.org/showthread.php?t=312040)

---

### Post by elektronaut on 2007-01-21
Thanks for the link, that's an interesting thread. But I don't see anything related to the hub story. The hub is powered by it's own ac adapter, so that shouldn't be a problem.

---

