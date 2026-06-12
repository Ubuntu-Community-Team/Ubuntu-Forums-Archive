---
title: "avconv and libx264 ... no parameter is working .. it seems so"
date: 2013-04-08
forum: Multimedia Software
---

### Post by Mr Zottix on 2013-04-08
Hello, at the moment i am trying to record my desktop. The Command i am using is:

```
[COLOR=#000000]avconv -f x11grab -r 30 -s 1920x1080 -i :0.0 -f pulse -i default -c:v libx264 -preset ultrafast -qp 0 -threads 0 -c:a pcm_s16le -y screencast.mkv[/COLOR]
```

But this causes a really worse framerate and bitrate ist ~1000k ... that should be much more higher.

If i dont use the parameters -preset and -qp ... libx264 is working well and is doing his job but it seems i cant create a lossless screencast-file.

What could be the reason for that behavior? .... 

Thats an image of the encoding 

[IMG]http://i.imgur.com/s7yvoAw.png[/IMG]

And an Image of my Performance during the screencast:

[IMG]http://i.imgur.com/HVCPV5yl.jpg[/IMG]


The Harddisk is a SSD .. so .. there the Datatransferrate of the Disk should not be a reason.

What can be a reason for that?

Thx

---

### Post by Mr Zottix on 2013-04-08
i solved it ... 

Could it be that is some bug in avconv for using pulseaudio?

If i am using 

```
-f alsa -ac 2 -i pulse
```

thats working very well ... so ... why the other syntax isnt working?

---

