---
title: "Flash Editor for Ubuntu?"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by acidblue on 2007-05-06
Is there a good flash editor for Ubuntu?
I have a few '.flv' files that i want to edit and splice together
to make one single 'flv' file.
Tried kino but that is for DV files, flv types won't load.
Search in synaptic didn't really see anything but kino.

Using Fiesty 7.04

---

### Post by TURNER on 2007-05-08
Hi, 

I've also been looking for a replacement to Macromedia Flash Editor, a couple which I've managed to find so far are:

synfig 
Ktoon
Blender

granted the last 2 are aimed at cartoon creation, but as far as my limited knowledge go, they will produce swf output.

synfig IS basically Flash, however the project isn't well supported at this time, and it seems close to going under. another project was/is

F4L (flash for linux) which merged and is now called uira, try google for details, however it does seem to have dried up!!

if you find any more, i'd love to know about it!

---

### Post by snoop on 2007-05-08
Synfig and ktoon are indeed for flash, but blender is a 3d modeler (it may be able to output swf, not sure about that).

The last time I tried synfig (to be honest it was a year or so ago), I tried to compile from source and it totally borked my machine. YMMV

To just slice some flv files, I would suggest using ffmpeg to convert it to mpeg and then using something like kino and then trying to reencode it to flash.

---

### Post by TURNER on 2007-05-08
Synfig is now in the repositories mate, I downloaded it last night. Looks cool, but from what I read there isn't alot of support for the project, shame really......

Have you had any experience with Ktoon, can it be used as a replacement for Flash?

---

### Post by snoop on 2007-05-08
> **TURNER said:**
> Synfig is now in the repositories mate, I downloaded it last night. Looks cool, but from what I read there isn't alot of support for the project, shame really......

Have you had any experience with Ktoon, can it be used as a replacement for Flash?

So it is. But running synfig doesnt give me any graphical interface, it just prints out its default commands. I have not used ktoon yet, I dont know they have an experimental package for ubuntu 6.06, but nothing after that.

Sadly, most of these projects seems to be down to nothing.

---

### Post by TURNER on 2007-05-08
> But running synfig doesnt give me any graphical interface,

I made the same mistake last night, search again in your package manager, and install the other synfig files, one of them is the GUI.


> Sadly, most of these projects seems to be down to nothing.

It seems that way, and it saddens me to acknowledge it, I am no programmer myself, and to be honest I wouldn't even know where to start...but I cannot see the point in starting something you have no intention of finishing, synfig looks really promising, and so does f4l/uira, if only everyone could join forces and really produce  a flash alternative for linux!

---

### Post by ccoppenbarger on 2007-05-08
Try ffmpeg for splicing the videos together. It has the documentation on sourceforge I believe.
[http://flowplayer.sourceforge.net](http://flowplayer.sourceforge.net) has information on this as well. 
FLVtools might work as well. These are command line tools, but check them out.

ffmpeg is in the repositories. flvtools is not.

---

### Post by acidblue on 2007-05-08
Ok i can covert the flv files to mpeg with ffmpeg.
but how do i splice thm together?
Looked at the docs on the ffmpeg website didn't
see anything about splicing.

---

### Post by snoop on 2007-05-09
You can use avidemux to splice them together.

---

### Post by FRuMMaGe on 2007-05-09
> **acidblue said:**
> Is there a good flash editor for Ubuntu?
I have a few '.flv' files that i want to edit and splice together
to make one single 'flv' file.
Tried kino but that is for DV files, flv types won't load.
Search in synaptic didn't really see anything but kino.

Using Fiesty 7.04

No need for a Ubuntu flash editor, as Macromedia Flash works great under Wine

---

### Post by acidblue on 2007-05-09
Ok I'm totally lost. 
No where on the ffmpeg or avidemux websites or docs
does it tell you how to splice files together
If i could get a little help here or pointed in the right direction 
that would be greatly appreciated.

---

### Post by Tim P on 2007-05-14
> **FRuMMaGe said:**
> No need for a Ubuntu flash editor, as Macromedia Flash works great under Wine

And all you need is $700 to purchase it... Yes there is a need for a flash editor that works in Ubuntu!  Unless you would like to buy us all a copy, I feel sure we could get you a list names and addresses to ship the CD's to.

---

### Post by FRuMMaGe on 2007-05-15
I stole mine from my school :)

---

### Post by daverich on 2007-05-17
I just mailed coffeecup and asked whether they'd be porting their firestarter flash editor to linux.

Seems to be a much better bet - I suggest everyone who would like a flash editor for linux does the same.

[www.coffeecup.com](www.coffeecup.com)

Kind regards

Dave Rich

---

### Post by IceDragonkin on 2007-05-23
> **FRuMMaGe said:**
> No need for a Ubuntu flash editor, as Macromedia Flash works great under Wine

Ok i have Macromedia 8 so whats wine? does it allow me to run macromedia on linux?

---

### Post by FRuMMaGe on 2007-05-23
> **IceDragonkin said:**
> Ok i have Macromedia 8 so whats wine? does it allow me to run macromedia on linux?

wine is a windows emulator that lets you run windows programs with linux.  Go to the synaptic package manager and search for wine, or just open the terminal and type:

```
sudo apt-get install wine
```

---

### Post by blueraven on 2007-05-24
**w**ine **i**s **n**ot an **e**mulator. Wine is a compatability layer that allows Windows applications to run in Linux.

---

### Post by EdUbun on 2007-06-06
How about f4l?
[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

---

### Post by liviubero on 2007-09-11
How do I install Flash and Dreamweaver in wine?
Let's say I have the installers... what next?
Could there be any video card issues?

---

### Post by FRuMMaGe on 2007-09-11
first check out winehq.

Dreamweaver:
[http://appdb.winehq.org/appview.php?iAppId=183]("http://appdb.winehq.org/appview.php?iAppId=183")

Flash:
[http://appdb.winehq.org/appview.php?iAppId=23]("http://appdb.winehq.org/appview.php?iAppId=23")

---

