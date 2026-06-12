---
title: "Sound Help"
date: 2008-08-31
forum: Multimedia Software
---

### Post by Rolaulten on 2008-08-31
Hello, 
I'm still fairly new to Ubuntu, and must say that I am enjoying it. That said I am running into a bunch of strange sound problems. The first is that I only get sound through my usb headset (its a Logitich) and if I unplug that in the hopes of getting sound though the main computer speakers there is no sound. Next, within the usb headset I have no way to change the sound volume levels (nether the keyboard buttons, the icon next to the clock, or in the sound preferences, the sidebar just does not want to move). Lastly, I get audio from anything on my local hard drive (music and such) however whenever I go to internet stream, youtube, shoutcast, etc, I have no audio.

SO, specs, I am running a Dell XPS 400, with no changes to the sound card (new video card and more ram).
The output of aplay -l is ```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thank in advance for any help
-Rol

---

### Post by cariboo on 2008-08-31
If you double click on the sound icon in the op panel what is the default sound device, is it your headphones or your sound card? If it is the headphones, change it to your sound card.

Jiim

---

### Post by wolfen69 on 2008-08-31
try installing libflashsupport.

---

### Post by Rolaulten on 2008-08-31
Ok, I feel like a nub, so if to switch between my main speakers and the the usb headset just go system>preferences>sound and change everything there to the USB headset or vice versa ?
-Rol

---

