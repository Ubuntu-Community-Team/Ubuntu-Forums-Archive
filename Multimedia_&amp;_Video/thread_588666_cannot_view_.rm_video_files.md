---
title: "cannot view .rm video files"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by MaximB on 2007-10-23
I've installed all property codec packages but I still cannot view .rm (real player) files.
It was viewable at Feisty, how can I fix it on gutsy ?

I also cannot view them with realplayer from the real site (I wasn't able to view those files with this program ever, ob feisty I used MPlayer for those files, but it doesn't work ob gutsy).

---

### Post by BigSilly on 2007-10-23
I'm having a bit of bother in this regard too. I'm hoping someone puts up a "multimedia how-to" stcky for Gutsy soon! I thought I'd downloaded all the requisite codecs and media players from the official repos and Medibuntu, but obviously not, since like the OP here I cannot play some trailers. Particularly [these trailers for Iron Man here. ]("http://www.empireonline.com/futurefilms/film.asp?id=9756")Just click the "Watch the trailer" button for a selection of different media types. I can't seem to get any of this selection to run in Gutsy, though I have managed to get the BBC media to run on their site. If you can offer any help regarding multimedia in 7.10 please let me know.

Many thanks in advance.

---

### Post by hanzomon4 on 2007-10-23
I posted about this in another thread:> **hanzomon4 said:**
> Gstreamer can play mp3 and mp4 just fine, i think you only need to try and play one of these files and it will install the codecs for you. 

Rmvb is different however gst can't play these files, but xine+w32codecs can. 

First you need to add the medibuntu repos ```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
``````
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Next run this command to apt-get everything you need to play just about any format```
 sudo apt-get install libxine1 libxine1-ffmpeg libxine1-gnome libxine1-plugins totem-xine w32codecs libdvdcss
```

Now there's a bug with xine and wmv but it's easy to fix just edit  ~/.gnome2/Totem/xine_config```
 gedit .gnome2/Totem/xine_config 
``` **Change the lines marked in red from this**
```
# priority for win32a decoder
# numeric, default: 0
[color=red]**#engine.decoder_priorities.win32a:0**[/color]

# priority for win32v decoder
# numeric, default: 0
[color=red]**#engine.decoder_priorities.win32v:0**[/color]
``` **To this** ```
# priority for win32a decoder
# numeric, default: 0
[color=red]**engine.decoder_priorities.win32a:5**[/color]

# priority for win32v decoder
# numeric, default: 0
[color=red]**engine.decoder_priorities.win32v:5**[/color]
```

Now totem will play all of your videos,even rmvb vids. 
Hope this helps.

---

### Post by MaximB on 2007-10-23
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gutsy/free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 88.198.37.77 80]
Failed to fetch [http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gutsy/non-free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 88.198.37.77 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
maxim@maxim-ubuntu:~$  sudo apt-get install libxine1 libxine1-ffmpeg libxine1-gnome libxine1-plugins totem-xine w32codecs libdvdcss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxine1 is already the newest version.
libxine1 set to manual installed.
libxine1-ffmpeg is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

---

### Post by boyturtle on 2007-10-23
hmm, I've got a similar problem in that I cant see the BBC videos, firefox offers to add xine or mplayer plugins for audio /x -pn realaudio rather than a video plugin. I also get different error  when trying to update medibuntu >  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

gpg: no valid OpenPGP data found.
 and the same error for the other bit
> sudo apt-get install libxine1 libxine1-ffmpeg libxine1-gnome libxine1-plugins totem-xine w32codecs libdvdcss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


If I load one of the plugins offered, all I get is audio and no video

---

### Post by BigSilly on 2007-10-24
Followed all your instructions hanzomon4. I'd already enabled the Medibuntu repository and got those codecs, the only difference for me was the installing of totem-xine, which had to remove totem-gstreamer. When I enter your gedit line into a terminal the xine-config screen contains nothing! There's literally nothing there to edit. What did I do wrong, and what should I do to put it right?

On the plus side I'm now getting some audio, but a big black screen now says "no video" when I select one of those trailers above.

---

