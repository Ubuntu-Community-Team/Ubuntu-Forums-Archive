---
title: "Can't convert mp3 to audio cd"
date: 2008-04-19
forum: Multimedia Production
---

### Post by fizban9 on 2008-04-19
Hey all, I'm trying to do something that should be incredibly easy.  I'm trying to burn an audio CD using some mp3's I have.  I've installed the ubuntu-restricted-extras and I've even installed lame.  Everything I've tried to burn with gives me some variation on the same error, can't covert, make sure you have the right codec.  I've tried Serpentine, Gnomebaker and Brasero.

I can play mp3's so I don't know what other codec I could need.  I suspect it's a gstreamer one but which one?  

Thanks for the help.

---

### Post by syczu on 2008-04-20
Convert your mp3's to ogg's by f.e. 'Sound Converter'. Then try to burn your CD.

---

### Post by buixuanduong1983 on 2008-04-20
Before I also had that problem, but only with K3B. GnomeBaker burns audio CD very good without any trouble. I'm not sure what you have to install, I list here all the gstreamer I have:

0.10-alsa
0.10-esd
0.10-ffmpeg
0.10-gnomevfs
0.10-plugins-base
0.10-plugins-base-apps
0.10-plugins-good
0.10-plugins-ugly
gstreamer0.10-tools
gstreamer0.10-x

Hope this help.

---

### Post by H0bb3z on 2008-04-20
You can also use Serpentine -- that seems to work okay and it comes installed by default.

If you are set at using K3B, you might have to use a converter to get your MP3s over to WAV format, then start an audio CD project in K3B.

I've used mpg123 (sudo apt-get install mpg123) to do the conversion:[INDENT] mpg123 -w output.wav input.mp3[/INDENT]

---

