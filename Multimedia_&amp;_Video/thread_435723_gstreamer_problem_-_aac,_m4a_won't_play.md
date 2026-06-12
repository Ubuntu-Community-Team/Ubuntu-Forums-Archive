---
title: "gstreamer problem - aac, m4a won't play"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by indridi on 2007-05-07
hello

I'm running feisty on a thinkpad r40 laptop, and have the following problem: 

totem-gstreamer and rhythmbox won't play my m4a and aac files. Rhythmbox gives a simple error message.
```
** Message: don't know how to handle audio/mpeg, mpegversion=(int)4, framed=(boolean)true, codec_data=(buffer)1210, rate=(int)44100, channels=(int)2
```
and totem gives me the easy codec selection dialogue, which advised me to install one of the packages
```
gstreamer0.10-plugins-ugly
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad-multiverse
```
but those are already installed, as well as a bunch of other codecs, and w32codecs (and some other stuff) from medibuntu.

The files used to play smooth on edgy, and (I think, not quite sure though) at first on feisty (beta). 

SoundConverter doesn't work for those files either, but used to on edgy.

I'm guessing this is some problem with gstreamer, it not being able to access some of the codecs, or something in that direction, since the files are not corrupted (mplayer plays them just fine) and all the needed codecs are (supposedly) installed.

Any help or suggestions appreciated

Regards
Indriði

---

### Post by Paul S on 2007-05-07
I just posted another thread that I'm having this problem whenever I have my firewall enabled, but it works when the firewall is disabled.  Are you using a firewall?  If so, try disabling it and see if it works.

---

### Post by indridi on 2007-05-08
Well, I don't have a firewall on my computer, only on my router. I tried turning it off, to no avail.

It might have something to do with it that I haven't done a clean install for a while (since dapper or breezy), but always updated through apt-get (mostly to a beta version).

regards
Indriði

---

### Post by indridi on 2007-05-08
whoops

well, I just resolved this problem. A while ago, I was trying to get as much media support as possible, stumbling upon a guide to use the ubuntusoftware.info repo. Later, I set up medibuntu, which seems to be the unofficial way. Somewhere along the way, the software from those two repos stopped vibing with each other. Now I have uninstalled everything I installed from ubuntusoftware.info and instead installed packages from medibuntu, and everything works smooth.

regards
Indriði

---

