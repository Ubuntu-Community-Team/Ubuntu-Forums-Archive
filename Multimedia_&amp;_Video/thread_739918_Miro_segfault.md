---
title: "Miro segfault"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by ba5e on 2008-03-30
Miro repetadly segfaults on me when playing a video:


```
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0xb9e5aac>
Segmentation fault (core dumped)
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...
```

I have a feeling this has something to do with codecs etc, but there are no options in miro to select.

Im running Hardy beta with Miro 1.1.2 (r6194)

---

### Post by ba5e on 2008-03-30
bump? any one have any ideas?

---

### Post by -X- on 2008-03-30
Same issue here. I just rediscovered Miro and now it's crashing on me :'-(

---

### Post by ba5e on 2008-04-01
I just tried reinstalling all my codecs, and removing unnecesary ones, to no avail

---

### Post by Damiox on 2008-05-31
just installed on hardy ....same thing...played intro vid fine then seg faulted after others

---

### Post by jspiers on 2008-06-30
I think I am having the same problem.  I haven't managed to watch any videos with Miro; it loads fine but dies when I hit play.  Looks like I am getting a segmentation fault as well.  Maybe someone can look at the output below (running miro from a terminal window) and offer some advice on a possible fix.  I am running Ubuntu 8.04 and Miro 1.1.2 (r6194).

Cheers.



$ miro

*************** INITIALIZE MOZEMBED
location: /usr/lib/xulrunner-1.9/libxpcom.so 
before 3
INFO     Starting up Miro
INFO     Version:    1.1.2
INFO     Revision:   [https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1.2/tv/resources](https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1.2/tv/resources) - 6194
INFO     Builder:    buildd@vernadsky
INFO     Build Time: 1202986841.91
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/jeff/.miro/sqlitedb
TIMING   Database load slow: 1.067
TIMING   idle (Initializing database) too slow (1.283 secs)
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     Creating video display...
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
INFO     loaded renderer 'xinerenderer'
INFO     First URL is [https://www.miroguide.com/](https://www.miroguide.com/)
TIMING   Icon clear: 0.009
INFO     Starting movie data updates
INFO     got file:///tmp/tmprApz2Z.html
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (1.410 secs)
INFO     got file:///tmp/tmpQ6Qqoe.html
INFO     First URL is [https://www.miroguide.com/](https://www.miroguide.com/)
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is [https://www.miroguide.com/](https://www.miroguide.com/)
INFO     got [https://www.miroguide.com/](https://www.miroguide.com/)
INFO     First URL is [https://www.miroguide.com/](https://www.miroguide.com/)
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     *** Daemon ready ***
WARNING  eventloop: Interrupted system call
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     got action:handleSelect?area=tablist&viewName=staticTabs&id=465&shiftDown=0&ctrlDown=0
INFO     got file:///tmp/tmpxi2z2V.html
INFO     got action:handleContextMenuSelect?id=476&area=itemlist&viewName=matchingNormalDLs
INFO     WARNING: error in Feed.update for Feed - CATWALK Fashion Magazine -- <class 'httpclient.ConnectionTimeout'>: Error: Timeout -- Connection to catwalk.pl timed out
INFO     got action:playNewVideos?id=24
INFO     Playing item with renderer: <frontend_implementation.xinerenderer.Renderer instance at 0x7f71cca3ecb0>
Segmentation fault
jeff@carl:~$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...

---

### Post by jspiers on 2008-07-07
Update:  I read that the problem might lie in the video driver, and that running "miro --xine-driver=opengl" fixed this problem for many people.  I tried that and then the video plays, but very poorly, rapidly cutting back and forth between the video and the menu window.  Any leads would be very welcome here...

---

### Post by frogotronic on 2008-07-11
Try:

$ sudo apt-get install icedtea-java7-jre icedtea-java7-plugin icedtea-gcjwebplugin

---

### Post by tcommbee on 2008-07-17
> **jspiers said:**
> Update:  I read that the problem might lie in the video driver, and that running "miro --xine-driver=opengl" fixed this problem for many people.  I tried that and then the video plays, but very poorly, rapidly cutting back and forth between the video and the menu window.  Any leads would be very welcome here...

I also get the flickering with opengl, but "miro --xine-driver=xshm
" works for me. No idea what xshm is, though.

---

### Post by frogotronic on 2008-07-18
1) Add this to your sources.list (This is the latest & greatest MIRO from the Miro site PPA repos)

```
$sudo gedit /etc/apt/sources.list

## Hardy Miro
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) hardy/
```

2) ```
$sudo apt-get update
```

3) install miro from the PPA repos

4) choose gstreamer from the Options>Play

5) restart Miro

This will work, but the video quality with gstreamer on my ATI card is poor relative to xine.

- CH

---

