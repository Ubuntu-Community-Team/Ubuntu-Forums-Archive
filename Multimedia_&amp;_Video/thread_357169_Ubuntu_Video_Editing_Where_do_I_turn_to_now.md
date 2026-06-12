---
title: "Ubuntu Video Editing: Where do I turn to now?"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by doundounba on 2007-02-09
Hi all,

So I've been trying to do some video editing.  Nothing *too* fancy, just things like putting together a Best Moments reel from footage shot during a trip, that kind of thing.  I'm running Kubuntu Edgy (with the nvidia drivers) on an Athlon X2 4200 with 2gb of ram and a Geforce 7600GS.  Beyond getting things *installed* and having to figure out things like compiling custom versions of ffmpeg, here's what my experience has been like so far:

- Kino:  what it does do, it does well.  Video capture works very well for me. I was also able to add captions to a slideshow video created with digiKam using Kino.  I find the interface generally nice, but it doesn't seem to work as non-linear video editor (or at least, I can't seem to figure out how to get the same kind of timeline view I get with other software).

- Kdenlive:  looks very promising, but is very, very early software.  Couldn't get it to switch to an NTSC project (from its default of PAL).  But I was able to edit together parts of clips and export that out.  However, the show stopper for me here is that the exported video isn't accurate wrt the cuts I had requested.  That is, for example, a panning shot ending on someone's face cuts out before I've finished panning, well before the outpoint I'd set on the clip.

- Open Movie Editor: younger than even kdenlive.  Right now, it can only use 25fps footage.  See you in six months, maybe.

- MainActor:  commercial software, but I'd pay, given my results with the other options. Interface is intuitive to me, the software is very responsive.  Only (major) problem is: Boom!  And I'm not talking about a Jobs-ian, see-how-fast-this-is, "Boom!" ([link]("http://www.youtube.com/watch?v=r8L39UwOS-Y")).  I'm talking about, repeated, sudden, apparently unavoidable crashes.  Take two clips, put them back to back on the timeline, hit play: boom!  Try to export instead: boom!  Try to put them on different video tracks: boom!  You get the picture, but I don't get my movie.  Dunno what the problem is here - either other people can't be having these problems or they must have sold exactly zero seats of their Linux version.

- Cinelerra: hmmmm, this one is a head scratcher.  The interface is... non-intuitive for me, to say the least.  However, it appears to be the most functional piece of software for editing.  I was able to successfully (and accurately) stitch together a few clips and then render that out as an ogg movie.  But various other things make it next to unusable.  Sometimes I have no sound.  Sometimes I have sound but playback when viewing a clip is at something like 12fps; or the audio plays, but video doesn't, it just stays on the first frame of the clip.  Sometimes the interface freezes.  And its understanding of "Quicktime" appears rather idiosyncratic - if I export to Quicktime, *nothing* else seems to understand (VLC, Mplayer, Kaffeine, Kaboodle, you name it).

Soooo...  What next?  I could invest more time to try to learn Cinelerra's quirks and troubleshoot its problem.  Even then, it looks like if I want a nice (smallish) quicktime file, at the end I need to export to something like raw DV and take the results to a friend's Mac (or maybe try to recompile Kino with quicktime support).

Or, I could try to run windows video editing software under Wine.  Does that even work for anyone?

I could give up and buy a copy of Vista.  That'd be pretty annoying, not to mention expensive.  I've been windows-free on my main machine for a long time now, I'd prefer not to have to go back.

Or I can try to get access to someone's Mac (or heck, even PC)...  Can Macs/PCs read (my external HD's) ext3 filesystems?  Maybe some friends will be able to help a poor Linux soul.  Not too great a situation for someone advocating open-source to his friends though...

Any advice?

---

