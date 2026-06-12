---
title: "Video plays in Totem but not VLC"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by Kerry_W on 2008-03-28
I've got an AVI that will play in Totem but not in VLC.  i opened VLC in the terminal, opened the file and got the following errors:

```
[00000307] avi demuxer error: avi module discarded (invalid file)
[mp3 @ 0xb1854610]Could not find codec parameters (Audio: mp1, 48 kb/s)
[00000307] ffmpeg demuxer error: av_find_stream_info failed
[00000307] ps demuxer error: cannot peek
[00000295] main input error: no suitable demux module for 'filename.avi'
```

I'm not sure what that exactly means.  hoping someone can explain it to me and how to fix the issue so i can use my preferred player.

Thanks for any feedback.
Kerry

---

### Post by xc3RnbFO8P on 2008-03-28
To start with install this (if you haven't):
> wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

---

### Post by Kerry_W on 2008-03-28
Appreciate the tip.  i've double checked and it's already installed.

Kerry

---

### Post by xc3RnbFO8P on 2008-03-29
Here is problem:
[https://trac.videolan.org/vlc/ticket/1022]("https://trac.videolan.org/vlc/ticket/1022")
Solution is to update ffmpeg codec far as I know.
If you haven't done this:
> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list 
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
and you should get update soon.

---

### Post by Kerry_W on 2008-03-29
thanks again Ringi, but i already had that source entered. still no luck

Kerry

---

### Post by xc3RnbFO8P on 2008-03-29
Then it is not supported by Vlc?
You could play it in Mplayer in terminal:
mplayer /home/ and what ever the file is > return
see if there is some useful information.

---

