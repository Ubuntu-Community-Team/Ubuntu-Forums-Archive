---
title: "Given up on SN9C20x cam - Anyone got any experience with Creative Live! Voice Webcam?"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by oserdavid on 2007-07-24
Does anyone have any positive experience with this particular webcam, which seems to be fairly rare (bodes ill. Last post mentioning it was in Feb). It's a very good cam - but doesn't seem to work in Ubuntu 7.04 and any drivers I have found online do not work. . Tried all mxhaard's stuff. That's now two webcams I can't get to work in Ubuntu!! :-({|=

Edit: Though I notice its mic seems to be working.... (Skype test)

---

### Post by SqRt7744 on 2007-07-28
re. sn9c20x:

 works fine for me with the (unfortunately) binary driver I picked up from here:
[http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

You can test it with any video-4-linux 2 application, there's one on the same page called videoview.  Also Ekiga supports v4l 2.

also, i added the line

sn9c20x
to /etc/modules
so that it loads the driver automatically at boot.


good luck.

---

### Post by oserdavid on 2007-07-28
> **SqRt7744 said:**
> re. sn9c20x:
 works fine for me with the (unfortunately) binary driver I picked up from here:
[http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)
You can test it with any video-4-linux 2 application, there's one on the same page called videoview.  Also Ekiga supports v4l 2.
also, i added the line
sn9c20x
to /etc/modules
so that it loads the driver automatically at boot.
good luck.
Many, many thanks for the heads up. It's a brand new .deb file at 
[http://www.linux-projects.org/modules/mydownloads/](http://www.linux-projects.org/modules/mydownloads/)
So I just downloaded it and double-clicked it - and provided I had Terminal showing and agreed to the license at the appropriate moment - it just installed itself.  Working fine at next startup without adding any lines - and recognised by Videoview. Also, apparently by aMSN (not sure yet) but not by Ekiga (at least not the version that came pre-packaged with Ubuntu 7.04, and is not updating itself). So the problem seems to be the paucity of apps that can make use of it. But at least we are now getting somewhere. =D>

Now, if only the linux version of Skype (I know, wash my mouth out) would make use of it, I'd be perfectly satisfied!

---

### Post by starlingjms on 2008-03-06
hi everyone,
i 'm an extreme beginner of ubuntu and i'm enjoying it, but this webcam make me mad.
here are some informations about my settings:

1)i have a creative live!cam voice
2)i'm using ubuntu 7.04 in order to use the unlimited sn9cxxx from [http://www.linux-projects.org/modules/mydownloads/](http://www.linux-projects.org/modules/mydownloads/)
3)my kernel is 2.6.22.16.generic and it should be the right one suggested by linux project
4)the led on the cam is not light
5)i can see the webcam from hardware information 
6) as oserdavid said the microphone in it is working

althought my webcam is not working. is there something i'm missing? i've just installed the pack with sn9cxxx drivers, is there something i am missing?
hope someone can help!thank you very much :)

---

