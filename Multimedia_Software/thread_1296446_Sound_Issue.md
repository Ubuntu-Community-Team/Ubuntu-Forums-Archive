---
title: "Sound Issue"
date: 2009-10-20
forum: Multimedia Software
---

### Post by squeak24 on 2009-10-20
HI

I have a strange sound issue, I have tried re-installing Alsa, I have restarted Alsa, I have done numerous things that I have found on various websites but can't seem to get it to work again.

When I first boot my computer up I am getting the login sounds, but when I try and play anything in either Audacity or the media player I am not getting anything.  When I tested the sound in the preferences area I get the following error

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

Does anyone know what the issue is, the sound works with the OSS, but not Alsa, I need to use Alsa as I have it set up for the headphones in Alsa, but with the OSS, it comes through the headphones but also my laptop speakers.

Many thanks in advance.

I have this working now on OSS, with the headphones cutting out as well, but I would like to get the Alsa working as well, any ideas?

OK, I have just tried to do some editing in Audacity, I can't hear anything, the test sound works but not the files that I have on the computer.

Any ideas what is going on hear?

---

### Post by Ulysses361 on 2009-10-22
Please first try the solution from Patola at this location:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/457497](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/457497)

To quote his words:

"Nevertheless, sound is working now. I just noticed that there was a '.pulse-cookie' file in my home directory from october 17. I removed ~/.pulse-cookie and the ~/.pulse directory then rebooted. After this, sound started to work again. If it was an authentication/cookie problem, why there wasn't any error message on this?"

Then reboot and retest sound.


If that does not help, please execute step 1, reboot and then send us output from step 3 and step 4 from the following procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Regards,

Mark Rijckenberg

---

### Post by VertexPusher on 2009-10-22
> **squeak24 said:**
> I have this working now on OSS, with the headphones cutting out as well, but I would like to get the Alsa working as well, any ideas?
Whenever there is more than one sound card present at boot time (USB headsets, USB webcam microphones, TV cards and even MIDI interfaces count as separate sound cards), you have to make a ".asoundrc" file in your home folder to choose one of those as a default device.

You can use the aplay or arecord commands to find out the names of the sound devices in your system. Once you know the names, you can pick one as the default card like this:
```
defaults.ctl.!card "NAME"
defaults.pcm.!card "NAME"
```This is the least intrusive way to change the default sound card. It does not require root privileges, and it leaves any other configuration (e.g. regarding software mixing) unchanged. All it does is overwrite the card parameter (which is 0 by default) with the actual name of a card, so the same card will be chosen even if the card indices change.

---

### Post by squeak24 on 2009-10-22
Just re-installed Alsa as described in the the article and it now works.

This is the second time this has happened in a week, why does this keep on happening, last time I just need to re-install Alsa but that didn't work this time

---

