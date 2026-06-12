---
title: "Unable to use WMA lossless, codecs are installed."
date: 2008-12-13
forum: Multimedia Software
---

### Post by kking on 2008-12-13
Hi,

I'm running Xubuntu 8.10 for AMD64 and having a problem with WMA lossless files.  I have no problem with normal WMA files (or any other format I've tried). w64codecs and many other multimedia codec packages are installed, I followed the big multimedia howto in this forum.

I'm using amarok as my music player, it tells me there is no available decoder.

VLC gives me:
"VLC does not support the audio or video format "wmal". Unfortunately there is no way for you to fix this."

I tried converting to flac using sound converter, and a blank error box appears after I select the folder containing the files

I tried soundkonverter as well, this appeared to work, but the conversions appeared to be instantly successful (I'd think the conversion would take some time to process), but the flac files are also unplayable in anything.

I'm about 99% sure I ripped these without DRM, but I'm not sure how to verify this right now.

I've searched around and found similar issues, but no clear fixes.  Does anyone have any ideas?

---

### Post by mc4man on 2008-12-13
In 32 bit Amarok will play wma lossless, you need either w32codecs or libxine1-ffmpeg (I forget which.

If it's w32codecs then you'd be out of luck unless you can setup to use them on 64 bit (w64codes were/are somewhat useless

---

### Post by bonfire89 on 2009-01-17
I just got 

"VLC does not support the audio or video format "wmal". Unfortunately there is no way for you to fix this."


And I'm 32bit ubuntu w32codecs doesn't seem to exist and the other is installed

---

### Post by mc4man on 2009-01-17
> VLC does not support the audio or video format "wmal". Unfortunately there is no way for you to fix this."

I think you can take that quite literally. (though vlc in windows can

Many other players will, amarok, mplayer, smplayer, totem-xine, ect.

To install w32codecs either add medibuntu as a repo and then go```
 sudo apt-get install w32codecs
```

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

or go here and directly download and install 

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

