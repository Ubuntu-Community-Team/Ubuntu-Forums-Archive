---
title: "SMPlayer skins"
date: 2011-04-21
forum: Multimedia Software
---

### Post by Black Beret on 2011-04-21
Can anyone tell me please, how to install skins for SMPlayer on Ubuntu 11.04?
I've downloaded 'powerplayer-1.1.tar.bz2' but terminal won't extract it - doesn't recognize it as a tar - bz2 file. 

Hopefully, Rog.

---

### Post by andrew.46 on 2011-04-21
Hi Rog,

Are you after this package:

[http://packages.ubuntu.com/natty/smplayer-themes](http://packages.ubuntu.com/natty/smplayer-themes)

If so the following will set you up:

```
sudo apt-get install smplayer-themes
```

Andrew

---

### Post by Black Beret on 2011-04-23
Thanks Andrew,

Did as suggested but Terminal tells me smplayer-themes are already installed.
What I want is to use a remote control skin. I've downloaded "powerplayer-1.tar.bz2"  but when I try to extract it Terminal says it doesn't recognise it as a bzip2 file.
Running ubuntu 11.04

Rog.

---

### Post by andrew.46 on 2011-04-23
I have searched for SMPlayer skins and I cannot see one called powerplayer, can you give a link?

---

### Post by Black Beret on 2011-04-24
Downloaded from here

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Happy Easter

---

### Post by andrew.46 on 2011-04-24
This and the others in this section are actually skins for the old default gui for MPlayer known as GMPlayer, not for SMPlayer :(. The actual file downloads and extracts ok now:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]tar xjvf PowerPlayer-1.1.tar.bz2 [/COLOR]**
PowerPlayer/
PowerPlayer/seekf.png
PowerPlayer/pref.png
PowerPlayer/stop.png
PowerPlayer/skin
PowerPlayer/equalizer.png
PowerPlayer/url.png
PowerPlayer/VERSION
PowerPlayer/menu.png
PowerPlayer/play.png
PowerPlayer/loadplay.png
PowerPlayer/mute.png
PowerPlayer/vcd.png
PowerPlayer/pause.png
PowerPlayer/preference.png
PowerPlayer/minimize.png
PowerPlayer/slider.png
PowerPlayer/extra.png
PowerPlayer/main.png
PowerPlayer/menus.png
PowerPlayer/trans.png
PowerPlayer/symbols.png
PowerPlayer/sub.png
PowerPlayer/eject.png
PowerPlayer/subtitle.png
PowerPlayer/skiner.png
PowerPlayer/audiofile.png
PowerPlayer/symbols.fnt
PowerPlayer/fullscreen.png
PowerPlayer/close.png
PowerPlayer/font.png
PowerPlayer/volume.png
PowerPlayer/about.png
PowerPlayer/font.fnt
PowerPlayer/README
PowerPlayer/vol+.png
PowerPlayer/dvd.png
PowerPlayer/vol-.png
PowerPlayer/next.png
PowerPlayer/load.png
PowerPlayer/sym-media.png
PowerPlayer/seekb.png
PowerPlayer/sym-media.fnt

```

and I suspect you have attempted to download it at a time when MPlayer was swapping servers, a process that is almost complete now. But unfortunately this file has no use for SMPlayer at all...

Andrew

---

### Post by Black Beret on 2011-05-31
Many thanks Andrew.
Guess I'll have to settle for basics unless - Do you know if it's possible to run GMPlayer on Kubuntu 11.04?

Sorry so late with thanks,

Black Beret.

---

### Post by andrew.46 on 2011-06-01
> **Black Beret said:**
> Do you know if it's possible to run GMPlayer on Kubuntu 11.04?

I have not tried it but I believe that the package name is *mplayer-gui*.

---

