---
title: "Soundsticks don't work after upgrade to 8.10"
date: 2008-12-29
forum: Multimedia Software
---

### Post by thomas9129 on 2008-12-29
I had been using ubuntu 8.04 and played movies and music through Harman/Kardon Soundsticks via a USB port.  They worked fine.  After upgrading to 8.10 I get this message when I test the soundsticks:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

Sound from my computer itself is fine.  So I'm stuck.  Any help?

---

### Post by kostkon on 2008-12-29
> **thomas9129 said:**
> I had been using ubuntu 8.04 and played movies and music through Harman/Kardon Soundsticks via a USB port.  They worked fine.  After upgrading to 8.10 I get this message when I test the soundsticks:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

Sound from my computer itself is fine.  So I'm stuck.  Any help?
Yes, you need to set them as the default output device in *PulseAudio*. In 8.10 all sounds pass through *PulseAudio*, i.e. it has the total control of the audio on the Desktop (whereas in 8.04 ALSA sounds used the card directly).

Anyway, firstly, set your sound playbacks to *Autodetect* in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*).

Then you need to install the *PulseAudio Device Chooser* utility, using *Synaptic*. Run it and it will put its icon in your taskbar. Left-click on its icon and select *Volume Control...*

In the *Output Devices* tab you should see all of your audio devices listed (including your USB speakers). Right-click on your speakers and enable the *Default* option to set them as the default audio output device in your system.

If it happens that a few applications don't produce sound anymore, it means that they don't try to output their sound through your speakers. The solution is to manually tell them to use the speakers.

To do this, open the *PulseAudio* volume control again and in the *Playback* tab you will see all your applications running listed there (only the ones that produce audio). Right-click on the one you want and select *Move Stream...* and in the list that appears select your speakers to send the sound of this application to your speakers.

*PulseAudio* will remember your choice the next time you run this application again.

Thus, you get great flexibility on deciding which audio device you want each of your applications to use to output their sound.

If you want, you can set the *PulseAudio Device Chooser* utility to start automatically every time you log-in from its preferences.

Hope that helps.

---

