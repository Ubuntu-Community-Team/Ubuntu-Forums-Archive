---
title: "Playing .mov videos (Apple Quicktime movies)"
date: 2009-06-03
forum: Multimedia Software
---

### Post by sajithkozhikode on 2009-06-03
Hai everybody...:p

How can we play QuickTime Movies (.mov)?  In which Player...?

Which codec required...?   How can we install it...?

Can anyone help...

---

### Post by SuperSonic4 on 2009-06-03
My Favourite is smplayer but standard mplayer will work too. The codecs are in the ubuntu-restricted-extras package

---

### Post by andrew.46 on 2009-06-04
Hi sajithkozhikode,

> **sajithkozhikode said:**
> How can we play QuickTime Movies (.mov)?  In which Player...?

Well, bear in mind that mov is simply a container that can hold a variety of audio and video codecs. Have a look at [QuickTime]("http://en.wikipedia.org/wiki/QuickTime") to see a list of the many, many supported formats.

Having said that I would suggest that MPlayer + SMplayer would be an excellent combination. If you use the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") version of MPlayer you could also pick up the w32codec pack and I would be surprised if you could not play all mov files you could possibly find :-).

All the best,

Andrew

---

### Post by tuggy on 2009-06-22
Hi there,

I copied some movies from a friend's iMovie library, but when I tried playing them in my linux box I only get sound, no image :(
Its in mov, but how can I get info of which codec is being used for video? 

Anybody else ever bumped into this problem? How to solve it?

thanks
ps - i have restricted-extras and w32 codecs, vlc and mplayer.. nothings works

---

### Post by andrew.46 on 2009-06-22
Hi tuggy,

> **tuggy said:**
> I copied some movies from a friend's iMovie library, but when I tried playing them in my linux box I only get sound, no image :(
Its in mov, but how can I get info of which codec is being used for video? 


One way is to get a copy of FFmpeg from the repository, [make sure it can read all possible codecs]("http://ubuntuforums.org/showthread.php?t=1117283"), and test the file from the commandline:
```

ffmpeg -i *myfile.mov*
```

and this will tell you exactly what audio and video codecs are being used.

Andrew

---

