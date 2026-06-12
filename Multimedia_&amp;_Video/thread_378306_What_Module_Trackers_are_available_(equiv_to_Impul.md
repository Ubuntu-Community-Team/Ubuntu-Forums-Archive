---
title: "What Module Trackers are available? (equiv to Impulse Tracker)"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by Corvo78 on 2007-03-07
Back in the days (when being a young lad, hehe) I used to compose music using so-called 'module trackers'.
I used several Trackers back then, namely:[list][*]Fast Tracker *(.mod or .xm files)*[*]Scream Tracker *(.s3m files)*[*]Impulse Tracker *(.it files)*[/list]
But when I moved to Win2000/XP I found that running those DOS programs was just plain horrible.
And I just couldn't get used to (the few) Windows versions that are available.

So, obviously my question is:
**Are there any Module Trackers available for Ubuntu?** :confused: 
Who knows, I just might find one that actually is comfortable to use (as a former Impulse Tracker user).

_____

*For those who are wondering:*
Modules can be thought of as being MIDI files with embedded sounds (called samples).
Although Trackers don't use a 'classical music gui' (like MIDI composers) but something different (which is kinda hard for me to explain).

---

### Post by Corvo78 on 2007-03-08
I've done some searching and I found the following Trackers in the Ubuntu repositories (probably in Universe/Multiverse):
[list][*]Soundtracker *(for .xm and .xi files)*[*]Cheesetracker *(for .it .mod and .s3m files)*[*]Schism *(for .it .mod and .s3m files)*[/list]

Schism is an _exact_ replica of Impulse Tracker, which simply is a an 'ugly DOS' program that can be put into Full-screen.
Naturally, I like Schism the most.. I simply feel right at home! :KS 

I haven't played around much with the other two Trackers, though in my case only Cheesetracker could be a real alternative to Schism.

Although I'll keep looking for more Trackers...
...I'm happy quite happy, since my 'problem' is solved!



*EDIT:*:
Here's a link to Impulse Tracker's Wikipedia entry: _[http://en.wikipedia.org/wiki/Impulse_Tracker](http://en.wikipedia.org/wiki/Impulse_Tracker)_
Containing a good description of what these 'digital sound trackers' are and what clones of Impulse Tracker were made.

---

### Post by rs3 on 2007-05-24
i'm not sure if rigelseven keeps a link to the latest builds of schism, but if he doesn't, [http://www.nimh.org/schism](http://www.nimh.org/schism) :D  have fun!

---

### Post by Corvo78 on 2007-06-04
Thanks for the info!  :popcorn:

---

### Post by esaruoho on 2007-12-28
> **rs3 said:**
> i'm not sure if rigelseven keeps a link to the latest builds of schism, but if he doesn't, [http://www.nimh.org/schism](http://www.nimh.org/schism) :D  have fun!

i've got their latest build, but am a total numpty in the installation of it. no amount of "read this or that file" will help. i just hope to get it running on a ubuntu installation that i'm  on.
im pretty desperate:/

---

### Post by vvoois on 2007-12-28
You can download milkytracker if you desire a Fasttracker variant.
There are not a lot of trackers that do native Impulse Tracker though.
But you can install DosBox (which also has a Linux edition) and then run the original Impulse Tracker natively if you can't say goodbye to it.
I personally stepped over to Renoise almost 5 years ago and Renoise will release a Linux binary somewhere early Q1 2008. (Currently i'm already testing alpha's which work pretty fine actually)

---

### Post by rs3 on 2007-12-28
> **esaruoho said:**
> i've got their latest build, but am a total numpty in the installation of it. no amount of "read this or that file" will help. i just hope to get it running on a ubuntu installation that i'm  on.
im pretty desperate:/

If you want to get the latest build working, I suggest opening a terminal and beginning with the following command:

```
$ sudo apt-get build-dep schism
```

This will satisfy build dependencies for compiling schism.  Then, after extracting [cvs-snapshot.tgz]("http://www.nimh.org/schism/cvs-snapshot.tgz"), it's a few simple commands:

```
$ ./configure
$ make
$ sudo make install
```

If it dies during the configure process, post the error message that results so we can figure out what dependencies require further satisfaction.

If you're running a 32-bit system, though, you could also get the latest schism by using the [autopackage]("http://www.nimh.org/schism/schism-0.5.x86.package") and executing the following from the directory in which it was downloaded:

```
$ sh ./schism-0.5.x86.package
```

This might be easier for you.  I recommend using the autopackage without sudo, and you can click "No Password" if it prompts you for one--this will install schism to your home directory and add links to your Sound & Video submenu in Gnome.

Hope that helps!

---

### Post by rs3 on 2007-12-28
> **vvoois said:**
> You can download milkytracker if you desire a Fasttracker variant.
There are not a lot of trackers that do native Impulse Tracker though.
But you can install DosBox (which also has a Linux edition) and then run the original Impulse Tracker natively if you can't say goodbye to it.
I personally stepped over to Renoise almost 5 years ago and Renoise will release a Linux binary somewhere early Q1 2008. (Currently i'm already testing alpha's which work pretty fine actually)

That's great news!  I haven't paid much attention to Renoise, though I paid for a license as I was pretty impressed with it.  Ideologically, I don't much care for Renoise (closed-source and all that) but it is a very technically solid next-generation tracker, and I'd definitely give it another shot in Ubuntu.  Thanks for pointing that out! :D

---

### Post by conner_bw on 2008-01-18
Renoise for Linux (beta) was released to registered users yesterday. A public demo should be available in a few weeks.

More info:
[http://www.renoise.com/indepth/renoise-news/renoise-191-beta-with-linux-port/](http://www.renoise.com/indepth/renoise-news/renoise-191-beta-with-linux-port/)

Screenshots:
[http://www.renoise.com/board/index.php?showtopic=15243](http://www.renoise.com/board/index.php?showtopic=15243)

Good times!

---

