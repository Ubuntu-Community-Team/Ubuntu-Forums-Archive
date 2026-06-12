---
title: "Logitech Desktop Microphone (AK5370) - Refuses to work - Tried everything"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by FusionXN1 on 2006-07-28
I have been everywhere to try and fix this! Googled and tried a lot of things, Skype hijack, I downloaded the skype beta, found several pages "with fixes" but it wont work.

Can anyone help me? Its one of the things that's making me to decide to go back to windows as I use skype... a lot. thanks :)

---

### Post by stummies on 2006-07-28
I have posted about this same issue yesterday, I have the exact same microphone, usb, and a SB Audigy 4, I've been trying to find information about how to get Teamspeak2 to use my SB for output and my AK5370 for input.  I even tried the skype hijack thing (musta been same page).  I would be interested in finding a solution.

---

### Post by FusionXN1 on 2006-07-29
*bump* Anyone help us out?

---

### Post by kendals on 2006-09-04
Count me in. Just spent $50, and tried numerous solutions ([http://crache.net/blog/2006/05/06/logitech-usb-desktop-microphone-in-linux/](http://crache.net/blog/2006/05/06/logitech-usb-desktop-microphone-in-linux/), [http://forum.skype.com/index.php?showtopic=10858](http://forum.skype.com/index.php?showtopic=10858) etc). Nothing has worked :(

Here's my sound devices:

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@kenny:/home/kendal# arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 1: Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 2: Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 3: Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [AK5370          ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Any ideas, anyone?! Running Dapper 6.06 Latest... :(

---

### Post by kendals on 2006-09-17
Bump!

---

### Post by bliind on 2007-01-21
It works for me in Skype, just go into the preferences and switch to the AK5370..

However, I can't get the microphone to work in any other programs :|

---

### Post by Bad_Byte on 2007-02-04
I have the same mic, after some testing I unplugged it and plugged in the old headset mic. The volume is extremely low. Shame that since it is a great mic when used in windows.

---

### Post by daradib on 2007-02-08
I have the same mic. Any help?

It is recognized as a sound mixer. It seems to show some signal if I shout into the microphone.

---

### Post by ThatOtherGuy435 on 2007-02-28
I am also trying to get this microphone to work. Would very much apreciate any help to be had out there!

-TOG

---

### Post by Stebalien on 2007-03-24
Fix:  Double click on the volume applet, File>Change Devices>AK5370, and rais the volume as high as it goes.

---

### Post by Bazzaah on 2007-06-19
> **Stebalien said:**
> Fix:  Double click on the volume applet, File>Change Devices>AK5370, and rais the volume as high as it goes.

worked for me  - thanks.

---

