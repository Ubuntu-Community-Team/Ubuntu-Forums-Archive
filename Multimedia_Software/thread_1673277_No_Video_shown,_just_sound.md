---
title: "No Video shown, just sound"
date: 2011-01-22
forum: Multimedia Software
---

### Post by graham73may on 2011-01-22
This is my first week using Ubuntu (10.10).

I have installed VLC and SMplayer.

I cannot get any videos to play, but the audio works fine. 

I assumed that installing VLC / SMplayer would install the needed codecs. (Is my problem missing codecs?)

I have an Acer Aspire One and have had to install poulsbo drivers GMA500 to get the screen to work properly. 

Whenever I try to play videos, they audio works but the video area just stays black.

Any help would be great! Thanks

---

### Post by meson2439 on 2011-01-22
Probably
1)Codec problem - install the restricted or even the ugly codec packages. Try them one by one until it works.
2)Install MPlayer and totem. MPlayer for mkv and Totem for avi's

After each install, do a restart. The video problem is unrelated to the screen as far I understand it. Also, please give up trying to play those 720p videos or anything HD. It lags (even in windows). I'm using the same netbook as yours at the moment.

---

### Post by graham73may on 2011-01-24
Hi Thanks,
I'm just trying them now... where would I get such codec packs for linux?

/me goes and installs mplayer and totem.

EDIT:

I have installed mplayer, and it actually has video! It is very choppy though, do you / or anyone know of a way to improve video performance? It is only a netbook so i'm not expecting much, but these play fine in windows...

EDIT EDIT:

in Mplayer I went to preferences - Video output and changed it to X11 and it is working GREAT... I'm going to try the other ones too, but if anyone else is having troule "vaapi" didn't work very well for me, choppy video and pixelated images. 

Thanks!

---

### Post by yvesdm3000 on 2011-02-13
> **graham73may said:**
> Hi Thanks,
I'm just trying them now... where would I get such codec packs for linux?

/me goes and installs mplayer and totem.

EDIT:

I have installed mplayer, and it actually has video! It is very choppy though, do you / or anyone know of a way to improve video performance? It is only a netbook so i'm not expecting much, but these play fine in windows...

EDIT EDIT:

in Mplayer I went to preferences - Video output and changed it to X11 and it is working GREAT... I'm going to try the other ones too, but if anyone else is having troule "vaapi" didn't work very well for me, choppy video and pixelated images. 

Thanks!

Xv is broken on gma500 for now and vaapi only works on hd-resolutions.

-Yves

---

### Post by paddy2 on 2011-02-18
In my case the black screen on playback was solved by setting deinterlacing to automatic in prefs.It was driving me mad,but this solved it.:)

---

### Post by findelmundo on 2011-02-22
Thanx alot ):P):P):P
I solved my problem easily now, on VLC, by just turning the video output to X11...
Now I only need to solve my flash-player problem, so Iwill be able to see full screen Youtube (and other) online videos... ):P

---

### Post by findelmundo on 2011-02-22
Btw... I could not solve it on Totem, since I could not find an advanced settings option...

---

