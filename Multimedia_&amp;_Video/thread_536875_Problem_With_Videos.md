---
title: "Problem With Videos"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by DocHolliday2006 on 2007-08-28
I've used EasyUbuntu to install all the video/sound codecs....almost everything from the entire program, actually. 

But my videos aren't playing.

When I click on a video, it says, "The file is encrypted and cannot be played"


I've got a bunch of different players installed, but none seem to work.

Any suggestions?

---

### Post by edward4130 on 2007-08-28
You most likely do not have everything, it is easiest to use apt-get to install the packages.  I personally use VLC for a player, it seems to handle everything and even the DVD menus. To install the libdvdcss2 thingamagig (tech term) use this code in terminal.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

then install the DVD package, for legal reasons they do not hand this out to you with Ubuntu.
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Now install VLC, it may work better for you.
```
sudo apt-get install vlc
```

that should cover it.

---

### Post by DocHolliday2006 on 2007-08-28
Should that fix my video/mp3 files as well as DVDs?

Also, are there any other general apt-get commands I should be aware of? Is there a list of good ones somewhere?

Thanks.

---

### Post by DocHolliday2006 on 2007-08-29
Bump

---

### Post by edward4130 on 2007-09-02
That should fix all of the stuff with DVD's as well as DivX XviD. As for the basic getting around in Linix CLI (command line interface) it never hurts to get a starter book.  There is a great one that is the official buntu book and it helped me out, they now have a second eddition.  

Help is always on here, and when you want to know what a command does, "man" it

```
man apt
```


"man is for Manual.  But don't try
```

man life
```
it doesn't work, thought I found the great shortcut....i think it would be a great joke to have it say "42" when you hit it.

Edward

---

