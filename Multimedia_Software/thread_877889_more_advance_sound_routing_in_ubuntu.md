---
title: "more advance sound routing in ubuntu?"
date: 2008-08-02
forum: Multimedia Software
---

### Post by sumpm1 on 2008-08-02
Hi. I have been running 8.04.1 for about a week. I came from XP. On XP I had a 3rd party driver for my SBLive soundcard that would allow me to do many things with audio routing, and customizing a setup that would allow different programs to have different volumes. The driver made 4 "virtual soundcards" available to the system. Each one of these "virtual devices" could be defaulted to by different programs. So your MAIN sound would go to one device, your MUSIC would go to another, TV IN to another etc... Then all of your sound could be adjusted in a mixer with monitors so you could see WHERE your sound was coming from. I am looking for this 1. to have more control over the sound of my system 2. Increase the volume of the output for the current sound (ability to add GAIN to sound). Can anyone tell me a good place to start looking for any of this functionality?

---

### Post by kostkon on 2008-08-02
> **sumpm1 said:**
> Hi. I have been running 8.04.1 for about a week. I came from XP. On XP I had a 3rd party driver for my SBLive soundcard that would allow me to do many things with audio routing, and customizing a setup that would allow different programs to have different volumes. The driver made 4 "virtual soundcards" available to the system. Each one of these "virtual devices" could be defaulted to by different programs. So your MAIN sound would go to one device, your MUSIC would go to another, TV IN to another etc... Then all of your sound could be adjusted in a mixer with monitors so you could see WHERE your sound was coming from. I am looking for this 1. to have more control over the sound of my system 2. Increase the volume of the output for the current sound (ability to add GAIN to sound). Can anyone tell me a good place to start looking for any of this functionality?
Yes you can do the above now that *Ubuntu* uses *PulseAudio* for its sound. Just go to *Synaptic* and install the *PulseAudio Device Chooser* application (search for the *padevchooser* package in *Synaptic*) and then run it (you will find it in your *Applications -> Sound & Video* menu). It will put a icon in your taskbar. Left click on it and select the *Volume Control* option.

From there you will be able to control the volume for every application and select its output source if you right click on it, etc. So pretty much you will be able to do all of the above. Just play with it a little to learn it.

You can add *padevchooser* to your sessions (*System -> Preferences -> Sessions*) so that it loads everytime you start your system.

Furthermore, it would be good to follow [this how-to here]("http://ubuntuforums.org/showthread.php?t=789578") to setup the sound from applications that use *Alsa* to pass through *PulseAudio* so that you will be able to control them too (and you'll avoid the situation of some applications locking the soundcard).

If you have any question about the above don't hesitate to ask here.

---

