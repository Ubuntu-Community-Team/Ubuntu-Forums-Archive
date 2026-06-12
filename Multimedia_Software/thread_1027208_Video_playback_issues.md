---
title: "Video playback issues"
date: 2009-01-01
forum: Multimedia Software
---

### Post by frost151n on 2009-01-01
Hello,

I changed my display recently and since then my video playback in full screen is kinda jerky and not-smooth. This is not an issue in a restored window size and noticeable in maximized window size. 
But in full screen it intolerable.

Specs:
Benq E2200HD 22"
AMD 64 3500+ 2.41GHz
2GB DDR 
ATI HD 3850 512MB Sapphire Make
Asus M2 ...something MoBo.

Thnx for any help.

---

### Post by frost151n on 2009-01-07
Anybody???

---

### Post by markbuntu on 2009-01-07
System/Preferences/Multimedia Systems Selector/Video/Default Output Plugin select

X Window System (No Xv)

Worked for me with my HD3650.

I assume you are using the restricted driver fglrx.

---

### Post by frost151n on 2009-01-08
I already tried that!!!
And yes i am using the proprietary drivers.

---

### Post by markbuntu on 2009-01-08
What applications are you using?

---

### Post by frost151n on 2009-01-09
Totem Movie Player.
Do you think there's a problem with the player software???

---

### Post by markbuntu on 2009-01-09
Try vlc or mplayer and see if you have the same problem.

---

### Post by frost151n on 2009-01-10
VLC does play better, but it kinda choppy so i have to disable effects.
Is there a workaround for this???

---

### Post by brunolabs on 2009-01-10
Also have that problem. ([http://ubuntuforums.org/showthread.php?t=774847](http://ubuntuforums.org/showthread.php?t=774847))

Try the suggestions on that thread. Didn't work for me but they did for other people. Might work in your case.

---

### Post by frost151n on 2009-01-10
Yea, its still not as good as it is in a restored window.

---

### Post by frost151n on 2009-01-11
I've been doing some fiddling and i found that

In Totem
With X Window System (X11/XShm/Xv) the video is smooth but choppy in fulscreen.
With X Window System (No Xv) the video is not choppy but jerky, like its not being refreshed fast enough. (fullscreen)

In VLC
It makes no difference, its not choppy but jerky, like its not being refreshed fast enough, which ever option.

Under either option video plays perftly in a small (restore) window size, in both players.

Driver issue???

---

### Post by frost151n on 2009-01-13
I've tried MPlayer, VLC, Totem, Real Player.
Countless configurations of 'X Window System (No Xv)' & 'X Window System (X11/XShm/Xv)'

The closest i got to perfect was X11 with VLC, in fullscreen it was less jerky than the others but still irritating.

Am I doomed???? 

PS RealPlayer for Linux can't play .avi WTH. Know where i can find some codecs for it??

---

