---
title: "dvd library similar to windows media center"
date: 2009-11-26
forum: Multimedia Software
---

### Post by kevinpfoote on 2009-11-26
hey guys. new here, and i don't know a whole lot about linux or its distros, so please bear with me.

here's the deal... i currently have about 250 dvds on an external hard drive. all dvds are in .vob format - they are a carbon copy of the actual dvd structure. i can play them in windows media center using the dvd library tweak in the registry. it allows me to browse through all of the dvds on the hard drive (dvd cover art and all), then pick which one i want to watch, then BAM it's playing. all of them have menus and everything just like the actual dvd.

my issue is this - i would like something with a similar functionality on linux. i am trying to get rid of my media center pc and use the other_os function on my playstation 3 to serve my media center needs. i have heard of several different video programs for linux, but i am unclear on what i can use to do what i specifically want to do.

so, in a nutshell, i'm wondering what is out there for linux that would play .vob dvd structures from an external hard drive, and allow me to browse through the dvd collection (with dvd cover art).

i know very little about linux softwares but would really like to learn what direction i should be going. a little bit of guidance could save me weeks of trial and error. please help! i really would like a solution!

---

### Post by jacobs444 on 2009-11-26
Use VLC media player, it will play just about everything (even corrupt virus laden wma files) without infection! Linux baby. Also you may want to install the libdvdcss2 package to rip/read your dvds for a legal backup-haha. seriously those two should do it, though they arent like window media center. I think you might need ,mythbuntu for that. never used by me so don't quote on the mythbuntu! Love, Linux And Fun for4 you!

---

### Post by ilil on 2009-11-26
For playing DVD from hard drive you can you use xine or totem-xine:
```
xine dvd://path/to/dvd/folder
```
```
totem-xine dvd://path/to/dvd/folder
```

---

### Post by airtonix on 2009-11-26
**elisa,** (now called [Moovida Media Center]("http://www.moovida.com/"))
[http://www.ubuntugeek.com/how-to-install-elisa-media-center-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-elisa-media-center-in-ubuntu.html)
 # karmic : sudo apt-get install elisa
 <optional> karmic : sudo apt-get install elisa-plugins-good
 <optional> karmic : sudo apt-get install elisa-plugins-bad
 <optional> karmic : sudo apt-get install elisa-plugins-ugly

**sofa**
[http://sofa.sourceforge.net/?s=downloads](http://sofa.sourceforge.net/?s=downloads)

---

### Post by kevinpfoote on 2009-11-26
airtonix, the elisa (moovida) software looks VERY nice. it is exactly what i am looking for and i think it is actually more attractive than windows media center.

curious, though, as to if it plays .vob files. it doesn't list that filetype on the website, but i see you have included code for some plugins. is the .vob codec included in those plugins?

---

### Post by kevinpfoote on 2009-11-26
update:

i downloaded the windows version of moovida to test out its functionality. everything works fine except for one small but important detail - my dvds from my hard drive do not show up in the "video library" section of the software. i cannot find any settings that would enable it to... anyone have any suggestions?

---

### Post by kevinpfoote on 2009-11-27
bump

---

### Post by mykrob on 2009-11-27
do they show under uncategorized? you may need to help the app determine what movie each file is. Had to do this with a few of mine that could have been a few diffferent titles..

---

