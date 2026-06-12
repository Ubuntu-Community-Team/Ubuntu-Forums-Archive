---
title: "Automatically recording sound (on voice activation?)"
date: 2017-08-10
forum: Multimedia Software
---

### Post by bobsta63 on 2017-08-10
Hello all,

I'm working on a new project where by I need to automatically record (think voice activation) sound using an external USB sound card connected to a Ubuntu Linux (or RasberryPi) and once the microphone level drops it will stop recording and then instantly play back the sound...

I've already found a well know application called **areceord** which serves nearly all my requirements, these being:

[list]
[*] Record audio-in (Mic In)
[*] Save/compress the file
[*] Automatically replay the recorded sound through the speakers.
[/list]

**The only shortfall is that I need to automatically record/start on voice activation (so CRON jobs etc are no good) and play back the sound when the audio in starts/mic level goes up, does anyone know if there is a way (with examples if possible)  of a way of doing this or any recommendations...**

What I *think* I need to do is execute this command but only once the mic-in audio level is detected/reaches a certain threshold:

```
arecord -P -t wav repeat_this_back.wav
```

The above command (see [man pages]("http://manpages.ubuntu.com/manpages/precise/en/man1/arecord.1.html")) will record the sound, write the file and then play it back immediately... I just need to figure a way to start and stop the audio recording when the mic-in levels change.

...I'm not set on using **arecord** so if you have another alternative then great but otherwise, **arecord** looks pretty mainstream so if I can use this in combination with something else that would be great!

I plan to intergare the commands into a PHP or Python Script and have it run as a daemon on system start-up on a headless server/device - I can do that bit no problem but just need some advice on how I can achieve the above :)

To give this some context - I'm starting a new open-source project where by I plan to build a Radio Simplex Repeater system, that will run on a Raspberry Pi/Linux based SBC.

A simplex repeater system works by recording radio transmissions from radios/"walkie talkies" and the instantly playing back (transmit) the message back to the user (and all other users on that frequency),it can be used for testing purposes as well as extending radio range - It is therefore essential that the audio is ONLY recorded when the microphone (think voice activation) is triggered and then stops recording (and instantly play back) the recording.

Any help or recommendations would be greatly received :)

Thanks,
Bobby

---

### Post by TheFu on 2017-08-11
TL;DR ... googling .. [https://github.com/MycroftAI](https://github.com/MycroftAI)   [https://github.com/the-raspberry-pi-guy/Artificial-Intelligence-Pi](https://github.com/the-raspberry-pi-guy/Artificial-Intelligence-Pi)

---

