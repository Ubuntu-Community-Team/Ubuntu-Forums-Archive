---
title: "can't record with Indigo I/O IO card"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by lusth on 2007-06-18
Hi all,

I just got an indigo IO card for recording sound samples with my laptop. Using the
latest alsa drivers and firmware, I got my system (edgy) to recognize the card.
I can play via the card but I can't record. Kmix/alsamixer does not show the mic or
any devices for which I can set the capture mode (all I can do is adjust the
volume). Echomixer looks similar, although I couldn't find any documentation
on it to really know.

Running

    cat /proc/asound/devices

yields

  2:        : timer
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
  5: [ 0]   : control
  6: [ 1- 0]: digital audio playback
  7: [ 1- 0]: digital audio capture
  8: [ 1]   : control
  9: [ 2- 0]: digital audio playback
 10: [ 2- 0]: digital audio capture
 11: [ 2]   : control
 12:        : sequencer

Card 2 is the indigo io. Running

    ecasound -i /dev/dsp2 -o out.wav

records silence. I also can't hear the mic via the headphones when
both ar plugged into the card.

Any ideas or suggestions?

Thanks,

john

---

### Post by lusth on 2007-06-19
Figured it out. Seems you can't plug a microphone directly into the Indigo IO; you need to plug the microphone into a pre-amplifier and then feed the output of the preamp to the audio card.

---

