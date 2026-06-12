---
title: "Pulseaudio?? ***Please Help***"
date: 2009-07-05
forum: Multimedia Software
---

### Post by acidpiper on 2009-07-05
Please help- I have recently changed from XP and have been using ubuntu for the last two weeks - I am having a problem with my sound - specifically pulseaudio- Before i continue  I HAVE READ THE [COLOR=navy]_**[SIZE=4][B]Comprehensive Sound Problem Solutions Guide** v0.5e[/SIZE][/B]_[/COLOR]- and still have issues. i am using an ATI 4670 via HDMI (which i want for all my sound) i have an nvidia sound card on my motherboard to.

**Whats The problem?**- **i HAVE** sound when playing dvds videos and mp3s which tells me that the ALSA drivers are fine (is this a correct assumption) but have** NO** system sounds (themed ubuntu sounds like start-up drums etc.) and **NO game** sounds**[COLOR=black] and i am not [/COLOR]getting sound from** **Flash Player **either. In Sound preferences i did the testing on the sound devices the only one working is my graphics card i assume this is because that it is the only device plugged in to a sound source - **my TV via HDM**I. All the other devices when tested there is no sound- 

The way i have understood it from the reasearch i have done to fix this issue is that pulseaudio manages the sound for you - IS THIS CORRECT AND SHOULD I BE GETTING SOUND FROM IT WHEN IT IS TESTED.

Spec: ubuntu 9.04-64, Quad core, ATI Radeon 4670 HDMI, ASUS MB 

Any help would be greatly appriciated thanks

---

### Post by kostkon on 2009-07-05
First of all, you need to put your sound playbacks in your sound preferences (*System &#8594; Preferences &#8594; Sound*) back to *Autodetect*.

Then you need to install the *PulseAudio Device Chooser* Utility (from *Synaptic*). Run it, right-click on its icon in your system tray and select *Volume Control*.

In the *Output Devices* and *Input Devices* tabs you will be able to set a default input and output audio device for your system. Just right-click on the one you want (in your case your ATI 4670) and then enable the *Default* option.

To make *Flash* send its sound to your ATI, put a *Flash* video playing in *Firefox*, then open the *PulseAudio* volume control again and select the *Playback* tab. You should see the audio stream of *Flash* listed there. Right-click on it, select *Move Stream...* and in the list that will appear select your ATI.

For more info, check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

Hope that helps.

---

### Post by acidpiper on 2009-07-05
Aaah its not picking up my HDMI sound card only the motherboard one- i went to disable it(M/B one)  now  it says Null output any ideas

---

