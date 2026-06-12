---
title: "Playback pure 44100 Hz and 48000 Hz audio without resampling"
date: 2010-03-10
forum: Multimedia Software
---

### Post by RussianNeuroMancer on 2010-03-10
[This is 16 bit / 44100 Hz sample]("http://sharebee.com/361ee93f").
Try to plyback this sample in your favorite music player, and after that try to use command "play SB_test.wav". You see, second part of this file sounds very differently. This is because all your 44100 Hz audio resampled 48000 Hz. It's ok if you watch DVD's (48000 Hz audio), but nasty if you listen CD-Audio (44100 Hz), DVD-Audio or Blu-ray (24 bit / 96000 Hz and 192000 Hz).
My question is: how to playback audio with different characteristics without resampling?

---

### Post by CannibalZerg on 2010-03-14
> You see, second part of this file sounds very differently.
You always can check the momentary freq of your sound card during playback:
```
cat /proc/asound/card0/stream0 | grep Momentary
```
Are you using PulseAuidio? If so, there is no way to play various sound stream (i.e. 44kHz and 48kHz) without resempling.

To avoid resepling you should use alsa directly, without PulseAudio. For example to play your test file from shell:
```
aplay play SB_test.wav
```

---

### Post by RussianNeuroMancer on 2010-03-14
> **CannibalZerg said:**
> You always can check the momentary freq of your sound card during playback:
```
cat /proc/asound/card1/stream0 | grep Momentary
```There is no stream-files in my card0 and card1 folders. Kubuntu 10.04.

> **CannibalZerg said:**
> Are you using PulseAuidio?No.

> **CannibalZerg said:**
> To avoid resepling you should use alsa directly, without PulseAudio. For example to play your test file from shell:
```
aplay play SB_test.wav
```With aplay same problem here. Only "play" correct playback this file.
I'm not very interested in how to play without resampling with a simple cli-player that does not support many formats. How to play without resampling at least through the Phonon-Xine, or even better in all applications? As far as I know, you somehow achieve this in your emu-patch for ALSA. It is possible for other sound cards?

---

### Post by CannibalZerg on 2010-03-14
What model of soundcard do you have?

---

### Post by RussianNeuroMancer on 2010-03-14
Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
Realtek ALC272 ([datasheet](https://docs.google.com/viewer?url=http://download2.dvd-driver.cz/realtek/datasheets/pdf/alc272_datasheet_1.0.pdf)).

---

### Post by CannibalZerg on 2010-03-15
It seems, that your soundcard hardware supports 44.1kHz without resampling (but I'm not sure, because it has only 48kHz sample sync oscillator, while emu-usb products has two independent 44.1kHz and 48kHz oscillators).

I recommend you to use "udial.wav" for testing purposes, you can get udial.ape from here, and decode it to wav:[http://www.hydrogenaudio.org/forums/index.php?showtopic=9772&hl=udial]("http://www.hydrogenaudio.org/forums/index.php?showtopic=9772&hl=udial") (ATTENTION!!! play it at low volume).
If during playback you hear only clear phone-dialing tone, it means that resample 44.1 -> 48 is inactive. And you'll hear very distorted sound at high frequences, if resampling occurs.

Try to run:
```
aplay -D hw:0,0 udial.wav
aplay -D plughw:0,0 udial.wav
```

If both of them produce clean sound, then something wrong with your sound system settings. If "aplay hw:0,0" produce distortions - bad news, it means that hardware/driver can't play "pure" 44.1.

---

### Post by RussianNeuroMancer on 2010-03-15
> **CannibalZerg said:**
> Try to run:
```
aplay -D hw:0,0 udial.wav
aplay -D plughw:0,0 udial.wav
``` 

If both of them produce clean sound, then something wrong with your sound system settings. If "aplay hw:0,0" produce distortions - bad news, it means that hardware/driver can't play "pure" 44.1.Both of them produce clean 44.1 playback.

What can be wrong with system settings?

---

### Post by CannibalZerg on 2010-03-15
Maybe your soundcard doesn't have hardware mixer and system use dmix by default. Try to redefine default alsa device: create file ".asoundrc" (without qoutes) in your home dir and put content into it:
```
pcm.!default {
  type plug
  slave {
    pcm "plughw:0,0"
  }
}

```
Now "aplay udial.wav" should be played without resempling, also try to play sound from other applications.

---

### Post by RussianNeuroMancer on 2010-03-15
> **CannibalZerg said:**
> Now "aplay udial.wav" should be played without resempling,Yes.> **CannibalZerg said:**
> also try to play sound from other applications.No, all Phonone-Xine applications still resample all 44.kHz audio.

---

### Post by CannibalZerg on 2010-03-15
I'm not familiar with Xine settings, so I need some time to test it. At least we find and solve problem with dmix,(but without dmix there is no ability to play several sound streams simultaneously).

---

### Post by RussianNeuroMancer on 2010-03-15
I found option "media.video4linux.audio_device:****plughw:0,0" in ~/.config/kde.org/Phonon-Xine.xine.conf but it's not help - all xine application still resampling sound.

---

