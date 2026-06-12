---
title: "Ubuntu 7.04 - No Sound, Sound Card Recognized"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by Dankmizter on 2007-06-04
My sound card is detected, but I'm not getting anything from my speakers. Is there something I'm not doing to get my sound working? My computer is rather old (533MHz celeron processor.  256 mb ram. 30 gig hard drive.) ethernet connection with wireless router. The system will beep but I get no sound from the speakers. 



```


cat/prod/asound/version
brandon@brandons:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

lspci -nn | grep audio

brandon@brandons:~$ lspci -nn | grep audio
01:09.0 Multimedia audio controller [0401]: Rockwell International Unknown device [127a:4310]
brandon@brandons:~$ 



```

---

### Post by Twintop on 2007-06-05
What do you get when you run the following command? Are there any error messages when you're in System->Preferences->Sound?

```
aplay /usr/share/sounds/login.wav
```

---

### Post by karaju on 2007-06-05
Hello,
I have a similar problem.  I have Winxp dual booting with feisty.  Sound works fine in Winxp.  I give the following output if it can help me solve.

raju@raju-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
raju@raju-desktop:~$ lspci -nn | grep audio
00:09.0 Multimedia audio controller [0401]: Yamaha Corporation YMF-724 [1073:0004] (rev 05)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
raju@raju-desktop:~$ aplay /usr/share/sounds/login.wav
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
raju@raju-desktop:~$ 

The system configuration and installation of drivers was tried several times in several ways by following the guidance given "Comprehensive Sound Problem Solutions Guide" in ubuntu forums.  Even after following everything there, I could not make the sound work.  The above output says Playing WAVE....but I could not hear any sound

Your help would be of great value to me as I am new to linux.
Thanks in Advance.

---

### Post by fluoblack on 2007-06-05
Dankmizter:
I had similar problem with my Audigy 2, this How-to resolved all my problems (a module wasn't charged at startup and the default soundcard wasn't as default as I thought):
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

karaju:
If it didn't work, well I can't help more than that, it's really complete. Try first to understand where your problem comes from and then, try to resolve it. If you did everything, as you said, maybe you did too much and created a new problem.

---

### Post by Dankmizter on 2007-06-05
When I put in the aplay /usr/share/sounds/login.wav it says..
```

brandon@brandons:~$ aplay /usr/share/sounds/login.wav
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
brandon@brandons:~$ 

```

but i still don't hear anything.

any more idea's or suggestions?

thanks in advance.

---

