---
title: "Multiple video formats to DVD"
date: 2007-07-11
forum: Multimedia Production
---

### Post by Gausian on 2007-07-11
What programs are available with a gui interface that will allow me to convert some of the following...

mp4 container with x264 video, aac audio -> DVD

mkv container with x264 video,  aac audio -> DVD

avi container with xvid video, mp3 or ac3 audio -> DVD

On windows i could just throw anything into nerovision and get a nice DVD with menus and all, but Linux Nero doesnt have this function and im having trouble finding a simple GUI interface program for this on Linux.

---

### Post by fishpie on 2007-07-11
I think qdvdauthor is probably the best program for your needs It's in the repos so it can with synaptic or ```
apt-get install qdvdauthor
```

---

### Post by lintoon on 2007-07-11
I used to use Avidemux for video conversion/editing and Varsha to create the DVD structure.  
It always worked flawlessly.  

Start up Varsha application by typing "java -jar varsha.jar" at a command prompt.  You will get a gui to create the DVD.

You can write directly to a DVD with Varsha but I used to just create an iso and use K3B to write the disc.  I suppose it's because I trust K3B.

Links:

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)
[http://en.wikipedia.org/wiki/Avidemux](http://en.wikipedia.org/wiki/Avidemux)

[http://varsha.sourceforge.net/](http://varsha.sourceforge.net/)
[http://varsha.sourceforge.net/tutorial/index.html](http://varsha.sourceforge.net/tutorial/index.html)

---

