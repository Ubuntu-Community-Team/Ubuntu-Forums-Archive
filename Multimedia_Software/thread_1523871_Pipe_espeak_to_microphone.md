---
title: "Pipe espeak to microphone?"
date: 2010-07-04
forum: Multimedia Software
---

### Post by fraser_m on 2010-07-04
Is it possible to pipe audio from espeak into a microphone device?

I've tried doing
```
sudo espeak --stdout "Hello world." >> /dev/audio
```
but I just get:
```
bash: /dev/audio: Device or resource busy
```

---

### Post by puppywhacker on 2010-07-04
literary you can't pipe sound into the microphone device. A microphone is an input device, not an output device. I assume you want to pipe your espeak to an application first? because espeak should be abled to play to your soundcard directly if libportaudio2 is installed.

```
espeak "Hello world."
```

I think your sample isn't working because --stdout generates a WAV header which isn't understood by the raw sound device (I guess?). Also the sound device is usually controlled by a mixer, so it will always be occupied by it.

I think what you are looking for is to pipe the sound into the soundboard using aplay.

```
espeak "Hello World" --stdout | aplay
```

I never understood the deep internals of the sound cards, I tried to figure out OSS, Alsa and Pulse ... but I get quickly confused, when looking at the deeper internals.

---

### Post by fraser_m on 2010-07-04
What I want is to be able to have espeak do TTS and then play that effectively into the microphone, so that, for example, on Skype, the other person will hear the voice.

---

### Post by Bob535 on 2011-06-18
Bump for same question.

---