### Post by uuwatti on 2007-02-09
KDEnlive works perfectly for me (I live in PAL world). But as you said its early in development. Kino is WAY too simple for any serious work. Cinelerra just keeps crashing all the time for me and the interface is unbearable. With MainActor I never had any problems, it has never crashed for me or anything. 
The biggest problem with Linux software is the lack of decent editing apps. I hope that KDEnlive will put all our problems to history. Meanwhile Blenders editing capabilities make it the only completely functional open-source NLE.
You can export your movie to anything that makes sense and then just convert it to Quicktime using mencoder or VLC.
Windows can read and write ext3 [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by dsegarra on 2007-02-09
How bout Lives?. I installed it yesterday with no problems but havent used it. 


[http://lives.sourceforge.net/](http://lives.sourceforge.net/)


Any thoughts?


Dan

---

### Post by dsegarra on 2007-02-09
link is broken but try this one for screenshots:

[http://lives.sourceforge.net/index.php?do=screenshots](http://lives.sourceforge.net/index.php?do=screenshots)

---

### Post by Shay Stephens on 2007-02-09
> **uuwatti said:**
> 
Windows can read and write ext3 [http://www.fs-driver.org/]("http://www.fs-driver.org/")

fs-driver corrupted my hard drive.  I don't blanket recommend it anymore.  Better would be (if using windows) to create and save your file, then when in linux, read/copy/move the file from there. 

As far as video editing, the only thing that has really ever worked for me has been avidemux.

---

### Post by baobab68 on 2007-02-10
Not an open source solution, but I've just been trying a trial version of Vegas (I found version 4 on the net) and it sure does run like a dream under VirtualBox.

*Almost* like running it under native Windows.

---

### Post by doundounba on 2007-02-12
Hi guys, and thanks for the advice!  I looked into LiVES and at first brush, it seems to really dislike the (NTSC) .dv files that I captured with Kino.  Hmmmmm.  I'll try to dig into that eventually, but for now I need to do a few other things, so I won't have time to look into the video stuff for a few days.

Virtualization, as suggested by baobab68, is another possibility I hadn't thought of.  For now, I'm thinking of doing editing with my laptop, where I still have a copy of XP hanging around.  I can use a KVM switch, or maybe try to find out if it's possible to display an XP desktop remotely on a Linux box, in order to at least be able to use my (large) desktop monitor.  This is all a little annoying, I must say, as my laptop isn't as powerful a machine as my desktop and I was really hoping Ubuntu could handle simple video editing. :(  Maybe once Ubuntu Studio comes out...

---

### Post by doundounba on 2007-02-14
Another quick followup...  My opinion of Kdenlive is improving.  If I first create a new (NTSC) project and save it, before importing any clips, it's much happier, and I can at least accurately put together sections of clips and export that out to raw DV.  Now I wish some of the lower quality rendering options had the right aspect ratio for NTSC, but I can use other tools for that.  It also seems to get confused when I try to have multiple excerpts from the same clip on my timeline.  I'm now thinking of building from source as development progresses.  I need to see how active the development is and how safe (or not) it is to build dailies...

Also, sound problems seem to be linked to Firefox - actually probably the Flash player.  Mostly, if I don't have sound in Kdenlive or Cinelerra, I can get it back by quitting Firefox.  (Odd that this doesn't affect Amarok, but hey.)

---

### Post by P_Badger on 2007-02-18
I've been going a bit nutty trying to find a good open-source NLE for Linux, and so far the absolute best I've found is Kdenlive. Unfortunately, much like every other (free) NLE I've come across for Linux, it's *really* crash prone. Here's hoping the (near) future brings a more stable release.

Lives is buggy and underdeveloped and crashes faster than James Dean on a bender. Same with Jahshaka and Kino.

I've never had *any* luck with cinerella, it screws up seconds into starting it up, and with all the searching I've done online trying to find fixes for its woes, nothing has seemed to work.

So yeah, I still stand behind Mainactor as the best current solution for an NLE on Linux. The only issue I've had with it was a crashing problem during inserting text, but that issue was fixed a couple of updates ago, and runs fine on Ubuntu, now.

---

### Post by doundounba on 2007-02-19
P_Badger:  I'm surprised that our experiences of MainActor and Kino are so different.  What kind of video are you editing and how are you acquiring it?  Are you editing PAL?  I'm acquiring NTSC dv files from a Panasonic PV-GS400 using Kino.  I haven't really tried to use Kino for editing, but for acquiring and some effects, it's been quite stable for me.

As for MainActor, I haven't been able to accomplish anything with it.  Basically, I launch it, click to add clips and select a couple of clips.  So far so good.  Then, select in and out points in both clips and drag them to the timeline and hit play: boom.  Try to export: boom.  Is there a trick I'm missing?

---

### Post by SadaraX on 2007-02-19
Not sure what you needs for a video editor are, but I thoroughly recommend Avidemux, if you like VirtualDub back in Windows, this program may suit your needs quite nicely.

You can download it from [www.getdeb.net](www.getdeb.net) or you can try my custom Edgy version:
[http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb](http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb)

If you feel really daring you can try the latest development unstable version. The official statement by the developers concerning non-stable versions is "Do not use if you want to save what you make" basically meaning no there is no guarantee. If you can, I would say use version 2.3, but 2.4 will probably not hurt you (I use it all the time and it is pretty stable).
[http://students.washington.edu/cdobrich/avidemux_2.4.0_unstable_i386.deb](http://students.washington.edu/cdobrich/avidemux_2.4.0_unstable_i386.deb)

---

### Post by P_Badger on 2007-02-20
> **doundounba said:**
> P_Badger:  I'm surprised that our experiences of MainActor and Kino are so different.  What kind of video are you editing and how are you acquiring it?  Are you editing PAL?  I'm acquiring NTSC dv files from a Panasonic PV-GS400 using Kino.  I haven't really tried to use Kino for editing, but for acquiring and some effects, it's been quite stable for me.

As for MainActor, I haven't been able to accomplish anything with it.  Basically, I launch it, click to add clips and select a couple of clips.  So far so good.  Then, select in and out points in both clips and drag them to the timeline and hit play: boom.  Try to export: boom.  Is there a trick I'm missing?

Well, I will say that kino is decent for grabbing dv, when it works. I just find it crashes a lot. And I generally use ntsc. Don't know why you're having such issues with Mainactor, though. Do you have the latest release? I  believe Mainactor is at version 5.5.37.

---

### Post by cvmostert on 2007-02-22
> **P_Badger said:**
> Well, I will say that kino is decent for grabbing dv, when it works. I just find it crashes a lot. And I generally use ntsc. Don't know why you're having such issues with Mainactor, though. Do you have the latest release? I  believe Mainactor is at version 5.5.37.

I installed the demo of MainActor yesterday and i am impressed, finally a video editing program like "windows movie maker" the thing is, when i export... i can not export sound aswell, i get some error... so i think i might need a driver or codec... but i dont know which one yet... it said mpeg audio etc etc error... but i will work on that one today... 

cheers

---

### Post by eriqk on 2007-02-22
Reading this thread with great interest. I'm on a similar quest.
I've found Kino to be a nice no frills editor, and it's been the only app that's been rock solid for me. It's too minimalistic, though, for anything other than quick cuts.

LiVES is a weird one. It takes forever to import footage, and it won't import the DV clips I exported from Kino. Cinelerra isn't as crash prone on my machine as it is on others, but I've been experiencing playback problems. When it works, it's pretty fast, though. 

KDEnlive won't do anything because it won't play nice with avcodec. Too bad, because it seems so promising. Nested timelines, basic compositing, the works.
I'm tempted to try MainActor but I won't be able to afford it as I'm completely broke. Oh well.

Groet, Erik

---

### Post by uuwatti on 2007-02-22
The demo version of MainActor v5 - Linux Video Editing - is fully functional, though it adds a watermark to processed video (without harming your source material). <-- from the website [http://downloads.mainconcept.com/fdl.php?downloads.mainconcept.com+MainActorLinux5.5.37Ubuntu6+mainactor-5.5-37.i386.ubuntu-6.06.deb]("http://downloads.mainconcept.com/fdl.php?downloads.mainconcept.com+MainActorLinux5.5.37Ubuntu6+mainactor-5.5-37.i386.ubuntu-6.06.deb")

---

### Post by nicoladimaria on 2007-02-24
> **uuwatti said:**
> The demo version of MainActor v5 - Linux Video Editing - is fully functional, though it adds a watermark to processed video (without harming your source material). <-- from the website [http://downloads.mainconcept.com/fdl.php?downloads.mainconcept.com+MainActorLinux5.5.37Ubuntu6+mainactor-5.5-37.i386.ubuntu-6.06.deb]("http://downloads.mainconcept.com/fdl.php?downloads.mainconcept.com+MainActorLinux5.5.37Ubuntu6+mainactor-5.5-37.i386.ubuntu-6.06.deb")

here's some informations about mainactor
MainActor v5 - Linux Video Editing - combines a large number of high-end functions 
in one product. The new video-editing software contains the convincing features of 
the predecessor version as well as many additional functions, in order to combine 
video-editing with compositing...
continues on
[http://tinyurl.com/2q2pop](http://tinyurl.com/2q2pop)

---

### Post by cvmostert on 2007-02-24
Thanks for the inofrmation

---

### Post by finite9 on 2007-03-21
Just a me too post--been trying to get a decent editor for Ubuntu...

I use the recent v1.0.0 release of Kino which is the only one that supports importing widescreen footage.  Previous release up till 0.9.7 did not import widescreen and even the version in Feisty's repo is older than this.  Kino 1.0 works very well for me as a dvgrabber and for merging/splitting video and exporting to divx/xvid or mpeg2.  However, as an editor it has many kinks, so I have looked at Cinellera and MainActor.  

MainActor demo, dowloaded today will not recognise widescreen dv imported using Kino, whereas VLC and Totem recognise it perfectly, so this is a complete showstopper for me.

I just installed Cinellera on my Feisty laptop and as I am completely new to video editing, the interface is too alien to me.  I cannot even figure out how to import my dv clips :(

From what you all say here, kdenlive is worth a look, but I cannot find it in the Feisty repositories, and uni-multiverse are both enabled.  Can I ask where others got the deb from?  Im running amd64 btw.

---

### Post by doundounba on 2007-03-21
Not sure they'll work for Feisty, but you can see here for (Edgy) debs: [http://kdenlive.sourceforge.net/wiki/index.php?title=Faq_Install#Ubuntu]("http://kdenlive.sourceforge.net/wiki/index.php?title=Faq_Install#Ubuntu").  The version I've been trying to use includes the following packages: kdenlive_svn20070101_i386.deb,  mlt_cvs20070101_i386.deb and  mlt++_cvs20070101_i386.deb.

If you look at it, I'd appreciate knowing if the packages have been updated to a more recent snapshot.  Been tempted to try to compile from source, but I've been busy with other things and don't currently have bandwidth to dig on the video editing front.  Can't wait for Kdenlive 0.5 though.  I wonder if the developpers have any idea of the expected release date...

---

### Post by eldragon on 2007-08-28
im having the same effect with mainactor...

boom everywhere.......when importing dv files..

i guess i'll try to preprocess them before using them with mainactor and see what happens...

EDIT

importing files as DV V2 with kino, fixes the problem.

apparently mainactor has a problem dealing with RAW dv files.

EOEDIT

---

