---
title: "Converting audio from context menu"
date: 2011-11-04
forum: Multimedia Software
---

### Post by rmcellig on 2011-11-04
Is it possible to right mouse click on an audio file and have a list of possible options to convert to? This would save me a ton of time converting audio files.

---

### Post by davdo2004 on 2011-11-04
This might be what you are looking for, 'nautilus-script-audio-convert'. When it is installed run the script manager and check the box for convertaudiofile. You will then have the right click option to convert in nautilus.

---

### Post by shantiq on 2011-11-05
oh yes and that is fun too   [takes half an hour tops to set up]

got some of this info from stinkeye and turned it so it would be good for audio conversions


```
sudo apt-get install --no-install-recommends gnome-panel
```  


then create a script and save  [ffmpeg must be installed but i think it is by default usually]


_so if you want all your files to turn to Alac_


use


```
#!/bin/bash

for f in *; do ffmpeg -i "$f" -acodec alac "${f%.*}.m4a"; done

```

maybe call Go_2_Alac

_if you want to turn all lossless music files in a folder to 320k mp3_


use

```
#!/bin/bash

for f in *; do ffmpeg -i "$f" -ab 320k "${f%.*}.mp3"; done
```


call Go_2_320k




**and Place bash-scripts in ~/.gnome2/nautilus-scripts/ and make executable.**


sudo chmod +x  Go_2_320k    etc...


========================================


Once you have done this go to an audio file folder open right-click on one of the files and pick

scripts and the one you want    [make as many as needed  MOST people probably only need two or three of their favourite formats]

BEWARE:    ALL music and video FILES in the folder will be converted
if you want to be more specific fine tune thus

```
for f in [COLOR="Red"]*.flac[/COLOR]; do ffmpeg -i "$f" -ab 320k "${f%.*.[COLOR="Red"]flac[/COLOR]}.mp3"; done
```


restricting it to flacs





It looks like this  [[IMG]http://img802.imageshack.us/img802/6733/vol3002.th.png[/IMG]](http://img802.imageshack.us/img802/6733/vol3002.png)

---

### Post by amjjawad on 2011-11-05
> **rmcellig said:**
> Is it possible to right mouse click on an audio file and have a list of possible options to convert to? This would save me a ton of time converting audio files.

What OS are you using? release?
You didn't mention that on your post :)

---

