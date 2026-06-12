---
title: "Gmediafinder Can No Longer Play Youtube Videos"
date: 2012-09-27
forum: Multimedia Software
---

### Post by kherring7383 on 2012-09-27
Is it me, or is anyone else have this issue with Gmediafinder?

Several days ago I was able to watch Youtube videos, but since several updates, the videos that are found are skipped when I attempt to start playing them. 

Has something changed?

Ubuntu 12.04/Mint 13
Gemediafinder v9.9.1

---

### Post by smo on 2012-10-10
hi

i m the gmediafinder's creator

i restarted the development of gmf since 1 week, progressive download was added, i fixed youtube, dailymotion and others engines and many things will change in the next few days too

for the moment you can remove your version (installed from ppa i think) then use the git version

[HTML]sudo apt-get install python-gtk2 python-gdata python-gst0.10 gstreamer0.10-ffmpeg libvisual-0.4-0 libvisual-0.4-plugins python-configobj ffmpeg python-mechanize gstreamer0.10-plugins-good python-xlib python-glade2 python-webkit
cd $HOME
git clone git://github.com/smolleyes/gmediafinder2.git gmediafinder2
cd gmediafinder2/GmediaFinder
python gmediafinder.py[/HTML]

i ll make ppa packages for precise soon (need to see on quantal since gstreamer is in v1.0 now and i ll have to make changes i think...) 

thanks !

---

### Post by kherring7383 on 2012-10-11
The suggested fix corrected the problem, thanks for the quick response.

Looking forward to the official PPA release.

---

### Post by smo on 2012-10-13
hi

thanks :)

i juste made a new package for ubuntu precise, some bug fixed again, vimeo added and others engines fixed

i removed the integrated browser for the moment, too many bugs ...

need reports :)

++

---

