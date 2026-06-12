---
title: "Surround conversion in pulseaudio"
date: 2015-08-08
forum: Multimedia Software
---

### Post by oierlauzi-r on 2015-08-08
Hello! I'm planning to setiup a 4.0 surround sound system. But I've got a question, as movies usually come in 5.1 surround, does pulseaudio route the center channel to the front left and right speakers when using 4.0 speaker setup or smply ignores the center channel. If the last one is the answer, is there anyway to solve this?
Thank you and sorry for my bad English

---

### Post by SeijiSensei on 2015-08-08
It seems to depend on ALSA, the choice of audio codec, and the player software as much or even more than pulseaudio.  Here's a fairly long discussion of 4.0 mixing in **mpv**: [https://github.com/mpv-player/mpv/issues/77](https://github.com/mpv-player/mpv/issues/77).  Apparently what you want is
```
mpv somefile.mkv -af force=channels=quad -channels quad
```
You can make those options permanent by creating a file named mpv.conf in the default $HOME/.config/mpv directory that is created when you install mpv from the repositories:
```

# sample mpv.conf for quad surround
af=force=channels=quad
channels=quad

```

A good graphical front end for mpv (and for its older cousin mplayer) is **smplayer** which is also in the repositories.

I'm afraid I cannot test any of this since I have a 5.1 system.

---

