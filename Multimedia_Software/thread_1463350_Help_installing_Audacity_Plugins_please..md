---
title: "Help installing Audacity Plugins please."
date: 2010-04-26
forum: Multimedia Software
---

### Post by philodice on 2010-04-26
[http://quitte.de/dsp/caps.html#Installation](http://quitte.de/dsp/caps.html#Installation)
I pasted this into my terminal after downloading.

The site says, Provided you run Linux, installation is simply: 

$ tar xvfz caps_0.4.4.tar.gz 
$ cd caps-0.4.4 
$ ./configure.py
$ make
$ su
# make install

However, it tells me command not found. What am I doing wrong?

Just need a little hint here.
I downloaded and uncompressed the tar file of plugins but now what?
If I am planning on having my next music player be Linux compatable, should I save my musical creations as Ogg vorbis files?

---

### Post by mc4man on 2010-04-26
> However, it tells me command not found. What am I doing wrong?
And what command might that be?

Just to mention - the $ and # are not part of the command

you might want to try this way

```
sudo apt-get install build-essential checkinstall
```
Then cd to the extracted caps-0.4.4 dir. in a terminal and at the prompt

```
./configure.py && make
```

Now either 
```
sudo make install
```

**or**

```
sudo checkinstall --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default
```

Checkinstall will make it easier to uninstall if need be

---

### Post by philodice on 2010-04-29
How do I Then cd to the extracted caps-0.4.4 dir. in a terminal?  Sorry, I would have asked in the beginner forum, but I got no answers there at all.

---

### Post by mc4man on 2010-04-29
> How do I Then cd to the extracted caps-0.4.4 dir. in a terminal

Well you'd open a terminal and type
cd /path/to/caps-0.4.4

So for instance if the caps-0.4.4 folder was sitting on the desktop this
```
cd ~/Desktop/caps-0.4.4
```
(~/ is another way to say /home/<your user name>

A simple way would be to open a terminal and type cd and then hit the space bar
Then drag the extracted caps-0.4.4 folder onto the terminal, click anywhere in the terminal to return focus and press enter on keyboard

Another easy way to open dir.'s in a terminal is to install 
```
sudo apt-get install nautilus-open-terminal
```

Then restart and you can right click on the folder -> open in terminal

---

### Post by philodice on 2010-04-30
Wow thanks that is really helpful.  I think I just did it.  I'm trying not to be a windows whiner, but sometimes I get stuck on all the stuff I'm reading and it doesn't make sense.  :)

I checked and it worked.  I have plugins!  My husband and I are in a unspoken contest of ,anything you can do in windows I can do in ubuntu for free, (except hardcore gaming and a couple things we don't do anyway).  He is being swayed to the free side.

---

