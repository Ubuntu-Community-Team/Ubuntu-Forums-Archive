---
title: "PulseAudio not picking up my laptop mic"
date: 2009-11-18
forum: Multimedia Software
---

### Post by Keatonguy on 2009-11-18
Hi folks. I'm trying to set up Skype on my HP Mini 110, but the built-in mic isn't getting picked up by Pulseaudio, which appears to be the only sound server Skype supports. Unfortunately, I don't have any more information than that, because Karmic's sound config GUI has been replaced with one without diagnostic tools... Does anyone know a tool I can use in place of it/a way to get the old version? And more importantly, can anyone help me figure out the issue?

---

### Post by gradinaruvasile on 2009-11-18
Hmmm.. Did u try changing in the input tab the connector (see attached screenshot)?

I work with a Dell D630 and i have 2 inputs: Mic 1 is the headphones mic, Mic 2 is the internal mic. And it doesnt switch them automatically when i plug in the jack, only the output gets rerouted to the headphones. So i have to select the mic i want to use. Maybe its your case also...

Skype supports ALSA too, but if PulseAudio is active, only that option is available. Also Skype is one of the handful programs that work perfectly with Skype in Karmic (based on my personal observations only).

---

### Post by Keatonguy on 2009-11-18
That dropdown menu in your screenshot for picking the input doesn't show up on my machine. The only port on my netbook here is marked with both a headphones and microphone symbol, so I presume it's supposed to be universal. Nevertheless, the sound level sensor on that screen aren't showing any sound coming in the microphone, even when amplified over 200%, so I can only presume it doesn't know where to look for input.

---

### Post by ke4jgx on 2009-12-08
download the alsa backports,the alsa mixer and dependencies and then adjust via the alsa gui your mics.. all the way to 100 .. should work fine.. It worked on mine and I can use skype and all the audio progs I have.

---

### Post by Ausmosis on 2009-12-08
Its a known issue with some netbooks particularly the HP mini 110. I have the exact same issue. some folks have tried the alsa backports which seems to have resolved the issue but I am also aware that it hasn't work for everyone. I've yet to test it myself but might give it a shot later tonight.

---

### Post by omunozsj on 2010-01-13
On a HP tx1220us, Karmic, you can't access important settings through Volume Control GUI (like ATAPI MIC). Instead of using that GUI or downgrading, you need to use alsamixer from a command line terminal:

% alsamixer -V all

Hope it helps...

---

### Post by zanox on 2010-01-14
> **gradinaruvasile said:**
> Hmmm.. Did u try changing in the input tab the connector (see attached screenshot)?

I work with a Dell D630 and i have 2 inputs: Mic 1 is the headphones mic, Mic 2 is the internal mic. And it doesnt switch them automatically when i plug in the jack, only the output gets rerouted to the headphones. So i have to select the mic i want to use. Maybe its your case also...

Skype supports ALSA too, but if PulseAudio is active, only that option is available. Also Skype is one of the handful programs that work perfectly with Skype in Karmic (based on my personal observations only).

in my netbook, pulse audio monitor picks up audio, but settings window don't. External mic works perfectly. Suggestions?

---

### Post by DCWhitbeck on 2012-07-03
> **Keatonguy said:**
> Hi folks. I'm trying to set up Skype on my HP Mini 110, but the built-in mic isn't getting picked up by Pulseaudio, which appears to be the only sound server Skype supports. Unfortunately, I don't have any more information than that, because Karmic's sound config GUI has been replaced with one without diagnostic tools... Does anyone know a tool I can use in place of it/a way to get the old version? And more importantly, can anyone help me figure out the issue?

I have the same issue with my Acer Laptop using Skype. The sound settings wount even let me do anything with the microphone its all greyed out. I downloaded the Alsa apps I have microphone adjust options buut stiill doesnt give me the ability to use it in Skype.

Found external webcam from logiitech WITH a built in mic and everything works however it would be less of a hassle if I could use my built in webcam with mic.

---

### Post by wildmanne39 on 2012-07-04
Hi, this is an old thread so it has been closed, please start a new thread with a descriptive title.
Thanks

---

