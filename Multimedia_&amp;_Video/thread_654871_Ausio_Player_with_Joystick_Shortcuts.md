---
title: "Ausio Player with Joystick Shortcuts?"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by johnsonfarms on 2007-12-31
I am looking for an audio player to do transcription work with but I need to be able to use my USB foot pedal to play/pause/forward/reverse, it shows up as a joystick in linux. I have been try Amarok but i can't seem to use the pedal with it. Does anyone have any suggestions?

---

### Post by frogitts on 2008-05-02
Similar wish here: I have a USB NES controller, and I'd love to be able to set a global shortcut so that when I press two buttons on the controller, my NES Emulator would start. Does anyone know how to get Ubuntu to recognize 'keystrokes' or other control from USB devices? I'm on a laptop, so I don't have a USB keyboard, but it would seem to me that, at least in my case, and maybe with johnsonfarms' case too, we should be able to take input from our usb devices and turn them into keystrokes to get done what we need to get done.

I've been playing around with joy2key, but I don't even know what it's supposed to do. I've got it to the point where if I type in "joy2key -dev /dev/input/js0 -terminal -buttons a" it'll go through a calibration test and then every time I press button0, it displays an "a" in the terminal window. Not useful.

The odd part of all of this is that the gfce nes emulator and jscalibrator both work perfectly with the gamepad. It'll grab the keys when I define a gamepad, but ccsm (Advanced Desktop Effects Settings) won't grab the input, and I don't know how to represent the keys from the device, so I can't define them that way in gconf-editor. Anyone know how to grab the input codes (or whatever you call them!) from a usb device?

---

### Post by frogitts on 2008-05-05
Well, here's a partial answer to my own question. The windows program JoyToKey (not joy2key) works exactly as I want it to...but only in Windows. I can run it in Wine, but then the input grabbed from the USB device (read:gamepad, joystick) only affects the Wine window, not anything else. Needless to say, this is not what I want to have happen. I guess we just need a port of JoyToKey for Ubuntu. Or maybe a joy2key that actually works.

---

