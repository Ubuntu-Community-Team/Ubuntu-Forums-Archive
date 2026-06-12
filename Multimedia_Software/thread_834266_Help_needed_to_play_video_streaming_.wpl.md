---
title: "Help needed to play video streaming *.wpl"
date: 2008-06-19
forum: Multimedia Software
---

### Post by _x_MaD_x_ on 2008-06-19
Hello everyone
I'm trying to play some nacional streams and one of them is:

[http://wms.velocix.com/ws/06f3060000000000/stream.wpl](http://wms.velocix.com/ws/06f3060000000000/stream.wpl)

But I can't, is there anyway to play it, any missing codec or something?
Thank you all

---

### Post by _x_MaD_x_ on 2008-07-02
Any one???

---

### Post by kostkon on 2008-07-02
I just downloaded and opened the *.wpl* file, which is a playlist metafile that redirects to media streams/media files/other metafiles and I found the actual stream file but again it does not play in the media player. It seems the service is down or does not work for some unknown reason.

The stream's url is
```
http://212.187.231.2/VXWMS/ws/06f3060000000000/data?MSWMExt=.asf
```
if you want to try it yourself.

---

### Post by _x_MaD_x_ on 2008-07-03
Sorry I'm a really NooB :(
I've never tried to open the wpl...
But I've tried now and the output that I have is  

<?wpl version="1.0"?>
<smil>
    <head>
        <meta name="Generator" content="Velocix"/>
        <title>playlist</title>
    </head>
    <body>
        <seq>
            <media src="rtsp://212.187.212.205/VXWMS/ws/06f3060000000000/data"/>
        </seq>
    </body>
</smil>

SO where do you find 

[http://212.187.231.2/VXWMS/ws/06f3060000000000/data?MSWMExt=.asf](http://212.187.231.2/VXWMS/ws/06f3060000000000/data?MSWMExt=.asf)

Thank you all

---

### Post by _x_MaD_x_ on 2008-07-04
Kostkon.
I would like to know how do you take that link under a *.WPL I have more links to find and I would like to know how to do it.
Thank you about your Help

---

### Post by kostkon on 2008-07-05
> **_x_MaD_x_ said:**
> Kostkon.
I would like to know how do you take that link under a *.WPL I have more links to find and I would like to know how to do it.
Thank you about your Help
I first tried to open the file with *Totem* but it did not play.
Then I just opened the terminal and downloaded the *.wpl* file with *wget*
```
wget http://wms.velocix.com/ws/06f3060000000000/stream.wpl
```
and I opened it with the text editor. I saw that it was a [*SMIL*]("http://en.wikipedia.org/wiki/Synchronized_Multimedia_Integration_Language") file and *Totem* is supposed to support *SMIL* files thus the problem has to be somewhere else, i.e. the stream is dead.

Indise the file I saw the following url
```
rtsp://212.187.231.6/VXWMS/ws/06f3060000000000/data
```

I also downloaded this file, i.e.
```
wget http://212.187.231.6/VXWMS/ws/06f3060000000000/data
```

and after I opened it with the text editor I found the actual url of the stream.

I tried it in *Totem* but again it didn't play.

The thing is that I did the above just to make sure that the problem is in the stream and not *Totem*, i.e. if *Totem* had a problem handling the *.wpl* file because it cannot to read such files (actually it can) or because the file was malformed.

Thus, after doing the above I found that there is a problem with the stream. The stream is down or for some unknown reason it does not give a response to *Totem* or something else.

Did you manage to play the stream? What media player do you use?

---

### Post by _x_MaD_x_ on 2008-07-07
Great how to...
I'm a windows user and never remind me to edit the files.
Thank you so much. That is a great help.

---

### Post by longhorm on 2011-05-13
> **_x_MaD_x_ said:**
> Hello everyone
I'm trying to play some nacional streams and one of them is:

[http://wms.velocix.com/ws/06f3060000000000/stream.wpl](http://wms.velocix.com/ws/06f3060000000000/stream.wpl)

But I can't, is there anyway to play it, any missing codec or something?
Thank you all

Hi _x_MaD_x_,

I installed **GStreamer plugins for mms, wavpack, quickitme, musepack**

to install this plugin, i open Ubuntu Software center and find by typing **mms **in the searchbox. Below photo is for your reference.

_[IMG]http://i24.servimg.com/u/f24/11/74/16/17/screen10.jpg[/IMG]_

Before I install that plugin I can't open the .wpl file with Totem Movie Player. After installing, it working fine. Cheer!

---

