---
title: "Viedeo playback problems (Ubuntu+Medibuntu)"
date: 2009-02-19
forum: Multimedia Software
---

### Post by c-m on 2009-02-19
I have the 120GB HDD Linux version of the Acer Aspire One.

I have installed a clean copy of Ubuntu and installed the VLC and medibuntu (for media).

Standard definition xvid plays back fine on the internal screen, but when hooked up to my 1650x1050 monitor, I notice tears and an occasional pause every 10 seconds or so.

I've read many reports about people being easily able to play back 720p content on the AAO, yet every 720p file I have tried to open is completely unwatchable. i.e the video will update a scene just once every 4 seconds or so, meaning I end up with sound but just a bunch of stills.

Does anyone have any suggestions on how to fix this?

Just to add - I'm using Ubuntu 8.10 UMPC edition

---

### Post by binbash on 2009-02-19
I was just like you before installing svn version of mplayer and x264 encoder.There is a repo for that, but i dont remember at the moment.But you can find which one navigating via firefox (it is from my sources.list ) :

deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/m-buck/ppa/ubuntu](http://ppa.launchpad.net/m-buck/ppa/ubuntu) intrepid main
deb [http://debian.vogelweith.com/](http://debian.vogelweith.com/) intrepid zgegthemes
deb [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/suraia/ppa/ubuntu](http://ppa.launchpad.net/suraia/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/phylu/ppa/ubuntu](http://ppa.launchpad.net/phylu/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/flam3/ppa/ubuntu](http://ppa.launchpad.net/flam3/ppa/ubuntu) intrepid main


PS : At the moment i am using gnome-mplayer, and video output set as Xv , however you may need to disable compiz if you are using ati or setting video output to X11

---

### Post by c-m on 2009-02-19
I generally use VLC for my video playback. If i install this new codec, is there a way to make VLC and all other players use it was the default for video rather than say ffmpeg or something else?

---

