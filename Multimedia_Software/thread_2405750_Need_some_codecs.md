---
title: "Need some codecs"
date: 2018-11-10
forum: Multimedia Software
---

### Post by jacatone on 2018-11-10
Been trying to play some .mkv files but keeps saying the following:

"Requried plugin could not be found

pk-gstreamer-install requires to install plugins to play files of the following type:

H-264 (High Profile) decoder
MPEG-4 AAC decoder

---

### Post by mc4man on 2018-11-10
This should suffice,
```
sudo apt install gstreamer1.0-libav
```

The 2 other multimedia plugins are
gstreamer1.0-plugins-bad
gstreamer1.0-plugins-ugly

---

### Post by joe136 on 2018-11-21
I tried all of the above and more..still no mpeg4... lots of old forums on the subject ..no help...why did I upgrade? lenovo t510 
fingerprint reader was also a pain but I did get it installed .,,(with lots of code that didn't work... still installed) looks like this mpeg4 issue has me installing extra code that doesn't solve problem.. still looking for a solution....loaded vlc openshot kdenlive..restricted extras.... updated... upgraded 
what's the trick?????  this is not my first cup of java... long time ubuntu  user....

---

### Post by Autodave on 2018-11-21
> ..why did I upgrade? ...


You may have answered your own question.  I rarely find that updating leads to anything good.  I learned a long time ago to only use the LTS releases and then to do clean installs after making sure everything was backed up to an external source.

---

### Post by SeijiSensei on 2018-11-21
Install smplayer and mpv. mpv plays practically anything.

```
sudo apt install mpv smplayer
```

I don't understand why mpv isn't the default player in Ubuntu myself.

---

### Post by ajgreeny on 2018-11-21
> **SeijiSensei said:**
> Install smplayer and mpv. mpv plays practically anything.


As does vlc in my experience; it's always one of my first additions to any of the OSs I install.

---

### Post by mc4man on 2018-11-22
> **joe136 said:**
> I tried all of the above and more..still no mpeg4... lots of old forums on the subject ..no help...why did I upgrade? lenovo t510 
fingerprint reader was also a pain but I did get it installed .,,(with lots of code that didn't work... still installed) looks like this mpeg4 issue has me installing extra code that doesn't solve problem.. still looking for a solution....loaded vlc openshot kdenlive..restricted extras.... updated... upgraded 
what's the trick?????  this is not my first cup of java... long time ubuntu  user....
Unless there is something 'off' about your ".mkv's" those plugins mentioned should do the job with gstreamer players. You could try removing the .bin file in the
.cache/gstreamer-1.0 folder.

---

