---
title: "Help with ALSA and M1010 configuration Ubuntu Studio..No sound"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by caseyg on 2008-01-10
All, I have Ubuntu Studio running with a Delta M1010LT card. I would like to get into interfacing my studio equipment with Ardour. I have done my homework with JACK... Problem being the only sound output I get is through channels 1&2 of the M1010 with a sound configuration of 'playback' set to ICE1712multi. My mainboard audio is disabled. When I set my sound 'playback' to ALSA, I get this error: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

I'm stuck on this. Many hours of googling with no results. Please, help if you have info. Let me know if you need more info.  Thanks Casey :guitar:

/proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: raw midi
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control

/proc/asound/cards
 0 [M1010LT        ]: ICE1712 - M Audio Delta 1010LT
                      M Audio Delta 1010LT at 0xac00, irq 20

---

### Post by caseyg on 2008-01-12
Can anyone tell me if I should be using ALSA, ESD, or OSS with a Delta M1010LT audio card and Ardour.

---

