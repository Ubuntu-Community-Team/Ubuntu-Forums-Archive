---
title: "Gmencoder (mencoder GUI) problem - solved"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by rafalr on 2007-10-28
There is this handy mencoder GUI at [http://gmencoder.sourceforge.net/](http://gmencoder.sourceforge.net/) (pity no more supported by author) and an "Ubuntu" debian package is available on the net, and working with my Feisty:

- either Polish Ubuntu download, quite fresh file (26-Mar-2007)
[http://download.ubuntu.pl/_Breezy_Badger/gmencoder/](http://download.ubuntu.pl/_Breezy_Badger/gmencoder/)

- or French site with nice screenshot
[http://doc.ubuntu-fr.org/gmencoder](http://doc.ubuntu-fr.org/gmencoder)

The problem I had was twofold:

1. the "gmencoder_opts" file was missing
- it was mentioned in "readme" as necessary to use options of cropping, scaling, deinterlacing etc
- I downloaded an old source.tgz file from the homepage - and it contained the _opts file, so after unpacking and moving to ~home/.gmencoder_opts all the mentioned options were available

2. the films coded in gmencoder after choosing mpeg4 (lavc) codec were not visible for my stationary DVD player
- although gmencoder informs that choosing this codec guarantees divx5 and xvid compatibility, it does not !
- so I opened a new file "~home/.mplayer/mencoder.conf" and edited it to contain only this line:
ffourc=DX50=1 # this for DivX5 compatibility;
or alternatively this line:
ffourc=XVID=1 # this for XVID compatibility;
- now gmencoder (like any other programm calling mencoder, as well as mencoder itself) will use the mencoder.conf file with then option in it
- I have tested that both options work (that is we get either DivX5, ffmpeg video or XviD, ffmpeg video) and both are perfectly recognised by stationary DVD player.

I know that you will say mencoder is to be used by command line and I agree, but when you do 2 pass encoding with lots of options you can easily make mistakes, and a simple gnome dedicated GUI like gmencoder (pity no more supported) can spare you the errors and do the job.

rafal

---

