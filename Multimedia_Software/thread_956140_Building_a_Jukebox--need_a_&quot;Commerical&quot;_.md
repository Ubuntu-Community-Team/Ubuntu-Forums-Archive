---
title: "Building a Jukebox--need a &quot;Commerical&quot; style program"
date: 2008-10-22
forum: Multimedia Software
---

### Post by jukingeo on 2008-10-22
Hello all,

I know that this topic on having a jukebox program in a computer has been beaten to death here, but my application is a bit different.

What I am looking for is a very simple interface (perhaps a touch screen), in which images of good old fashioned jukebox title strips would be shown on the screen.  There would be nice large forward/reverse scroll buttons to "flip" through "pages" of title strips.  Then when the desired song is viewed, all one has to do is touch the selection.  The computer will then play the appropriate song.

Simple and sweet...however, like a real mechanical jukebox, I would like the selections to "cue".  Thus when someone comes along and the jukebox is already playing, the next selection made will be put "in line" and so on and so on.

I have seen many of the programs mentioned here, and they are not going to cut it.  Most are just boring looking lists or are too complex for the average "joe" to use.

If possible I would even like this to work off of a coin mech.  My intention is to build a Wurlitzer style round top cabinet (complete with lighted plastics and bubble tubes) and have the touch screen in the middle.  From afar it would look like a lighted title strip display.

I don't intend to play videos or show pictures, however, I did think about having the display change to a random pattern that goes with the music (kind of like what many media players do) and when some approaches the machine and touches the screen, it goes right to the title strips.

As for the title strips themselves, I am leaning more towards the older style strips, but I am a bit flexible.  I do want the selections to be a decent size so that no mistake can be made (i.e. touch selections too close together).

Outside of using a touch screen (considering they are much more expensive than regular LCD monitors).  I have also thought of using a standard number keypad in which the song title would be shown on screen with a number and someone just punches the number in.

I would like the system to boot up in the background when turned on.  I don't want it to look like a computer program, but a custom program.  In other words after the operating system loads up, the program launches into the jukebox program.

So, is there something out there in Linux-land that can do this?

Edit:

Something like this is acceptable:

[http://www.youtube.com/watch?v=8cL5vAD_Fmw](http://www.youtube.com/watch?v=8cL5vAD_Fmw)



Thanx,

Geo

---

### Post by jukingeo on 2008-10-23
Anyone have any ideas as to what is out there? 

I don't want anything that looks like Rhythmbox.  That is too "Computery", I would like something that you would find on a commercial machine. (see my link above.)

Edit:

OK, everyone.  I DID find a really cool jukebox program called DWJukebox.  It is meant for Windows XP or Dos:

[http://www.dwjukebox.com/](http://www.dwjukebox.com/)

DWjukebox is by FAR better than any jukebox media player that I seen that runs in native Linux.  The program literally changes your machine into a jukebox with title strips and all.  It can be set to take coins and the best part is that you can program buttons to a USB game controller, which you can hack and use "arcade" type buttons (or a number pad) to work the jukebox.

This is EXACTLY what I wanted and what I was looking for.  However, there isn't a version for Linux.  But I did notice that there is a DOS version.  I been running my old DOS computer games in Linux for a while now using a program called DOSBOX.  I am wondering if this program would work in that. For now I am using it in Windows XP and having a BALL of a time with it.

Geo

---

### Post by jukingeo on 2008-11-25
Update:

I have been doing some tests with DWJukebox with Wine and Linux.  It DOES WORK!  However, in Ubuntu, the program runs very slow and has trouble with the animations.  If you turn them off and use a low resolution skin, it will work fine.   However, I have discovered that using a much faster operating system such as Puppy Linux, will have much better results.

The program is constantly being updated and presently the author is attempting to remove any potential bottlenecks and it should prove to run faster in the future.  Who knows?  He is also thinking about making a Linux version.

I do have to add that this machine was my benchmark:

Dell Dimension 4600
Pentium 4 2.8ghz
2.0gig ram
SATA hard drives
256meg video card.

I seriously do not recommend using a machine with specs much less than this to use DWJukebox with Wine & Puppy Linux.   With a Core Duo machine, you should be able to run it in Ubuntu, but I would recommend Xubuntu instead.

Program Website:

[www.dwjukebox.com](www.dwjukebox.com)

---

