---
title: "winff mobile phone presets gone"
date: 2010-04-26
forum: Multimedia Software
---

### Post by Awareness on 2010-04-26
The only preset for mobile phone is mp3. All video presets are gone...
Anybody knows how to install them?

Im using lucid atm

---

### Post by Awareness on 2010-04-26
bump
:guitar:

---

### Post by paul.gevers on 2010-05-03
> **Awareness said:**
> The only preset for mobile phone is mp3. All video presets are gone...
Anybody knows how to install them?


What do you mean by "are gone"? Since you reinstalled? I removed the presets that use libfaac because that is not included in Ubuntu Lucid anymore, but the complete presets are still available in /usr/share/winff/ (presets-libavcodec52-v5.xml) If you didn't change your own presets, you can move that to ~/.winff/presets.xml You need to get a ffmpeg that supports libfaac thou (from medibuntu for instance).

Hope this helps.

---

### Post by Awareness on 2010-05-03
well, i installed the program for the first time... "are gone" means the last time i used winff i rememberd more presets...
Anyway, i mv libavcodec52-v5.xml and it all worked fine (i wonder why this is not done by default)

Well the presets just appeared, but not all of them worked fine .3gp QVGA videos didnt work... i dont remember the error... ill post them later, i have all the stuff in my other computer :)

thank for the response

---

### Post by paul.gevers on 2010-05-04
> **Awareness said:**
> 
Anyway, i mv libavcodec52-v5.xml and it all worked fine (i wonder why this is not done by default)

Please read /usr/share/winff/README.Debian. As I mention there and before in this thread, I removed the presets which include ffmpeg functionality which is NOT available in the ffmpeg in Ubuntu. 

> Well the presets just appeared, but not all of them worked fine .3gp QVGA videos didnt work... i dont remember the error... 

Probably the same issue. I think you need the ffmpeg from medibuntu to do this, or follow the advise in [FakeOutdoorsmans howto]("http://ubuntuforums.org/showthread.php?t=1117283") to build your own full featured ffmpeg.

---

