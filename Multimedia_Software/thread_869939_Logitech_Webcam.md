---
title: "Logitech Webcam"
date: 2008-07-25
forum: Multimedia Software
---

### Post by indiana_crook on 2008-07-25
Alright yall what's up?!  I have a webcam, old one, that I pulled from an old computer of mine, it's a logitech, but don't know anything else about it.  I want it to work on Skype but I don't even know where to begin.  I plugged the camera in but don't know how to get it to work...  Anyone willing to lend a fellow a hand?

---

### Post by linuxwizard on 2008-07-25
I don't use Skype but lets see if we can get the webcam to work than worry about getting it to work in Skype. Try using Ekiga see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If the webcam does not work post the results of the command > lsusb

---

### Post by indiana_crook on 2008-07-25
okay it's working, but before we get too far I should tell you that I got the Logitech working and the color was messed up, so I went and bought a phillips.  Works fine in Ekiga but not in Skype, Camorama or Cheese.

---

### Post by linuxwizard on 2008-07-25
You can adjust color, brightness, Hue and so on in Ekiga.

Look over these see if they will help with using Skype.
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by indiana_crook on 2008-07-25
> **linuxwizard said:**
> You can adjust color, brightness, Hue and so on in Ekiga.

Look over these see if they will help with using Skype.
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

yes sir!!  Works GREAT in Ekgia.  But I want to use skype, and maybe pigeon if that's possible.

---

### Post by linuxwizard on 2008-07-25
Pidgin does not support microphone and webcam.

Bottom of page.
[http://developer.pidgin.im/wiki/Using%20Pidgin#VoiceandVideoMicrophoneandWebcamSupportNotImplementedYet](http://developer.pidgin.im/wiki/Using%20Pidgin#VoiceandVideoMicrophoneandWebcamSupportNotImplementedYet)

---

