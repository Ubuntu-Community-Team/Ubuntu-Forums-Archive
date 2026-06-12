---
title: "m4a files not recognized by gtkpod"
date: 2012-01-17
forum: Multimedia Software
---

### Post by rleck on 2012-01-17
I have just jumped from Ubuntu 10.10 to 11.10 (fresh install) over Christmas, and my first attempt to use gtkpod under 11.10 has ended in failure. gtkpod doesn't recognize my .m4a files and won't transfer them. Banshee was happy to transfer them and even play them, but they are not in the ipod's menus and the ipod's databasse is now corrupt and the cover art gone, etc. Since a flush of the ipod is clearly pending, I'm game to try some things!

Doing multiple searches turns up a lot of advice. (This is an ongoing issue it seems) The gtkpod-acc transition package is long dead. There is conflicitng advice as to whether the libmp4 in the faad2 package is or isn't the solution, depending on the date of the (older) posts. More recent posts say to install libmp4v2-0, but this packaged has been deleted from the oneiric repositories, although it apparently saved a lot of bacon for 11.04 users. 

I've got a Nano 5g, 11.10 amd64 and the following:

libgpod4         0.8.0-3build1
libgpod-common   0.8.0-3build1

gtkpod           2.1.0-1ubuntu1
gtkpod-data      2.1.0-1ubuntu1
libgtkpod1       2.1.0-1ubuntu1

Any suggestions?

with thanks for reading this...

---

### Post by rleck on 2012-01-20
Turns out this is a confirmed bug:
[https://bugs.launchpad.net/ubuntu/+source/gtkpod/+bug/883962](https://bugs.launchpad.net/ubuntu/+source/gtkpod/+bug/883962)

User keplicz there reports this workaround:
"It seems that the gtkpod 1.0 from natty used a libmp4v2 library in order to process M4A files. The newer version doesn't nor is libmp4v2 available.

Downgrading gtkpod using gtkpod, gtkpod-data, libgpod4 and libmp4v2-0 packages from natty seems to do the trick."

I'll give it a try and edit this with the results.

---

### Post by SirWeazel on 2012-04-07
What were your results? Any step by step instructions would help alot. Im having the same issue. I even copied a movie from the iPod that I know plays, but I get yhe error when I try to copy it back. Wierd that I can read the file but copy it back to the iPod with a different name?? Thsnjs for any help.

---

### Post by charlie99 on 2013-03-18
FTR, work-around for this issue on a Lubuntu 12.10 system: (strictly NOT supported since Natty is no longer supported):

1. Ensure /etc/apt/sources.list contains the following lines:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse

2. execute the following commands:

```
sudo apt-get update
aptitude -vv versions ~nlibmpeg4ip
aptitude -vv versions ~ngtkpod
aptitude -vv versions ~nlibgpod4
sudo apt-get remove gtkpod
sudo apt-get autoremove
sudo apt-get remove libmp4v2-2
sudo apt-get install libmpeg4ip-0
sudo apt-get install libgpod4=0.8.0-2
sudo apt-get install gtkpod-data=1.0.0-0ubuntu1 gtkpod=1.0.0-0ubuntu1
gtkpod --help
```


NOTE that the programme used to create the m4a file has to populate the 'tag' fields with album, artist, track etc (not sure of the minimum requirement).

---

