---
title: "Audacious 1.4.5 installation on gusty with media library"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by banda on 2008-01-28
hey audacious 1.4.5 was released recently, i had a few problems compiling it from source (they don't give deb packages). 
after sorting out a few dependencies it worked like a charm.

i use audacious with a media library called methlab which runs seprately from audacious but works pretty well.



a screenshot of methlab and audacious(click to enlarge)-
[[IMG]http://img134.imageshack.us/img134/3217/screenshotca4ax0.jpg[/IMG]](http://img509.imageshack.us/img509/7026/screenshotca4.jpg)

heres a short how -to to install audacious 1.4.5 with methlab media library

just copy paste each line in terminal..

> sudo apt-get update && sudo apt-get upgrade

sudo apt-get install build-essential mercurial autogen automake checkinstall

sudo apt-get install libgtk2.0-dev libpng12-dev libglade2-dev libdbus-glib-1-dev libmcs-dev bison libxml2-dev libxcomposite-dev imlib11-dev

sudo apt-get install libsamplerate0-dev libsidplay1-dev libsidplay2-dev libflac-dev libmad0-dev libvorbis-dev libasound2-dev libesd0-dev libpulse-dev libsndfile1-dev libmpcdec-dev liblame-dev gettext libpango1.0-dev

wget [http://distfiles.atheme.org/libmowgli-0.6.0.tgz](http://distfiles.atheme.org/libmowgli-0.6.0.tgz)
tar xvvzf libmowgli-0.6.0.tgz
cd libmowgli-0.6.0
./configure
make
sudo checkinstall


now download audacious and audacious plugins from 
[http://distfiles.atheme.org/audacious-1.4.5.tgz]("http://distfiles.atheme.org/audacious-1.4.5.tgz") &
[http://distfiles.atheme.org/audacious-plugins-1.4.4.tgz]("http://distfiles.atheme.org/audacious-plugins-1.4.4.tgz") (plugins are not optional, audacious needs them to work)

extract them in seprate folders


> cd audacious-1.4.5
./configure --enable-samplerate --enable-chardet
make
sudo checkinstall
cd src/libaudclient
sudo cp -r libaudclient.so /usr/lib/libaudclient.so.1

> cd audacious-plugins-1.4.4
cd
./configure
make
sudo checkinstall


audacious is now installed, 
to install methlab media library ... 


> sudo aptitude install python2.5 python-ctypes python-tagpy libboost-python1.34.1 python-gtk subversion

svn co [http://methlab.thegraveyard.org/svn/trunk](http://methlab.thegraveyard.org/svn/trunk) methlab
cd methlab
./methlab

methlab is also installed now.


to have both audacious and methlab open simultaneously with a single icon, do the following...

go to your home folder and create a file called 'audacious_methlab'(or whatever)
, paste the following in it and save 
> #!/bin/sh

audacious&
/home/name/methlab/methlab&
(replace 'name' with your username)

right-click the file and in permissions allow it to execute as a program

go to your desktop and create a launcher for '/home/name/audacious_methlab'

give the launcher an icon of your choice then launch it
if everythin went ok then you will have audacious and methlab running now 

in methlab 
under settings choose the audio player as audacious(DBus) & add your music directories
make 'enque' the default action
also tick 'start hidden' if you like
**done!**

now go load up audacious's playlist and enable the plugins you like... (i think the global hotkey one is pretty good) 
and get the skins from [here]("http://browse.deviantart.com/?catpath=customization/skins/media/winamp/classic/&order=9&alltime=yes&offset=48") (put them in /home/name/.local/share/audacious/Skins)

**credit to orignal authors**-- most of this i got from [here]("http://ubuntuforums.org/showthread.php?t=395599") & [here]("http://boards.nenolod.net/viewtopic.php?f=8&t=928&p=3072#p3072")

---

### Post by santaslittlehelper on 2008-01-28
Hi 

Nice howto.

I had a small issue, I got the error -
```
audacious: error while loading shared libraries: libmowgli.so.1: cannot open shared object file: No such file or directory
```
and had to 
```
ln -s /usr/local/lib/libmowgli.so.1 /usr/lib/libmowgli.so.1
```
to get it working.

Maybe configure libmowgli with ./configure --prefix=/usr instead would avoid this? 
This could just be something related to my install was just wondering. 

Anyway thanks, was thinking about getting this done for some time.

ps
In audacious-plugins-1.4.4 checkinstall is missing an l

---

### Post by banda on 2008-01-28
thanks for the pointing out the typo .. fixed it

i think it worked for me with ./configure only. i will wait for some1 else to confirm the error and then make the changes if necessary

---

### Post by disturbedite on 2008-01-28
heh, you said they don't release deb packages.  but audacious is in the ubuntu repo!
there isn't any reason to compile it.  (unless you want 1.4.5 and aren't on hardy.  cuz hardy has audacious 1.4.5).

---

### Post by banda on 2008-01-28
ah.. i do know audacious is in the repo, but, i wanted to try out 1.4.5.
also i am a beginner with this ubuntu stuff, so i don't miss a chance to compile a software myself.. 
say just for the sake of a learning experience if nothing else :)

---

### Post by doug1212 on 2008-01-28
Hi,
I am using audacious 1.4.5 from morgoth's gutsy repo.
[http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/)
Doug.

---

### Post by banda on 2008-01-28
guess i should have checked backports too:oops:

---

### Post by santaslittlehelper on 2008-01-28
Hi

> **disturbedite said:**
> heh, you said they don't release deb packages.  but audacious is in the ubuntu repo!
there isn't any reason to compile it.  (unless you want 1.4.5 and aren't on hardy.  cuz hardy has audacious 1.4.5).
lol why would he be on hardy?

> **banda said:**
> guess i should have checked backports too:oops:
Sure but you are allowed to compile something if you want to :D

---

### Post by disturbedite on 2008-01-29
> **banda said:**
> ah.. i do know audacious is in the repo, but, i wanted to try out 1.4.5.
also i am a beginner with this ubuntu stuff, so i don't miss a chance to compile a software myself.. 
say just for the sake of a learning experience if nothing else :)
thats great.  i wish more ppl had that attitude.  most ppl have the opposite attitude.

---

### Post by disturbedite on 2008-01-29
> **santaslittlehelper said:**
> Hi
lol why would he be on hardy?
why not?  ppl *do* test pre-releases...


[QUOTE=santaslittlehelper]Sure but you are allowed to compile something if you want to :D[/QUOTE]
i never said he wasn't.  actually, it makes for good practice if one is inexperienced...

---

### Post by santaslittlehelper on 2008-01-29
> **disturbedite said:**
> why not?  ppl *do* test pre-releases...



i never said he wasn't.  actually, it makes for good practice if one is inexperienced...
I am in complete agreement. :)

---

### Post by Nitroadict on 2008-02-24
Well, Audacious installed alright, but it doesn't play a damn thing i put in the playlist :\.  The plugins somehow didn't install at all, and I'm still not quite sure why (I am noob to these ubuntus, I apologize).

Eventually I kind of gave up and went into synaptic for the older version of audacity (making sure the uninstall the previous stuff with synaptic and installing anything the older version required).  


Sadly, it doesn't end there: the old version, while allowing me to see that indeed, the plugins are there, refuses to play and keeps giving me error (which entails: check to see if another program is blocking the soundcad, etc. etc.)

***** EDIT **** Nevermind, it was a simple matter of just telling audacious what sound card and hardware to recognize (I had the sudden common sense to see why amarok was working...)

---

### Post by Jose Catre-Vandis on 2008-02-24
Methlab works fine, just takes an age (@ 5 minutes) to start up (loading up 35,000 tracks on a network server!)

ahh, just found the "update library on startup checkbox!  :)

---

### Post by xvistafan on 2008-07-05
THanks a lot ! I installed audacious from the repo but Methlab library from ur how-to...this is just what I was looking for.No more wine+winamp for me :D

---

