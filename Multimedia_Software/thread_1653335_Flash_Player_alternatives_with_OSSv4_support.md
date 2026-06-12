---
title: "Flash Player alternatives with OSSv4 support"
date: 2010-12-26
forum: Multimedia Software
---

### Post by KutViZ on 2010-12-26
I want to use OSS instead of ALSA. I've changed almost all programs to OSS as default sound device (except a few like Hydrogen, which were only compatible with ALSA) but then I read that Adobe Flash Player only support ALSA, not OSS. Now I want to ask you guys what do you recommend me? Get back to ALSA or is there any good and compatible flash player in ubuntu?

---

### Post by Yellow Pasque on 2010-12-27
Adobe Flash supports OSS if you compile libflashupport.so with OSS enabled. Fortunately, the OSS4 wiki offers pre-compiled versions. See that: [http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#Adobe_Flash](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#Adobe_Flash)

---

### Post by KutViZ on 2010-12-27
The guide did the trick. Thanks! But I still need to set up an applet for the gnome panel. I can't see any sound icon in the "Add to Panel" list.

---

### Post by Yellow Pasque on 2010-12-27
[https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by KutViZ on 2010-12-27
> **Temüjin said:**
> [https://launchpad.net/~dtl131/+archive/ppa]("https://launchpad.net/%7Edtl131/+archive/ppa")
And which are the ones that I should install? I've installed everything except dev and debug packages.

---

### Post by KutViZ on 2010-12-27
I had to add the mixer (ossxmix) manually, but it works now, though it's quite weird because the headphones and the builtin speakers sounding together, no matter what I change in the mixer or what I put in the headphones output. Also is there any way to use the hotkeys again? I tried to remap the keys in System->Prefences->Hotkeys but it did nothing.

To test the key I have set up Audacious hotkeys, they are working so it's 100% percent that OSS doesn't handle the key events.

---

### Post by KutViZ on 2010-12-28
The speaker problem is solved: in the jack options i had to change int-speaker to a different channel (for example pcm2).

Still not a clue how to set the hotkeys. There's a lot of config files in the /etc/oss4/conf but don't know which should I modify and actually how.

---

### Post by KutViZ on 2010-12-30
reinstalled pulseaudio and hotkeys are handled, but it doesn't changes anything in volume since i'm still using oss... at least some compatibility problems solved this way (i was playing a game which only works with alsa/pulse, and without pulse it didn't wanted to start, now it works but there is no sound)

---

