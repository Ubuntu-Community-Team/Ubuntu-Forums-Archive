---
title: "Using a SoundBlaster X-Fi Surround 5.1 Pro as synthesizer module"
date: 2012-10-31
forum: Multimedia Software
---

### Post by PetRoo on 2012-10-31
Hello @all,

I am stuck somehow in using a Soundblaster X-Fi Surround 5.1 Pro as a synthesizer module in Ubuntu Studio (or Ubuntu 12.04.1 canonical):

I would like to use an (admittedly somewhat weak) Lenovo IdeaPad as a synthesizer module for a USB attached midi wind controller (Akai EWI-USB), since the IdeaPad would provide me with several hours of battery operation. Unfortunately I experience a severe xrun problem if I take the jackd for low-latency interconnecting and Qsynth/FluidSynth with the FluidGM.sf2 as soundfont, both in the formerly installed Ubuntu 10.04 and the new 12.04 based Ubuntu Studio. The resulting drop-outs and other audio rendering faults render the system useless for musical application

I bought the said USB attached Soundblaster card because it was mentioned that it would support uploadable sound fonts as well. The idea was to relieve the weak main processor from the actual sound creation work and leave that to the new Blaster.

The Blaster is recognized by the notebook, and I managed to play mp3 over its sound output, but I do not see how to put the device to work for live midi conversion. My expectation: Upload the desired soundfont to the Blaster, and afterwards only send the conversion directives (midi signals) right through to the card that should produce the resultant interpreted instrumental output directly on its own outputs. I had expected that the automatically invoked library for the Blaster would support a respective call by FluidSynth.

But now I am clueless how to realize this setting. Any help is gladly appreciated!

Kind regards,

Peter

---

### Post by PetRoo on 2012-11-04
Well, answering to myself - but in a positive way at least, so some others with same problems might benefit from it.

After several glitches with Ubuntu-Studio I resorted back to good old mainstream Ubuntu 12.04 32-bit as principal version for my Lenovo IdeaPad S12.

After successful installation of the main system I additionally installed the low-latency kernel version and jackd2 (as the newer version).
Mind that the successfully installed low-latency kernel version typically goes to the "older/other versions" grub entry, so you will need to stop grub simply booting stereotypically in order to use it. (left shift key right from boot start)

Now the adaptations that Ubuntu-Studio presumably had made by itself were necessary, derived from the various web pages on the net. I report the changes that worked ***for me***. Any followers might do this at their own risk!

# add root and me-myself as members to the "audio" group

# add to /etc/security/limits.conf three audio lines:

```

@audio        -    rtprio 95
@audio        -    nice -19
@audio        -    memlock unlimited

```# in /etc/pam.d create the file "audio-session" with following content:

```

#%PAM-1.0
session    required    pam_limits.so    noaudit

```# in /etc/pam.d create a file according to your used window manager (for me: "xfce") with following content

```

session include audio-session

```# setup of jackctrl options:

    - deselect D-Bus-Interface
    - turn on real time processing
    - switch on 16-bit-mode
    - choose appropriate hardware for ALSA, incl. the digits after the colon: for my Sb X-Fi => hw 1,1
    - check in the message window if jackd really is invoked and keeps on running 
    - ATTENTION: after a standby/wakup the system erroneously changes the soundcard numbers! Therefore check with "aplay -l" which ALSA numbers are valid; reset them accordingly in the ALSA hardware choice, otherwise you will get trouble by re-invokation of jackd by JackCtrl.

# setup of QSynth:

    - audio interface: jack
    - set correct rates
    - at least for starters: use very few effects


All in all, the rather weak IdeaPad works very stable at latency values of less than 10 msec, with only very occasional XRUNs that don't seem to matter too much. This is true both under XFCE and Gnome Classic (no effects)

Hapyy grooving,

Peter

:-({|=

---

