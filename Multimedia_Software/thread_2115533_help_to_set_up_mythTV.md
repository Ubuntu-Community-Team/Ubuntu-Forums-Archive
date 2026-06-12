---
title: "help to set up mythTV"
date: 2013-02-13
forum: Multimedia Software
---

### Post by christia on 2013-02-13
So, I'm buying a new machine to act as a home entertainment system. I want to partially be able to use the computer for some light internet browsing but mainly to watch videos and/or tv shows.

I also have a cable tv package (I live in Hong Kong, so not a standard US cable setup), and wouldnt mind being able to combine this with my machine.

I've read about MythTV, but still really trying to understand what it is. When I try to read about it, I can only find really complicated sites.

So, can anyone help me answer these beginners questions or help point me towards a guide that can (i have searched around almost 2 hours now w no luck)?

a) If I use ubuntu 12.10 and then install mythtv, does my computer then function like it would had i not installed mythtv, and then when i open mythtv i now have a "tivo" like program running? or does mythtv "take over" control and make my computer "only" a mediacenter?
b) what is needed to set this up? I.e., what do i need to connect to what? can i just connect my machine to my TV using a HDMI cable and then i can use mythtv using my TVs remote? or do i need to do more connecting? 
c) same as b), but about my cable tv - how do i get this to be "in" mythtv, so that i can browse around the channels in mythtv just like i would with my downloaded files? 
d) once (or, IF) i manage to set up the above, then i can use a keyboard or the remote to control the stuff - can i also install something on my phone (samsung galaxy S3 lte, so far no ubuntu stuff installed on it)

thanks
Christian

---

### Post by ceejay on 2013-02-13
MythTV is a bit of a monster - very powerful, but hard to get to grips with and set up. If you go down this route, be prepared to spend at least a couple of weeks fiddling. When you're done, you might have something very good.

Try the "mythbuntu" board within these forums - you will find discussion of MythTV generally there, not just the specific Mythbuntu distro (which is basically Ubuntu with MythTV preinstalled.

The first thing to grasp with MythTV is that there is a backend component (which has the tuners and manages recordings) and a front end component (which is what you actually use to watch those recordings). Both components can happily live on one computer, though they are often separated. The front end displays on your TV using HDMI or whatever.

If you install MythTV front end on Ubuntu, its just another program. You choose whether you want it to run on start up or not.

In principle you can use a remote to control this, assuming you have something like a USB IR receiver. It can be a bit fiddly to get right.

If you want to watch a lot of videos, you might also want to look into XBMC which does that a whole lot more slickly than MythTV does - and which, from the latest version (12) will also act as a MythTV front end for good measure.

---

### Post by christia on 2013-02-13
Thank you, I also felt like it was a bit of a beast. 

As I will mainly be watching downloaded movies or shows, and not really do much recording, it seems as if xbmc is an easier option that can achieve just that 

Before I look into that in more detail, is my understanding correct that xbmc mainly acts as a mediacenter, ie a program that collects all my music and video? and not much installation is needed, ie I can just get from Ubuntu software center and then tell the program where my files are (or will it be smart and find it itself, if so, what about external drives that are only connected sometimes? )

one thing I hated w windows media center was it didn't swallow all file types like vlc did, will xbmc have that problem too?

---

### Post by ceejay on 2013-02-14
XBMC is pretty easy to set up. You can tweak with it a lot if you want to, but you really don't have to do that, in my experience it works more or less out of the box.

You have the chance to tell it where to look for files, nothing very bad will happen if a disc is temporarily missing.

It will play a wide variety of files. I suggest you download it and have a play before asking any more questions, it's easy to do and won't break anything.

---

