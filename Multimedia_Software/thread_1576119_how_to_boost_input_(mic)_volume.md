---
title: "how to boost input (mic) volume?"
date: 2010-09-16
forum: Multimedia Software
---

### Post by nerdy_kid on 2010-09-16
my laptop's mic is not nearly loud enough for any purposeful use; so after some fishing I got a 50 db software boost by adding this to .asoundrc:
```


# creates a new alsaboost device that takes over sound card
pcm.alsaboost {
    type asym
    playback.pcm {
        type hw
        card 0
    }
    #software gain upto 50dB for digital microphone
    capture.pcm {
        type softvol
        slave.pcm "hw:0,0"
        control {
            name "+50dB Mic Capture Volume"
            card 0
}

```
found it on a howto some where.  it works fine except:  pulseaudio does not like it a bit.  once my audio card suspends/turns off pulseaudio gets screwed up and only shows the software "card" and not my real hardware card.  So my question is this:  is there a way to make the virtual alsa device "sleep" for a set time?  if not; is there a prettier way of boosting my mic's volume?  thanks :)

---

### Post by nerdy_kid on 2010-09-16
never mind, found that paman had it.

---

