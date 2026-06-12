---
title: "MP3s stop playing suddenly"
date: 2008-05-20
forum: Multimedia Software
---

### Post by hudsonhauck on 2008-05-20
I have been having this problem as of lately [Ubuntu 8.04], and it is rather annoying. My audio stops working suddenly for no apparent reason. The best way to fix it right now is by killing X and re-logging in. Obviously this is a pain.

Whenever this situation happens, it appears that mp3s are the only things that don't work. WAV's are still playable in gnome-sound-recorder. Also the `gstreamer-properties` test sound tool still works too. However, whenever I try to listen to an mp3 (whether it is through rhythmbox, banshee, or even mpg123), it doesn't work. Rhythmbox and banshee pretend they are about to play the file, but the progress doesn't move. The following is the output of mpg123.

```
MPEG 1.0 layer III, 128 kbits/s, 44100 Hz stereo
[../../../src/audio.c:267] error: Unable to set up output device! Constraints: 44100, 22050 or 11025Hz.

Audio device: <none>
Audio capabilities:
(matrix of [S]tereo or [M]ono support for sample format and rate in Hz)
        |  s16  |  u16  |  u8   |  s8   | ulaw  | alaw  |
 --------------------------------------------------------
  8000  |       |       |       |       |       |       |
 11025  |       |       |       |       |       |       |
 12000  |       |       |       |       |       |       |
 16000  |       |       |       |       |       |       |
 22050  |       |       |       |       |       |       |
 24000  |       |       |       |       |       |       |
 32000  |       |       |       |       |       |       |
 44100  |       |       |       |       |       |       |
 48000  |       |       |       |       |       |       |
```

I am not even sure where to start with this. Any help will be much appreciated!

---

### Post by hudsonhauck on 2008-05-22
Any help?

It does this with OGG files as well. Is this a gstreamer problem?

---

### Post by hudsonhauck on 2008-06-25
Four weeks have gone past,
I still wait steadfast.

Do you have any help for me?
Or shall I continue to wait patiently?

---

### Post by Mr.Useless on 2008-06-25
All i can do is bump this, but..

BUUmP

BOOOOOOOOHHUUUMMMP

:D

---

### Post by hudsonhauck on 2008-07-03
Okay, well I think it might be solved now.

It happened again today and so I tried to use mgp123 again, and this time I saw a reference to audio_oss.c or something related to OSS. So, I realized that might be the culprit. The sound settings were set to "Autodetect", instead of ALSA. I set it to ALSA and Rhythmbox is working again (along with mpg123-alsa).

Anyway. It is solved for now. Hopefully this is the problem.

---

### Post by trent_easton on 2008-07-22
Hi, Im new to Ubuntu and signed up when I logged on and have gotten a lot of help from the forums by just lurking and reading up on info which I am extremely grateful for! 

I have been having the same problem as you hudsonhauck, Id be listening to music etc and then for some reason mp3s would stop playing in Totem, VLC, Rhythmbox etc. Could you give me some more detail on the setting you changed in MPG123?


Edit: Apparently Firefox doesn't agree with my choice in music, when I close it I can play mp3s etc again. Any idea why this is? Would love to be able to fix it thats all.

---

### Post by hudsonhauck on 2008-07-23
Sorry, I should have made myself clearer. The sound settings I changed were not mpg123 sound settings, but rather the Ubuntu sound settings app (found in the "Settings" menu on the top panel [in my setup])

---

