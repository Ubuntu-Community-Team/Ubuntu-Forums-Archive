---
title: "Sound Flickers in Flash"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by LuisGMarine on 2007-05-05
Hey guys,

I seem to be having an issue here with Flash and the sound it produces.  For some reason the sound produces by flash flickers, making it almost inaudible to hear anything.  This happens when I watch videos on YouTube and the music players that my friends have on MySpace.

I've looked around, and tried a different amount of fixes, one which included these steps:
```
sudo gedit /etc/firefox/firefoxrc
```
Then in the file adding the changing the line:
```
FIREFOX_DSP="none"
```
To resemble this:
```
FIREFOX_DSP="aoss"
```

Other than that, my sound across the system is perfectly fine, aside for software mixing for some reason not working.  Even my 5.1 surround sound works, but I don't see why flash would have a problem with the sounds.

So if you guys maybe know of a thread that I wasn't able to dig up that has some kind of fix for sound issues with flash and Firefox let me know, I can try the fix and you never know I might strike gold.  

If not, I'd appreciate any other suggestions, and before I forget, I have tried using Opera and the same effects happen to Opera that happen to Firefox.  

Thanks :guitar:

---

