---
title: "Subtitle Control"
date: 2009-03-05
forum: Multimedia Software
---

### Post by DevoiD666 on 2009-03-05
Hi Guys, long time listener, First time caller

I'm looking for a media player with better subtitle control than totem or vlc for linux can give me, in ubuntu, this is the ONLY thing holding me back from making linux my 24/7 media center, by total control I will give the following example

1. In windows I use ffdshow and some other plugins so that the subtitles for a movie can be shown in the letter box as well as being clear enough to read on a standard CRT television running off S-VIDEO.

2. in linux I have tried totem with gstreamer and xine backend, xine was the best as it put the subs in the letterbox to begin with, but none of the options for changing the text size work for me (even the editing config files hack thing) so the text whilst in the right place, is WAY to small to make out on my crappy TV, VLC has nice subs, readable, but they are not in the letterbox, they are on top of the video, and this is anoying for me.

I need subtitles cause my wife is deaf, so she needs subtitles to watch movies.

Any help would be appreciated, I am running ubuntu 8.10 with all updates current as of this post, perhaps if there are hints to maybe fixing totem with the xine backend I would be open to that, the hacks I found involved editing a file (which I could not find), since it wasn't there I made one, but it still failed to adjust the settings

Thanks for any help you can give!

P.S. I don't care if the media player is garbage and everyone hates it and it givesme green babies, if you can make a solution to give me subs (hell even something windows running in wine) I will love you forever

---

### Post by lovinglinux on 2009-03-05
The best subtitle experience I had so far was achieved using the latest mplayer version as backend and the latest version of smplayer as frontend.

I don't know which versions are available in 8.10 but you can get the most recent versions from [http://ubuntuforums.org/showthread.php?t=982135](http://ubuntuforums.org/showthread.php?t=982135)

I never tried to put the subtitles in the letterbox, but I guess it is possible.

> 
* The subtitles when using the SSA/*** library can now be further customized. It's possible to select the font, size, colors, bold, italic, outline, shadow...

Here is an example of my mplayer config file. I actually use gnome-mplayer, but my mother likes the subtitles in the top of the screen, so she uses smplayer. I'm not sure if the settings below will work with smplayer, but just in case...
```

[default]

alang=English,eng,en
slang=Portuguese,por,pt
ao=pulse
vo=xv
zoom=1
vf=eq2
double="yes"
font=/usr/share/fonts/truetype/msttcorefonts/arial.ttf
***="yes"
embeddedfonts="yes"
***-color="FFFF0000"
subfont-text-scale="7"
subfont-outline="3"
subpos="0"
subalign="1"

[gnome-mplayer]
alang=English,eng,en
slang=Portuguese,por,pt
ao=pulse
vo=xv
af=volume=5:0
double="yes"
font=/usr/share/fonts/truetype/msttcorefonts/arial.ttf
***="yes"
embeddedfonts="yes"
***-color="FFFF0000"
subfont-autoscale=1
subfont-text-scale="7"
subfont-encoding="ISO-8859-1"
subfont-outline="3"
subpos="0"
subalign="1"
```

To edit the config file:

```
gedit ~/.mplayer
```

Please notice that I use the msttcorefonts truetype fonts that you have to install separately. They make a big difference in my opinion.

---

### Post by konqueror7 on 2009-03-05
you can try [SMPlayer]("http://smplayer.sourceforge.net/"), its basically a frontend to MPlayer, but more options...provides automatic searching and downloading of subtitles...

---

### Post by rvm4000 on 2009-03-05
> **lovinglinux said:**
> The best subtitle experience I had so far was achieved using the latest mplayer version as backend and the latest version of smplayer as frontend.

I don't know which versions are available in 8.10 but you can get the most recent versions from [http://ubuntuforums.org/showthread.php?t=982135](http://ubuntuforums.org/showthread.php?t=982135)

I never tried to put the subtitles in the letterbox, but I guess it is possible.

Yes, it is. Video -> Filters -> Add black borders. (The subtitles will appear in the black borders)

In newer versions there's an option in preferences to add the black borders automatically when switching to fullscreen.

[http://smplayer.berlios.de/downloads.php](http://smplayer.berlios.de/downloads.php)

---

