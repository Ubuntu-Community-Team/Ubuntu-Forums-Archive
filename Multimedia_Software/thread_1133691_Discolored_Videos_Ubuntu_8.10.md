---
title: "Discolored Videos Ubuntu 8.10"
date: 2009-04-23
forum: Multimedia Software
---

### Post by roh8880 on 2009-04-23
I just made the switch over to Ubuntu and I really can't believe that I stayed with windows for as long as I did! I love linux now.
But, onto my problem. I loaded all of my videos onto my new HD that runs Ubuntu 8.10. I downloaded a codec download here:
[http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/]("http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/")
> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2

I copied and pasted this code into my terminal, and all of my videos have a blue tint to them.
They had the blue tint before, but this codec pack had no effect on the discoloration. 
Being the poopy fingered n00b that I am on Ubuntu, can somebody please help?

Also, how do I find out if I am running 64 bit or 32 bit? Could this be my problem?

---

### Post by miniyak on 2009-05-26
im having this issue also. peoples faces show up blue, the colour green shows up purple ect. This happens universally across all played videos after installing the medibuntu extras

---

### Post by miniyak on 2009-05-26
my problem was solved by restarting... lol

---

### Post by Plasma_NZ on 2009-05-26
had this issue, fixed this issue by doing the following...

first i logged out - logged back in to check, still tinted blue with strange-hues...


opened terminal and ran

gstreamer-properties

then i went to 

"video" 

tab, then under "default output"
 i picked

Plugin - X Window System (No Xv)

closed gstreamer-properties, logged out - then back in and the problem was solved..

---

