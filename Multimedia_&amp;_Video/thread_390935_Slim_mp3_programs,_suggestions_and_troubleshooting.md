---
title: "Slim mp3 programs, suggestions and troubleshooting."
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by Longwing on 2007-03-22
I'm a noob, bare with me if I'm doing something dumb here:

I've been running Ubuntu on my Fujitsu p1120 for quite some time. For a while, it was a Frankenstein install, Ubuntu with a Xubuntu desktop, but with Nautilus running at startup and Enlightenment for the window manager. The typical cobbled-together and overly customized install. I grew tired of it never quite working right, and particularly tired with the slow response (Nautilus was too much for my poor innocent Transmeta processor). 

In an attempt to simplify things, I recently upgraded to a straight Xubuntu 6.10 release. The upgrade went off with only one hitch: I can't seem to get gxine, the default Xubuntu media player, to run correctly. [U]Every time I open an mp3 in gxine, it plays about half a second, and then gxine closes for no apparent reason.
[/U]
I worked around this by installing Rhythmbox, which works as it should. But Rhythmbox is (from the perspective of my 800mhz Transmeta) bloated. I love the program, but it slows the whole system down. (partly by loading some gnome-dependencies, I think.)

Does anyone know how to restore Gxine to health? Or can they suggest a light, fast, and simple mp3 player? I need something which can play long playlists (for my commute) but other than that, the lighter on resources, the better.

---

### Post by tcrroadie on 2007-03-23
Have you taken a look at XMMS.  XMMS is an old gtk1 music player that is extremely light on resources.  And xmms also has the ability to create a playlist.  You can also get custom skins for xmms from gnome-look.org

```
sudo apt-get install xmms
```

There is also a newer gtk2 version of xmms called Beep Media Player that you may also want to try.
```

sudo apt-get install beep-media-player
```

---

### Post by racoq on 2007-03-23
Don't forget audacious, is a fork from beep media player, and it is a modern gtk2 , application, i recommend this last one because, it is  supported and in current development. Beep media player and xmms are dead projects.

```
sudo apt-get install audacious
```

---

### Post by Longwing on 2007-03-26
Thank you both for your suggestions, I'm going to install and try each of them. For anyone encountering the same problem as me, I found that gxine behaved after I installed the gxineplugin package:

```
sudo apt-get install libxine-extracodecs ffmpeg lame faad sox mjpegtools libxine-main1 gxineplugin
```I got that code from _[COLOR=Black][this guide]("https://help.ubuntu.com/6.10/xubuntu/desktopguide/C/multimedia.html")[/COLOR]_, which, honestly, I should've found before posting. When I ran the code, the only package which wasn't already at it's latest version was gxineplugin. Once that was installed gxine stopped complaining.

racoq, I'd like to try audacious, but it shows up as "package not found" when I try to install it. I've both Universe and Multiverse repositories enabled.

---

### Post by Longwing on 2007-04-19
tcrroadie and racoq, I wanted to thank you both for your suggestions. Having had some time to toy with the programs suggested here, I'm currently using XMMS for my MP3 playing. The wonderfully low memory and cpu footprints make it perfect for my application. 
I have the others installed, and may give them some more attention later, but XMMS does the job just fine for now.

Thanks again for all your help.

---

