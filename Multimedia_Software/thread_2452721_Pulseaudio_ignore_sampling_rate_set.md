---
title: "Pulseaudio ignore sampling rate set"
date: 2020-10-27
forum: Multimedia Software
---

### Post by michau2020 on 2020-10-27
after I change the file:[COLOR=#0000FF][FONT=Ubuntu]/etc/pulse/deamon.conf  [/FONT][/COLOR]to:
```

[COLOR=#006400][FONT=Monaco]resample-method = src–sinc–best–quality
default-sample-format = s24le
default-sample-rate = 48000
alternate-sample-rate = 44100[/FONT][/COLOR]

```
still don't see any difference because command
```
[COLOR=#008000][FONT=Ubuntu]pacmd list-sinks | grep sample[/FONT][/COLOR]
```
still giving me: [COLOR=#0000FF][FONT=Ubuntu]sample spec: s16le 2 k 44100 Hz

[/FONT][/COLOR][FONT=Ubuntu]I can proove that soundcard should work with much higher rate.
In [/FONT][FONT=Ubuntu]/proc/asound/carda/codec#2 there are lines:[/FONT][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]```
[COLOR=#006400][FONT=Monaco]rates [0x5ec]: 16000 22050 44100 48000 88200 96000 192000
bits [0x1f]: 8 16 20 24 32[/FONT][/COLOR]
```[COLOR=#333333][FONT=Ubuntu]

I have been search the solution since month. 
Mayby someone have any idea how to change it?[/FONT][/COLOR]

---

### Post by CatKiller on 2020-10-27
The src resample methods haven't been in there for about five years, and you wrote it incorrectly in any case: it was src-sinc-best-quality, not the src–sinc–best–quality that you wrote.

---

### Post by Yellow Pasque on 2020-10-28
You have an alternate sample rate of 44100. So if you are playing sound that's 44100, or the last sound you played was 44100, that's what sample spec will be. Try playing something that you know is 48000 and check sample spec again.

---

