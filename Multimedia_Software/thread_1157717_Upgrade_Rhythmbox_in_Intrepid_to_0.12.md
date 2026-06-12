---
title: "Upgrade Rhythmbox in Intrepid to 0.12"
date: 2009-05-13
forum: Multimedia Software
---

### Post by nacho-wan on 2009-05-13
In my laptop I Have several partitions. In one I have a Fat drive with my music, one ext3 with my home directory, one ext3 with intrepid ibex and last week I made a new ext4 partition with jaunty jackelope.

Since I haven't moved yet to use jaunty daily, I still boot in intrepid from time to time. Since both share the same home directory, I'm having trouble in rhythmbox in intrepid because it doesn't load its library and play count but when I load jaunty, rhythmbox finds everything ok.

I suppose this is because jaunty uses rhythmbox version 0.12 and intrepid 0.116. I suppose I can fix this by upgrading the intrepid version, so it would load the library and play count fine as it does in jaunty.

I have been unable to upgrade intrepid rhythmbox 0.116 up to 0.12 from synaptic. Can somebody explain me how to do it from the command line? Thanks in advance

---

### Post by brookie on 2009-05-28
hi nacho,
i'm having the same problem
i downloaded the 0.12 version at [http://projects.gnome.org/rhythmbox/]("http://projects.gnome.org/rhythmbox/") but i falied on the manual install.
i read the install text and followed the steps, 1. ./ocnfigure, 2. make... and i fail on make, no makefile error.
let me know if you figure this out or maybe we just use older version of rhythmbox on intrepid
cheers,
brookie

---

### Post by dartmusic on 2009-05-28
I installed from a deb posted at getdeb.net.

Try this: [http://www.getdeb.net/app/Rhythmbox](http://www.getdeb.net/app/Rhythmbox)

---

### Post by brookie on 2009-05-30
Okay. So I see there are two different versions. 12.0 intrepid and 12.1 jaunty. The gnome site says that the latest stable version is 12.1 and they do not specify wheather it is jaunty or intrepid version. I don't think the sw is made for specific os version is it? I might try the 12.1 on intrepid. Thanks for the info.

...12.1 deb package install failed on intrepid: dependency is not satisfiable libdbus-glib-1-2, however, synaptic package manager shows that libdbus-glib-1-2 is installed. 

the 12.0 version installed with no problem. i hope this stops rhythmbox from crashing when it cannot stream from radio paradise

great station by the way, [http://www.radioparadise.com/index.php](http://www.radioparadise.com/index.php) and you can listen at 192k. 

cheers, 
brookie

---

### Post by Vadi on 2009-06-02
[http://www.getdeb.net/app/Rhythmbox](http://www.getdeb.net/app/Rhythmbox) works as pointed out.

---

### Post by Arup on 2009-06-02
Getdeb updated rhythmbox to latest version 12.2 which works fine on my Jaunty x64, suggest you get that.

---

