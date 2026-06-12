---
title: "No audio with bluetooth headset (Intrepid)"
date: 2009-02-15
forum: Multimedia Software
---

### Post by Die Kuh macht muh on 2009-02-15
Hi,

I had no problem connecting to a Jabra bluetooth headset. It shows up in Bluetooth Preferences.

However, it won't work as a audio device. The btsco program runs successfully:

```
user@pc:~$ sudo btsco -v 00:1A:45:B3:75:B7
[sudo] password for user: 
btsco v0.42
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 2 connected
Using interface hci0
```

It is apparently recognized by ALSA (after I added it to ~/.asoundrc):

```
user@pc:~$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 16
 1 [Headset        ]: Bluetooth SCO - BT Headset
                      BT Headset 1
```

The only problem is, I can't use it with arecord or aplay:

```
user@pc:~$ arecord -D bluetooth -f S16_LE /tmp/test.wav
ALSA lib pcm_bluetooth.c:1531:(audioservice_recv) Error receiving data from audio service: Success(0)
ALSA lib pcm_bluetooth.c:1547:(audioservice_expect) Bogus message BT_GETCAPABILITIES_REQ received while BT_GETCAPABILITIES_RSP was expected
arecord: main:583: audio open error: Invalid argument
```

Anybody know what this error message means?

---

### Post by Die Kuh macht muh on 2009-02-20
Just tried the latest Jaunty alpha, but still no luck. It connects to the headset, but I can't use it for audio (tried ALSA and pulseaudio).

I hear Linux is getting better A2DP support soon, thanks to some Google project, so maybe I'll just have to wait for that.

---

### Post by Die Kuh macht muh on 2009-02-28
Turn out my headset doesn't work under XP, either. It gives me the same problem I have under Ubuntu: the headset pairs, but isn't recognized as a audio device.

It's a Jabra BT4051 btw.

Does anyone know of a cheap bluetoth headset that works under Ubuntu?
Thanks :)

---

