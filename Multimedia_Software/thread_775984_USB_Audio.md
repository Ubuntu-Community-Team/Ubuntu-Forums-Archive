---
title: "USB Audio"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Don_Shifty on 2008-04-30
Hello
I have a Sony CMT-N333NT Micro Hi-Fi component system connectet to my laptop via USB, i'm running on Hardy 8.04. Now I would like to use the hi-fi system as a default audio output instead of my laptop speakers. Hardy provides default audio codecs, but with them activated all sounds played by Firefox or VLC are still heard trough the laptop speakers. 
On the other hand Amarok automatically uses the usb output, even with the alsa option selected in the sound menu. 
I couldn't find linux drivers for my CMT-N333NT, so does anyone have an idea how i could tell linux to use the usb output, if connected....
thanx a lot
shifty

---

### Post by Don_Shifty on 2008-04-30
correction: i don't know what changed, but now not even amarok playes via usb anymore..... !?!

---

### Post by Don_Shifty on 2008-05-06
anyone? help please?

---

### Post by deshotel on 2008-05-12
I am also on Hardy now (Acer laptop) with no other problems except my Samsung USB speakers. I had lots of GUI problems with Gutsy so am glad to have moved on. But the speakers only play the OS startup sound (and even replay it repeatedly by re-inserting the usb plug) and will give the TEST sound dignal an "all clear" ring as if I am on the way but NO sound ever comes out (mp3s, flv)from Mplayer or VLC...maybe I will try to use other programs and see if one or another will play nice with my usb speakers, which did in fact work fine in Gutsy.

I am surprised no one has even attempted to help you (and now me too!)...are we on our own? Oh dear, Toto we are not in Kansas anymore!

---

### Post by deshotel on 2008-05-12
Got both speakers working using Totem and PulseAudio (Manager). It was real simple, no cleverness required. Had to stop using VLC as it did not pick up the USB speakers.
:)

---

### Post by Don_Shifty on 2008-05-20
hey deshotel!
thanks for your help! mabye i'm too much of a noob but i still didn't get it working... i put all the settings in the preferences->sound menu to USB-Audio and had the PulseAudio Device Chooser running and only rythmbox played via the usb speakers! amarok, firefox and all the rest played via the laptop speakers! if i put all the sound settings to pulseAudio nothing really works and if i want to play the testsound i get the following error:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect: Connection refused!

the same happens if i want to acces the pulse audio volume control or volume meter, i get an error:
Connection failed: Connection refused

what is wrong and how did you put your sound menu, pulseAudio and player settings?

thanks a lot for your help!
cheers shifty

---

