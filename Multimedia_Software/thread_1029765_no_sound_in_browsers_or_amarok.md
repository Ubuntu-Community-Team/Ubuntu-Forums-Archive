---
title: "no sound in browsers or amarok"
date: 2009-01-03
forum: Multimedia Software
---

### Post by HamHamT on 2009-01-03
i use a creative soundblaster audigy and for the most part totem (i think its called) video player and the default sound player rhythm box plays sound, however if i try to watch a youtube video in my browser instead of totem i dont get any sound

any clues?

---

### Post by Setehk on 2009-01-04
I have the same problem. I'm using OSS with my Creative Soundblaster xfi Extreme Music on Ubuntu 8.10 and can not get any sounds from Firefox and games alike. Help would be appreciated.

---

### Post by namdung on 2009-01-04
In terminal
```
less /proc/asound/card0/pcm0p/info
```

Check *subdevices_avail*, it if's zero it means that ur sound card is captured by some other device. Stop any other devices and try again.

Also pls install Adobe Flash Player 10 available from:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) 

Try this for multiple sound solution:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by HamHamT on 2009-01-04
so my *subdevices_avail* says 1, but i tried youtube and nothing
i have a clean install of ubuntu (installed about 2-3 days agO) and i reinstalled flash 10 just for the hell of it and nothing

im looking thru the multi sound solution right now, though i dont think it applies since i have subdevices avail 1

---

