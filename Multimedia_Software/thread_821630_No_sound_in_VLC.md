---
title: "No sound in VLC"
date: 2008-06-07
forum: Multimedia Software
---

### Post by Retrospekt on 2008-06-07
Sound works fine on youtube and RhythmBox, but I can't hear a thing in VLC.  What do I need to do?

---

### Post by mastermindg on 2008-06-07
Copied:

I use Amarok religiously as my music player. I am able to get sound from multiple applications (amarok, firefox, vlc....) simultaneously.

PulseAudio is now SOP for Ubuntu. In order to give apps priority in the sound scheme you will need to give them access to pulse.

Amarok - Settings - Engine - Output plugin - pulseaudio
Firefox - Install libflashsupport
VLC - Settings - Preferences - Advanced - Audio - Output Modules - Pulseaudio audio output
MythTV -
1) Install libasound2-plugins
2) asoundconf set-pulse
3) Make sure that your audio device is set to alsa:default

If you have any other specific apps, let me know.

---

### Post by Pjotr123 on 2008-06-07
It's also possible that not all codecs are installed. Apply this how-to for that:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and afterwards this one:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by Retrospekt on 2008-06-07
> **Pjotr123 said:**
> It's also possible that not all codecs are installed. Apply this how-to for that:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

and afterwards this one:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

I can't complete step 1 because it says I have drivers installed that are conflicting.  :(

---

### Post by Retrospekt on 2008-06-07
> **mastermindg said:**
> Copied:

I use Amarok religiously as my music player. I am able to get sound from multiple applications (amarok, firefox, vlc....) simultaneously.

PulseAudio is now SOP for Ubuntu. In order to give apps priority in the sound scheme you will need to give them access to pulse.

Amarok - Settings - Engine - Output plugin - pulseaudio
Firefox - Install libflashsupport
VLC - Settings - Preferences - Advanced - Audio - Output Modules - Pulseaudio audio output
MythTV -
1) Install libasound2-plugins
2) asoundconf set-pulse
3) Make sure that your audio device is set to alsa:default

If you have any other specific apps, let me know.

I don't have "Pulseaudio audio output" as an option in VLC.

I did both steps of that tutorial posted above, it did nothing.  :(

---

### Post by wolfen69 on 2008-06-07
[THIS]("http://ubuntuforums.org/showthread.php?t=776739") fixed all my sound issues.

---

