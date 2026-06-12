---
title: "[SOLVED] Totem can't create all thumbnails, can I use Mplayer instead?"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by mysticmatrix on 2007-08-27
There are certain video files whose thumbnails are not displayed in nautilus. I've noticed these are the file which can't be played in Totem due to codec limitations of Gstreamer. 

Is there any way I can use Mplayer(or some other thing) to generate thumbnails for Nautilus? I would like it for my Real Media and WMV9 videos.

---

### Post by mysticmatrix on 2007-08-27
*bump*

---

### Post by mysticmatrix on 2007-08-28
Ok,  I found the solution myself and would write it down so that others might also be helped.

The Problem: Totem is currently not able to play certain files like wmv9 and real media files. So when nautilus encounters any such file, it fails to create a thumbnail for it. We know that Mplayer([www.mplayerhq.com](www.mplayerhq.com)) can play almost all files most people will ever encounter. So a good idea would be to use Mplayer to generate thumbnails.

Solution:
Here we go 

1) Download the Mplayer-video-thumb script [from here]("http://me2030581.googlepages.com/") ( A great app written by Ravinder Rathi) to your home directory.

2) Extratct the tarball in your home folder.(By using Right Click-->Extratct Here...)

3) Open the terminal and type

```
sudo apt-get install mplayer imagemagick
```

Note that you must enable universe repository for this.

4) Now type

```
cd
cd mplayer-video-thumb-1.3-3
chmod +x setup.sh
sudo ./setup.sh
./gconf.sh
```

5) Now Mplayer will create thumbnails of all new media files that Nautilus will encounter. If you want that Mplayer should recreate all your previous thumbnails too, use the command

```
rm -rf $HOME/.thumbnails/large/
rm -rf $HOME/.thumbnails/normal/
rm -rf $HOME/.thumbnail/fail/gnome-thumbnail-factory/
```


Hope this would help anyone who wants a similar setup.

NOTE: If you are unsatisfied at any stage, and want to restore Totem to generate your thumbnail, you can download the script attached and place it with video_ext file of Mplayer-thumbnailer and run in terminal
```

chmod +x unset_gconf.sh
./unset_gconf.sh
```

---

### Post by oomingmak on 2007-09-22
I have yet to try this, but thank you for coming back to post your solution.

---

### Post by khelu on 2007-10-09
seems that i cant get the file u mentioned in ur post could u pls post your files somewhere else in d net rather than goole one, thanx 
just want my thumbnails bak thts all with mplayer.

---

### Post by patchoro on 2007-10-16
sudo apt-get mplayer imagemagick 
should be:
sudo apt-get install mplayer imagemagick

Otherwise this worked like a charm. Thank you very much!!

---

### Post by trmiv on 2007-10-19
This didn't work for me in gutsy.  None of the videos previewed and then only some of the jpg's previewed.  I had the file limit for previews set to 1gb,

---

