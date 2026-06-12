---
title: "Video Editing similar to Virtual Dub?"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by diablo75 on 2007-07-28
I'm trying to find an application that is easy to use and will allow me to edit video and cut and paste video using keyframe based selections.  Virtual Dub for the Windows environment works very much like this.  Are there any Linux alternatives that work?

---

### Post by ruibernardo on 2007-07-28
Try avidemux.

```
sudo apt-get install avidemux
```

It's very complete.

Cheers.

---

### Post by Drooling Iguana on 2007-07-31
I'm trying to do something similar to what the OP's asking about, and avidemux doesn't seem to do anything close to what I want. Basically I need a program that can easily cut out and arrange short clips from a long video file. Avidemux seems to be a decent program for converting files from one format to another, but unless I'm really missing something it doesn't seem to have any facilities for actual video editing.

If it does can someone please point me to a tutorial, and if not can someone please suggest a program that might actually do the job?

---

### Post by Scunizi on 2007-07-31
You should take a look at LiVes at [http://lives.sourceforge.net/](http://lives.sourceforge.net/)
There's also ...
[http://kdenlive.sourceforge.net/downloads.php](http://kdenlive.sourceforge.net/downloads.php) for the kde environment
[http://www.pitivi.org/wiki/Main_Page](http://www.pitivi.org/wiki/Main_Page) gnome environment
[http://freshmeat.net/projects/kino/](http://freshmeat.net/projects/kino/) available from the repos
[http://www.linux.com/articles/60624](http://www.linux.com/articles/60624)  info & helps
[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3) - it's the cats meow if you have horsepower in your pc. - takes getting use to.  If you like it consider installing Ubuntu Studio [http://ubuntustudio.net/](http://ubuntustudio.net/).  It has it in there by default.

---

### Post by Drooling Iguana on 2007-07-31
I tried Kino, but it was unable to import any of my video files (ordinary .avi files created with Mencoder using the lavc mpeg4 codec for video and LAME for audio.) I'll look in to Lives and Cinelerra.

---

### Post by diablo75 on 2007-08-03
I've had luck with avidemux so far.  I like it's interface.  It's very similar to virtual dub, but a little easier.  I've not had a lot of time to really test it out, but I like what I see so far.

---

### Post by Drooling Iguana on 2007-08-05
Well, Lives appears to theoretically capable of actually editing video, through the most awkward and convoluted process imaginable, requiring me to go through an insane number of steps every single time I want to add another clip to the finished movie.

PiTiVi, on the other hand, appears to do absolutely nothing at all. You can import video and audio "sources" into the program, but you can't actually *do* anything with them afterwards.

Cinelerra appears to never have been made into a .deb package, so I was saving it for last. Looks like I have no other choice, though.

---

### Post by Scunizi on 2007-08-06
If you're running Fiesty you might be able to find a deb for Cinerella at [www.ubuntustudio.net](www.ubuntustudio.net).  I tried to get there tonight but the site is having problems.. If you can get there give it a shot.

---

### Post by rosewater on 2007-08-06
Sorry.I find a lot of such softwares,but they just work on the windows platform.l

---

### Post by AnRa on 2007-08-06
> **Drooling Iguana said:**
> I'm trying to do something similar to what the OP's asking about, and avidemux doesn't seem to do anything close to what I want. Basically I need a program that can easily cut out and arrange short clips from a long video file. Avidemux seems to be a decent program for converting files from one format to another, but unless I'm really missing something it doesn't seem to have any facilities for actual video editing.

If it does can someone please point me to a tutorial, and if not can someone please suggest a program that might actually do the job?You have to set two marks (A and B), one in the start and the other at the end of the clip you want to make. Then save the video. ;)

---

### Post by Drooling Iguana on 2007-08-06
That's fine for cutting the clips out of the original video, but it doesn't seem to have any way of arranging them for the completed video.

---

### Post by Samhain13 on 2007-08-06
^Have you tried Cinelerra?
I found many sample videos in YouTube regarding it. I also use it myself sometimes.

---

### Post by AnRa on 2007-08-06
> **Drooling Iguana said:**
> That's fine for cutting the clips out of the original video, but it doesn't seem to have any way of arranging them for the completed video.File -> Append... or Ctrl+Alt+A ;)

---

### Post by User-007 on 2007-08-09
Hi!

Intall LIVES. I think it is exactly what you are searching for.

Download LIVES from [http://www.getdeb.net/app.php?name=lives](http://www.getdeb.net/app.php?name=lives)

Then run in terminal:

```

sudo apt-get install jackd ogmtools mkvtoolnix mjpegtools cdda2wav sox

```

And finally (replace /path/to with the target of your lives download)

```

sudo dpkg -i /path/to/lives_0.9.8.6-1~getdeb1_i386.deb

```

Then only type "lives" in the terminal or choose the icon in the menu, you will see the program opening.

User JB

---

### Post by mongoose_za on 2007-12-28
hey hope  this is right place to post..
I've not installed Avidemux yet but in advance i'm going to ask how to revolume a movie file. I used to just modify the streaming audio file seperate to the avi file using virtual dub and i was wondering how to do it with these (new to me) programmes. Cause it was a bit tricky in windows anyway.
Any tutorials or links or a few simple instructions would be great thanks.

---

