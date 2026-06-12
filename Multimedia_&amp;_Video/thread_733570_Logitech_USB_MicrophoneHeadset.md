---
title: "Logitech USB Microphone/Headset"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by mlyons16 on 2008-03-23
I have a Logitech USB microphone/headset combo that I bought predominately for use with Skype. I plugged it in and ran the lsusb command in terminal and it is recognized.

I go to System > Preferences > Sound... 

under Sound Events, I have set: autodetect.. but when the headset is plugged in.. i put it to USB audio. The test works fine.. i can hear the test chime well from the headset earphones.

under Audio Conferencing, I have set: usb audio on soundplayback and capture .. but when i press test on either, and start talking.. i get the message:

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

Can someone help

---

### Post by Mikeoak on 2008-03-24
I have the same head set and it works great with Skype.

Under Skype/ Options/Sound Devices make sure in Sound in and Sound out that the Logitech USBHead(plughwHeadset) is selected.  

Also, it might make a difference if the headset is plugged in before you boot up...

---

### Post by mlyons16 on 2008-03-24
> **Mikeoak said:**
> I have the same head set and it works great with Skype.

Under Skype/ Options/Sound Devices make sure in Sound in and Sound out that the Logitech USBHead(plughwHeadset) is selected.  

Also, it might make a difference if the headset is plugged in before you boot up...

Alright, I'll give that a try. Are there any other suggestions in terms of settings?

---

### Post by Mikeoak on 2008-03-24
No, it's really simple once you know that you have to check the options/ under Skype.  The other setting for Logitech does not work on my system.  Also, it does not appear that you 
have to have the USB headset plugged in when you boot up.

---

### Post by mlyons16 on 2008-03-24
> **Mikeoak said:**
> No, it's really simple once you know that you have to check the options/ under Skype.  The other setting for Logitech does not work on my system.  Also, it does not appear that you 
have to have the USB headset plugged in when you boot up.

Ya, use the command prompt:

```
 lsusb 
```

That detects any USB devices. My headset was detected no problem last night and for the most part, the Sound settings look all in check to me... but I never thought to try out the Skype settings and make sure they are in check. I'll try that tonight.

It's only a USB headset... Ubuntu is modern enough that it should have the drivers to run it pretty seamlessly I'd think.

---

### Post by Mikeoak on 2008-03-24
You would think.  Another program that works well with the USB headset is Audacity and similarly you have to open Audacity>preferences and make sure you have selected the Logitech USB headset for playback and recording.

---

