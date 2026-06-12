---
title: "How do I install codecs not available in repositories?"
date: 2008-12-07
forum: Multimedia Software
---

### Post by technoshaun on 2008-12-07
I bought one of those cheapie Chinese MP3 players that use the .mtv format. They included the codecs but I need to know how to install them in Intrepid Ibex so I can do file conversions. Yes I know incredibly small screen etc. but the price was $20 at a clearance sale. Its no iPod but its a nice little device for what I paid and it has a 10GB capacity with a micro-SD card. Not to shabby and I would like to copy some videos over to it to watch when I am away from home.

I have the codecs (.dll files) and I want to see if I can get Ubuntu to use them (hoping it can) better yet if anyone knows where I can get .mtv codecs for Linux that would be better, but not holding my breath.

Anyway the /usr/local/libs/codecs directory is not there so in a nutshell I need to know where Intrepid puts codecs.

Shaun

---

### Post by gandaran on 2008-12-07
> **technoshaun said:**
> I bought one of those cheapie Chinese MP3 players that use the .mtv format. They included the codecs but I need to know how to install them in Intrepid Ibex so I can do file conversions. Yes I know incredibly small screen etc. but the price was $20 at a clearance sale. Its no iPod but its a nice little device for what I paid and it has a 10GB capacity with a micro-SD card. Not to shabby and I would like to copy some videos over to it to watch when I am away from home.

I have the codecs (.dll files) and I want to see if I can get Ubuntu to use them (hoping it can) better yet if anyone knows where I can get .mtv codecs for Linux that would be better, but not holding my breath.

Anyway the /usr/local/libs/codecs directory is not there so in a nutshell I need to know where Intrepid puts codecs.

Shaun
these .dll files (windows codecs) you can install from the repositories, just add the medibuntu repository [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and then install the w32codecs package, you'll need a player that can use these codecs, install mplayer or any xine player and gstreamer0-10 pitfdll for gstreamer based players can use use some of those codecs

---

### Post by technoshaun on 2008-12-07
The codecs I have are not in that package. these are .mtv codecs that are not available in the repositories. So I have to put them in the correct directory by hand. (Please read original post carefully) the codecs I am trying to install are not, and most likely never will be, in the win32codecs package which I have already installed.

--Shaun

---

### Post by gandaran on 2008-12-07
> **technoshaun said:**
> The codecs I have are not in that package. these are .mtv codecs that are not available in the repositories. So I have to put them in the correct directory by hand. (Please read original post carefully) the codecs I am trying to install are not, and most likely never will be, in the win32codecs package which I have already installed.

--Shaun
okay then, try droping them in /usr/lib/win32, that's where .dll's go to
or install them anywhere you like, just make sure you favourite player can find them

---

