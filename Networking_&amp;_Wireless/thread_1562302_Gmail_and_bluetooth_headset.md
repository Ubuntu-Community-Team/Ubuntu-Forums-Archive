---
title: "Gmail and bluetooth headset"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by kid1000002000 on 2010-08-27
Gmail and google voice is something of a great combination for me.  Now, I would like to use it with the bluetooth headset that has always served me well when connected to my phone.

My computer will pair with my headset, but no audio is ever transferred to or from the device.  There is nothing bluetooth-related that shows in gmail's chat settings either- only internal devices can be selected.

Thanks for the help

---

### Post by kostkon on 2010-08-27
What devices are listed?

Nevertheless, try installing and using the *PulseAudio Volume Control* utility.

---

### Post by kid1000002000 on 2010-09-01
Only the following devices are listed under my sound preferences:

"(monitor) Internal Audio Analog Stereo" and "(monitor) Simultaneous output to Internal Audio Analog Stereo"

For these options, I have output listed to either "analog output" or "analog headphones."

Neither of which send audio or receive from my bluetooth headset (motorola h710).  The headset pairs just fine with linux and is listed as a "headset" under bluetooth properties.

Anybody have ideas on how to port audio to my bluetooth device?

---

### Post by klausner on 2010-09-19
> **kid1000002000 said:**
> Gmail and google voice is something of a great combination for me.  Now, I would like to use it with the bluetooth headset that has always served me well when connected to my phone.

My computer will pair with my headset, but no audio is ever transferred to or from the device.  There is nothing bluetooth-related that shows in gmail's chat settings either- only internal devices can be selected.

Thanks for the help

Have you tried:
> Left click on the volume control icon in your tray
Right click on "Sound Preferences"
Select the "Hardware" tab
Included in the choices should be your regular sound card (chip), and your bluetooth device. Just select the bluetooth instead of the sound card.

---

### Post by kid1000002000 on 2010-09-19
Bluetooth is not listed as a sound device there...

---

### Post by klausner on 2010-09-19
> **kid1000002000 said:**
> Bluetooth is not listed as a sound device there...

Then your bluetooth hardware isn't being seen. Possibly an install problem, or a pairing problem.

You did pair your bluetooth device to the PC, didn't you?

---

### Post by kid1000002000 on 2010-09-23
I did.

And actually, something finally sort of worked for the first time in like a year.  I turned the headset off, then back on, and now I cant get it to work again.

I completely re-paired the headset w/ gnome's bluetooth manager, and for whatever reason now it will randomly show up or not show up as a sound device in my sound preferences.  When it shows up, it works fine, when it doesn't, well, I think its an issue with the bluetooth manager or bluez.  I have this same problem now with my bluetooth mouse, where I have to set each up as a NEW device each time, unplug the wireless bluetooth dongle several times and plug it back in before it can recognize the device, then sync correctly...

grr

---

