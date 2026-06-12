---
title: "How to reproduce MKV videos?"
date: 2015-04-25
forum: Multimedia Software
---

### Post by giaco2 on 2015-04-25
Hello, I got Lubuntu as my distro and recently downloaded some movies and they got this extension ".mkv", I used to reproduce them with DirectX as I used windows but now the multimedia player on Lubuntu just reproduce the audio.

-----------------help.

Thanks:)

---

### Post by VMC on 2015-04-25
By 'reproduce' I assume you mean play the 'mkv' file. I use the 'mpv' program to play all my music, videos. It plays anything I through at it. I purge all the default multimedia stuff that comes with xubuntu.

---

### Post by Keith_Helms on 2015-04-25
vlc or mplayer can usually handle anything you throw at them, given you have the needed codec library installed.

---

### Post by Rob Sayer on 2015-04-26
Ubuntu doesn't ship with all codecs installed ... try installing them like this:

```
sudo apt-get update
sudo apt-get install lubuntu-restricted-extras
```

Just copy and paste each line into terminal.

BTW vlc and mplayer can indeed play just about anything.  I use SMplayer as my default, which is an mplayer front end.  I think mpv is too.  Haven't tried it.

But with vlc and mplayer/mplayer GUIs you don't have to install codecs.  They use their own codec libraries and those come with the install.

---

