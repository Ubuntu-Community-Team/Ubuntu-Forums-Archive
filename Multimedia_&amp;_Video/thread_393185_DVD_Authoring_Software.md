---
title: "DVD Authoring Software"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by Razenoth on 2007-03-25
Hey everyone, so I have been looking for awhile now and am unable to find a piece of software in that will fit my needs. Basically what I have is a bunch of .avi movies that I have made and I want to be able to burn them onto a DVD so that I can put them in my DVD player at home and have them play. So if anyone knows of a good program to do this I would greatly appreciate it.

---

### Post by fenian on 2007-03-25
You may want to try [DeVeDe]("http://www.rastersoft.com/programas/devede.html")  to install it...

> sudo apt-get install devede

---

### Post by reclusivemonkey on 2007-03-26
DeVeDe isn't great, I tried it this weekend, it almost made the DVD but then just hung. This is one area which Ubuntu doesn't have anything that works for me personally. I hear people get good results with tovid, but its not a GUI and I don't have time to learn the commands ATM.

---

### Post by mrthundercleese4 on 2008-01-23
Yes I too could use some DVD software for my avi files. Don't need to edit the video jsut want an app that takes the avi's converts them and burns them and dvd menu software would be nice too.

---

### Post by ron999 on 2008-01-23
Hi
I use 'tovid'.
It's all command line, but you have to go about it methodically.

First use 'tovid' to convert the file into the correct format.
Next use 'makexml' to make a (kind of) cue sheet.
Then use 'makedvd' to create the file structure.
Last use K3b or similar to burn the disc.

Tovid lets you create menus too, but I found I needed to practice making single file DVDs first.

This is where to read about tovid, and there's screenshots. Here:-[http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")
:cool:

---

### Post by sandr- on 2008-01-23
You can install dvdshrink under wine to enjoy its capabilities.

---

### Post by dannyboy79 on 2008-01-23
tovid also has a gui. that's what i use. and I must say, i've used it a lot for my friend. he gave me all seasons of South park as avi files, then I just add some to the tovidgui, change some settings, tell it to encode them, then tell it to burn them. All is well! I had a few that the sound got out of sync but that normally happens when I try to fit to many avi's onto one dvd.

I have also used Devede, it's not bad either.

---

### Post by dannyboy79 on 2008-01-23
> **ron999 said:**
> Hi 
nice avitar! that guy is one sick motha. I especially like his cattle-killa-compressor-punch! Didn't like the ending of the movie though.

---

### Post by ron999 on 2008-01-23
> **dannyboy79 said:**
> nice avitar! that guy is one sick matha. 
LOL He's gonna win an oscar maybe:lolflag:

---

### Post by dphirschler on 2008-01-23
This is so weird to me because I remember when there weren't any free alternatives to the paywares on the Windows platform for DVD authoring.  That is until somebody ported over a tool from the Linux world simply called "DVD Author".  I use that tool in Windows.  I've never tried to go back and try it on Linux.  There are several Windows GUIs written for DVD Author.  I have no idea if one exists in Linux, but I would imagine one does.


Darryl

---

