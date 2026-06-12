---
title: "Webcam question."
date: 2008-07-25
forum: Multimedia Software
---

### Post by Moonfrost on 2008-07-25
My webcam (Logitech Quickcam STX) has a built-in microphone. Is there anyway to make it work on Ubuntu (64bit Hardy Heron 8.0.4.1)? the webcam works but I want to know if I can make the mic work? or should I use a separate microphone?

---

### Post by terry_gardener on 2008-07-25
i have the same webcam quickcam communicate stx and to get the sound to work i just had to select the usb audio option. 

i have only tested mine in skype but it works.

---

### Post by Moonfrost on 2008-07-25
> **terry_gardener said:**
> i have the same webcam quickcam communicate stx and to get the sound to work i just had to select the usb audio option. 

i have only tested mine in skype but it works.

Where is that option? if it's in Skype I don't have it and don't usually use it but if it's in the system itself can you tell me where can I find this option? do I need any Linux specific drivers?

---

### Post by pfeels on 2008-07-25
It's in Skype ... Don't know where to find it otherwise

---

### Post by terry_gardener on 2008-07-25
i am using the ubuntu 8.04 LTS 32bit so might be different for 64bit not sure never used 64bit. 

i found it in 3 different places. 

1. alsamixer -cx (x = card number it is 2 on mine) 
2. right click the speaker near the clock and select open volume control file-change device-usb device. 
3. pulse device chooser - volume control-input devices and find the usb audio device in there. 

hope this helps

---

