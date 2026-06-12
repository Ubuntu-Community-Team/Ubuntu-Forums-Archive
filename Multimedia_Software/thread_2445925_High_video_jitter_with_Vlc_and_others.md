---
title: "High video jitter with Vlc and others"
date: 2020-06-22
forum: Multimedia Software
---

### Post by gdesilva on 2020-06-22
Hi, I upgraded my laptop running Lubuntu 18.04 to 20.04 yesterday and noticed that the video jitter was significant when playing videos with Vlc, Celluloid and also mpv.

The following tweak appears to have fixed the problem in Vlc

1. In Vlc go to Tools -> Preferences

2. Select Video

3. The default value for Output is 'Automatic'

4. Changed it to 'OpenGL for Embedded Systems 2 video output'


The above fixed the problem in Vlc.

If any one has suggestions to fix the problem in Celluloid or mpv please let me know.


Hope the above will be useful for those who have encountered the same problem in Vlc.

---

### Post by VMC on 2020-06-22
Depends on hardware. Specifically Graphics-nvidia, amd, intel, etc.
I have "Intel Corporation UHD Graphics 630", and never experience video problems, no matter what method I use.

---

### Post by Yellow Pasque on 2020-06-23
So if you try to force OpenGL ES on mpv, is it better?
```
mpv --log-file=~/mpvlog.txt --vo=gpu --opengl-es=yes  filename
```
If not, please share ~/mpvlog.txt

---

### Post by gdesilva on 2020-06-30
> **VMC said:**
> I have "Intel Corporation UHD Graphics 630", and never experience video problems, no matter what method I use.


Interesting....I have Intel Corporation UHD Graphics 605 (rev 03). Does not appear to be that much older than your graphics card.

Thanks for the info.

---

### Post by gdesilva on 2020-06-30
> **Yellow Pasque said:**
> So if you try to force OpenGL ES on mpv, is it better?
```
mpv --log-file=~/mpvlog.txt --vo=gpu --opengl-es=yes  filename
```
If not, please share ~/mpvlog.txt


Yep....that did the trick. I updated mpv.desktop to include the options you suggested. Celluloid is set to use mpv config files but there is a slight lag in the audio stream - however, this is not that important as I have vlc and mpv working perfectly well.

Thanks so much!

---

