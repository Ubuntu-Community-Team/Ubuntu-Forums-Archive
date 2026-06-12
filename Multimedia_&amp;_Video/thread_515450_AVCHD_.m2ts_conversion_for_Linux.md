---
title: "AVCHD .m2ts conversion for Linux"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by ethos101 on 2007-08-02
So I'm trying to run [_this_]("http://www.avsforum.com/avs-vb/showthread.php?t=789775") (<-link) install script because obviously I need to convert some .mts HD videos from my camcorder.

I get this message:  /bin/csh: bad interpreter: Permission denied

I'm a bit of a noob when it comes to installing source.  I even try it as SU (sudo su).  I'm sure it's something completely simple that I don't know yet.

As you can see [_here_]("http://www.avsforum.com/avs-vb/showthread.php?p=11175049&&#post11175049") (<-link) nobody has given me an answer on that forum yet...

Is this script compatible with Ubuntu?  I'm on a nearly fresh install right now.

---

### Post by ethos101 on 2007-08-09
Just an update.  I found help on another forum and he fixed me up.  Here is the link in case anybody stumbles across this post looking for the same thing.

[http://www.highdefforum.com/showthread.php?t=47653](http://www.highdefforum.com/showthread.php?t=47653)

---

### Post by citybird on 2007-12-20
ok i used 
> aptitude install mplayer ffmpeg x264 faad2 faac a52dec mencoder
to install the programs.

now how do i install the scripts without running the full install?

---

### Post by wesleybailey on 2008-01-30
Once you have downloaded the neccessary packages (i.e mplayer ffmpeg x264 faad2 faac a52dec mencoder)

You then need to run the modify the download script file, and then run the install script.

I have created a tutorial [here]("http://wesleybailey.com/blog/2008/01/20/m2tstoavi-avchd/") that steps you through the process.

Hope this helps.

---

### Post by tribunal on 2008-03-29
Your tutorial works fine, thank you, but with my Sony SR5E I have no sound after converting :(
Now I know the source of the problem:
format 0x56444152
Cannot find codec 'dvaudio' in libavcodec
win32codecs are installed...

---

