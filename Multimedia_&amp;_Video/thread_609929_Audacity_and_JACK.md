---
title: "Audacity and JACK"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2007-11-11
I installed Ubuntu Studio a couple of weeks ago--not because I especially NEED fancy audio and video apps right now--more for the fun of trying to get it all working...

After wrestling with JACK for what seemed like forever, I concluded that the only way to get it to run properly (without crashing, etc) was to set it on either playback OR record--but not duplex.   My Audigy SE is just not up to the task, I don't think...

Last week I got Audacity to play through JACK--but today, for some reason, it wont.  I get that 

> "Error while opening sound device. Please check the output device settings and the project sample rate."

error message.    Both Audacity and JACK are set for 44100, and I've gone into the Audacity preferences and selected the "Jack Audio Connection Kit: alsa_pcm option" under 'playback'...

I'm stumped...  Audacity will play and record fine through ALSA if I don't have JACK running at all...   And all my other audio apps seem fine...

(And while I have your attention, why does the JACK gui look so snarky?!)

[I've attached a screenshot of my settings]

---

