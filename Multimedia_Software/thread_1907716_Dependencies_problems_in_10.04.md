---
title: "Dependencies problems in 10.04"
date: 2012-01-11
forum: Multimedia Software
---

### Post by Silverflyer on 2012-01-11
Yes, I am on 10.04 and in an attempt to follow the directions in the how to thread, I got to the part to install this code

```
sudo apt-get install ubuntu-restricted-extras non-free-codecs p7zip-rar acroread gimp inkscape blender smplayer vlc libdvdcss2 libdvdread4 faac faad audacious rubyripper cd-discid aacplusenc gtkpod lame cdrdao aacgain flac mp3gain normalize-audio vorbisgain arista soundconverter gnome-sushi exfalso winff devede openshot audacity cheese synaptic gconf-editor lsb-core
```

and I get this in Terminal.

---

### Post by mikewhatever on 2012-01-12
The output shows that you have a getdeb repository for Oneiric enabled, and obviously, a repository for Oneiric (11.10) won't work on 10.04. Remove it, then try again.

---

### Post by Silverflyer on 2012-01-12
you are right, I can't believe I did that.  Wow.  Maybe it is time I go to bed and get some sleep.

Thanks.

---

### Post by mikewhatever on 2012-01-12
Probably a good idea, sweet dreams. :~)

---

