---
title: "How to play RM Videos."
date: 2009-02-22
forum: Multimedia Software
---

### Post by Abdel-Rahman on 2009-02-22
Hello.

Which video player can play real-player videos? VLC cannot!

---

### Post by UbuntuNerd on 2009-02-22
vlc should be able to play anything if you have the right plugins also you can use the real player in Ubuntu check this links:
[HERE](http://my.opera.com/ubuntunerd1/blog/realplayer-in-linux)
[HERE](http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem)

---

### Post by Abdel-Rahman on 2009-02-22
i do not understand how to install the real player.

---

### Post by Franic on 2009-02-22
MPlayer can play RealMedia files if you install the w32codecs (or w64codecs if your OS is 64 bits) package.

---

### Post by Abdel-Rahman on 2009-02-22
can you give me a link for the codec?

---

### Post by Franic on 2009-02-22
They are in the Medibuntu repository :) Add it in your /etc/apt/sources.list and then you can install it with synaptic.

For me the repository is:
## medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

---

### Post by Abdel-Rahman on 2009-02-22
thanks i can watch with Mplayer now, but my vlc still only plays the sound, strange... and i cannot make a proper fullscreen with mplayer.

Is there anyway to activate realfiles in vlc player?

---

### Post by Franic on 2009-02-22
Sorry but I don't think you can play RealVideo files on VLC because FFMpeg don't play them (as far as I know), and yes that's why RM files are annoying. 

At least they play on MPlayer, and you should be able to watch them fullscreen that's weird... have you tried typing the F button?

---

### Post by Abdel-Rahman on 2009-02-22
It goes to fullscreen but the movie only fits a part of it.

---

### Post by Franic on 2009-02-22
Maybe you should try another MPlayer frontend I don't know... or use the CLI and see if it's still the same (the F key toggles fullscreen/windowed mode).

---

