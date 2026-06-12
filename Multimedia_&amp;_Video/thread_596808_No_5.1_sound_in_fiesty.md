---
title: "No 5.1 sound in fiesty"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by O__________o on 2007-10-29
//newbie alert//

hey, i just installed a new sound card its a creative sound AUDIGY MODEL SB0570.
i get 2.1 sound, but i wanted 5.1 surround sound.
i only have one card, and the onboard card is disabled.
Could anyone help me get surround sound?
it works in windows, but i love my new ubuntu, and i want it to work here aswell.

[SOLVED] thanks alot mate.

---

### Post by cogadh on 2007-10-30
These instructions worked for me with Feisty:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_and_test_surround-sound_speakers_.285.1_and_others.29_with_ALSA](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_and_test_surround-sound_speakers_.285.1_and_others.29_with_ALSA)

It should be noted that by default, unless the audio source is already encoded for 5.1 audio, it will only play on two channels (stereo sound). These instructions will make it so that the stereo signal is replicated across all 6 channels. You can still play true 5.1 audio, you'll just need to specify the "surround51" plug in any application that you use for 5.1 sources (like when playing a DVD movie).

---

### Post by O__________o on 2007-10-30
its works
thanks so much<3
SOLVED.

---

