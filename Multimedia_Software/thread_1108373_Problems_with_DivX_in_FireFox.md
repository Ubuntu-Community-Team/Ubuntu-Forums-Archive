---
title: "Problems with DivX in FireFox"
date: 2009-03-27
forum: Multimedia Software
---

### Post by billytalent on 2009-03-27
Hey everyone, im wondering if you can help me solve one of the biggest problems with my ubuntu install, streaming Divx through FireFox.

This is the story, everytime I attempt to watch divx via mplayer ff plugin the movie stalls and goes for 3 seconds and then stalls again. This continues for the whole video. 

Having done heaps of research via google to find a solution im at a loss. 

How can i easily stream divx content through FireFox?

screenshot of plugins: [http://i44.tinypic.com/2u76cfn.png](http://i44.tinypic.com/2u76cfn.png)

[IMG]http://i40.tinypic.com/jqq8a0.jpg[/IMG]

...another of the problems with mplayer is that i cant see how much of a video has loaded.

---

### Post by germanix on 2009-03-28
I have been trying to solve this problem for over a year now, but have had only limited success. I have posted this problem on more than once and can tell you the following:
I have been informed that there are no Linux version of the Divx player at this time, so this Divx Player plug-in that you installed, I suspect hinders more than it helps and you should probable de-install it.
I suggest you do the following.
open the Terminal and run this command; (copy and paste the command below)

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

This will add the medibuntu repository and install codecs for xvid, divx and a number of other video codecs, audio codecs, flash, java, commercial dvd playback, ...

Just copy/paste the command, press enter, enter your password (you won't see what or how many letters you type) and press enter again.

During installation a EULA for Java will pop up,press tab and press enter to agree.

When it's all done you are set.
You will find however that you can then watch (from CD/DVD) all Divx and Flash movies, can also stream all Flash movies, (regardless if you are using Totem, MPlayer, VLC player etc) but on most sites you still cannot stream Divx. I did find some sites where I was able to stream Divx but when using the VLC player I could not start/stop nor go to full screen, Mplayer allowed me to stop/start but would not go full screen, and gecko worked, but only on this one site (Movielab.tv), on other sites like (Kino.to) I could not stream Divx at all no matter which player I used.
I have googled this, asked question on this forum, but to date no advice that I recieved solved this problem for me. I hope you have better luck.
have a nice day

---

### Post by binbash on 2009-03-28
Can you guys please post a link to  a divx video?I am going to tweak the configs

---

### Post by billytalent on 2009-03-28
I have sort of figured out this problem. Default ubuntu install uses totem player with gstreamer installed. Get rid of this, delete it whatever...

then install mplayer, follow this little [handy guide]("http://tinyurl.com/8syexr") i found, configure the settings to suit...

and all should work :)

---

### Post by germanix on 2009-03-28
Your _handy guide_ link takes me to a website in French which I am unable to read?
Do you have this guide in english or german?

---

### Post by germanix on 2009-03-28
binbash, go to [www.kino.to](www.kino.to) and chose any Divx movie you want

---

