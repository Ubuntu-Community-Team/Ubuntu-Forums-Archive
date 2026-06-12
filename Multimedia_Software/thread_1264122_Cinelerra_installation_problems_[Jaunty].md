---
title: "Cinelerra installation problems [Jaunty]"
date: 2009-09-11
forum: Multimedia Software
---

### Post by smilesfozwood on 2009-09-11
Hi, I'm running Jaunty Jackalope, and I can't get Cinelerra to install. 

First I installed this: **[http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb)** which I guess is a repository. I'm not too familiar with all the lingo.

Then I added **deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main** into the Synaptic Package Manager/Settings/Repositories/Third Party Software, gone back the the main screen, hit reload, then mark for installation on **cinelerracv**. Then it said

"The following packages have unresolvable dependencies. Make sure that all repositories are added and enabled in the preferences."

followed by:

"cinelerracv:
 Depends: libfaac0 (>=1.26) but it is not installable
 Depends: libmjpegtools-1.9 (>=1:1.9.0) but it is not installable
 Depends: libmp3lame0 (>=3.98) but it is not installable
 Depends: libquicktimecv but it is not going to be installed
 Depends: libx264-65 (>=1:0.svn20081230) but it is not installable"

What am I doing wrong? I've tried many different ways to do this, searched the forums, and I just can't get it to work...

---

### Post by Bucky Ball on 2009-09-11
Did you also install the GPG key? I am not on my studio box at the mo to give it to you but that could be your problem. Run update perhaps (from update manager).

---

### Post by AlexanderDGreat on 2009-09-12
Same here, but in my case, I can't see cinelerra anywhere in the repositories.

1. I already typed

wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
or
echo deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update

2. Installed [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb)

3. Restarted, reloaded, Synaptics and Update Manager, Used Main Server and Server USA, looked it up in synaptic typing "cine" or in Add/Remove Programs

Any ideas?

---

### Post by smilesfozwood on 2009-09-12
Okay, I ran Update Manager, but still nothing. How would I get the GPG key? I don't really understand what that is, even after googling and wikiing it.

Also in the Cinelerra manual it says that these must all be installed:

    *  a52dec
    * dv
    * faac
    * ffmpeg
    * fftw
    * lame
    * libavc1394
    * libfaad2
    * libraw1394
    * mjpegtools
    * OpenEXR
    * theora
    * x264 

How would I go about checking to see if I have these? 

By the way, I'm running Jaunty off of a usb stick, if that matters.

---

### Post by smilesfozwood on 2009-09-13
FINALLY! I got it to install. I actually had to reinstall ubuntu to solve a different problem, and this time cinelerra installed right away. yay

---

### Post by eyeyoubin on 2009-09-14
for your problem alexanderDgreat, here is the solution
1. go to your synaptic package manager
2. click origin on bottom-left corner
3. select akirad.cinelerra.org/main
4. install cinelerracv

hope this works for you as well.

---

### Post by Bucky Ball on 2009-09-14
Problem already solved if you read the post above yours. :)

Smilesfozwood, I've heard the 'solved' function is back in the 'thread tools' drop down menu.

---

### Post by smilesfozwood on 2009-09-14
> Smilesfozwood, I've heard the 'solved' function is back in the 'thread tools' drop down menu.

Yeah, I know. I've already done that.:razz:

---

### Post by AlexanderDGreat on 2009-09-14
Hi, finally found cinelerra in the repositories.

What could be the reason after I've tried all the instructions in the cinelerra website, it still didn't appear in the repositories, only after a dozen reboots, waiting for days, or not using my computer for a long time, that it did appear.

You just type cine and all options are there.

Also, I didn't even need eyeyoubin's advice to go to Synaptics, click "Origin" -> akirad.cinelerra.org/main because this morning it just appeared in the Synaptics.

The truth is out there. =)

---

### Post by Bucky Ball on 2009-09-15
Yea, Cinelerra is not actually an 'official' Ubuntu app (that's why it is not in the repos and you need to add it) so you use at your own risk and get whatever info you can from other users or the Cinelerra devs themselves.

You will probably notice they say something along the lines of 'We take no responsibility ... etc.' In other words, it changes, bugs resolve and occur. If you have added the akirad repo to your software sources and updated lately, that could be what caused the change. A recent Akirad update. :)

---

### Post by MisFitt on 2009-11-29
> **eyeyoubin said:**
> for your problem alexanderDgreat, here is the solution
1. go to your synaptic package manager
2. click origin on bottom-left corner
3. select akirad.cinelerra.org/main
4. install cinelerracv

hope this works for you as well.
Thanyou,it worked beautifully and EASY for me and now I have cinelerra!

---

