---
title: "Cant play wav files in Ubuntu 8.10"
date: 2008-12-28
forum: Multimedia Software
---

### Post by Jessica's on 2008-12-28
Hi 
I'm having problems playing wav files I have installed the Gstreamer codecs and i can play mp3 files but not wav, any ideas?

Thanks you for your help in advance
Jess.

---

### Post by seventyeights on 2008-12-28
I was checking on exactly which gstreamer plugin you'd need, and I found this post:
[http://ubuntuforums.org/showthread.php?t=987654](http://ubuntuforums.org/showthread.php?t=987654)

It seems that gstreamer has difficulty reading the header of certain wav files. You'll likely have problems with Totem (Movie Player) and Brasero disc burner. (Do you remember exactly what program you used to create the wav's?)

I don't know if there is a specific plugin that will fix it. I suggest installing ubuntu-restricted-extras to install all the codecs you'll ever need. I already automatically do this on every machine that I set up. Open a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
(Be ready to click OK a couple times)

If you still can't play your wav's with Totem then you can also try mplayer or vlc, as they use ffmpeg instead of gstreamer.

---

### Post by Jessica's on 2008-12-28
I didn't make the wav files so i do not know what program made them. I will type in the code tonight when I get back from work.


Thanks for your help

---

### Post by cariboo on 2008-12-28
I would suggest installing the ubuntu-restricted-extras package as well as the w32codecs and libdvdcss2 from the medibuntu repositories. Go [here]("http://help.ubuntu.com/community/Medibuntu") to setup the Medibuntu repositories, and scroll down to setup the gpg keys.

The combination of the ubuntu-restricted-extras, w32cpdecs and libdvdcss2 packages will allow you to play almost any type of audio/video files.

Jim

---

### Post by mc4man on 2008-12-28
If you continue to have issues with those .wavs and some gstreamer apps then first make sure your fully updated. (some player issues seemed to have been resolved in regard to .wav files

If it's still a problem then install sox

```
sudo apt-get install sox
```

Then you simply run each .wav thru sox and it will 'fix'

Just cd to the folder they are in and run this (adjusting red to match

Ex. 
The .wav is in a folder on my desktop named waves

```
doug@doug-desktop:~/Desktop/waves$ sox [COLOR="Red"]foo[/COLOR].wav [COLOR="Red"]foo-1[/COLOR].wav
```

The new .wav should work fine (will probably be 70 bytes smaller

---

### Post by jamesisin on 2009-01-05
Know much about encoding?

[http://ubuntuforums.org/showthread.php?t=1031973](http://ubuntuforums.org/showthread.php?t=1031973)

---

