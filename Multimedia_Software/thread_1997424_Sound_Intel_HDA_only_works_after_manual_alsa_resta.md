---
title: "Sound Intel HDA only works after manual alsa restart"
date: 2012-06-05
forum: Multimedia Software
---

### Post by oujgazoiro on 2012-06-05
Hello,

I'm having a strange problem with my onboard soundcard in Ubuntu 12.04. The sound starts totally normal and works in the login screen. But after I enter my password and log in, it stops working. The sound applet looks muted and there is no sound device listed under Sound settings.

I also can't start some applications that use the sound, such as Open Arena or Skype.

When I manually restart alsa with

```
sudo alsa force-reload
```

everything is fine. But of course it is anoying to restart alsa from terminal after every login...

For your information about my soundcard:
```

$ lspci | grep Audio
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series]
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ID 887

```

[I've looked here]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and it seems that my card just isn't supported, but then again it works after a manual restart.

Does anybody have some ideas how to get the sound working automatically?

Thanks very much!

---

### Post by oujgazoiro on 2012-07-02
Ok, nobody has answered so far, but the problem is still existent. But I found another clue. When I boot my computer, of course I get the login screen. 
It seems that my soundcard doesn't get disabled when I wait some minutes at the login screen, I didn't figure out how long I have to wait, but three minutes are always enough. 
So I don't have to do the manual alsa force-reload, but I always have to wait some minutes at the login screen which is annoying as well.

Also I found out that I when I login directly and my soundcard gets disabled, I have to wait until the sound settings appear in the sound applet before I manually restart alsa. Restarting to early doesn't fix it.

Maybe all of you could think again and give me some tips?

Thanks very much!

---

