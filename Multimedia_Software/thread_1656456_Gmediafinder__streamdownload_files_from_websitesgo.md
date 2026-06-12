---
title: "Gmediafinder : stream/download files from websites/google/youtube..."
date: 2010-12-30
forum: Multimedia Software
---

### Post by smo on 2010-12-30
hi

the original idear for this soft was just to get sounds from mp3 searchengines then be able to stream or download it...(to search samples...)

since i was unable to find all the sounds i wanted, i added youtube and google search (google is really a try....), visualisations....

and finally here's gmediafinder

Videos:

[IMG]http://www.penguincape.org/downloads/pics/Capture-video.png[/IMG]


Audio:

[IMG]http://www.penguincape.org/downloads/pics/Capture-audio.png[/IMG]


Note:
-----
i had to build a custom version of python-beautifulsoup because we have the v 3.1 in the ubuntu mainstream wich is (for me) a very bad idear... so i made a v3.2 package on my ppa, and now it works well...(and can fix many others softwares in the same time...)

you ll have to add the ppa to your sources to get this new package even if you don t install gmediafinder thru the ppa...


Installation:
-------------

By PPA (RECOMMENDED):
```

sudo apt-add-repository ppa:s-lagui/ppa
sudo apt-get update
sudo apt-get install gmediafinder

```


from git (do not mix with ppa!):

```

sudo apt-get install python-beautifulsoup python-html5lib python-gst0.10 gstreamer0.10-ffmpeg python-gdata libvisual-0.4-0 libvisual-0.4-0-plugins
git clone git://github.com/smolleyes/gmediafinder.git
cd gmediafinder
sudo python setup.py install
gmediafinder

```

or just start it directly after the git-clone... : 

```
cd GmediaFinder
python gmediafinder.py
```


all bugs found are now fixed but let me know if you find something wrong!

i think it just miss a fullscreen mode and maybe a better organisation in the gui...

thanks for your comments, idears... ;)

sorry for my english and if i posted in a bad section...^^ (no "your free developments" section like ubuntu-fr?)

++

---

### Post by smo on 2011-02-13
up !

news here:

[http://gtk-apps.org/content/show.php?content=138588](http://gtk-apps.org/content/show.php?content=138588)

++

---

