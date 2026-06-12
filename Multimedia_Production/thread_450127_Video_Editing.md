---
title: "Video Editing"
date: 2007-05-21
forum: Multimedia Production
---

### Post by locustfist on 2007-05-21
I have moved to Linux because of a program called cinelerra. After looking at some 'tutorials' on how to install it on Ubuntu Feisty Fawn, i am now cross eyed. just about every term mentioned went well over my head...after all i am a designer.artist and not a programmer. I gave kino a go and it is one of the worst video editing programs i have ever used.

can someone point me to a tutorial for extreme newbies on getting cinelerra up and running?

---

### Post by rsambuca on 2007-05-21
It is actually pretty easy to install.  You just have to add a repository to your sources list, which we can help you out with.  First, though, we need to know what cpu you have, as there is a different cinelerra build for different cpu's.  AMDathlon, pentium4?

---

### Post by jiminycricket on 2007-05-21
Kino is just a simple video editor for DVs.  The things you want to look at are Pitivi, LiVeS, or kdenlive.  They still maybe too simplistic for what you want to do though.  You may want to look at Cinepaint and Blender (yes, it can do video, too)

With Cinelerra, here's some help on adding a software repository (don't get too confused) : [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Another good general guide: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

[http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php) has the Feisty Fawn repositories for Cinerlerra.  The i686 should work for all modern processors-- the difference between Athlon and Pentium is mainly optimisation IME-- so it is a safe bet.  If you want that optimization, type ```
cat /proc/cpuinfo
``` into a terminal to find out the name of your processor.

---

### Post by locustfist on 2007-05-21
I'm running an AMD athelon processor

---

### Post by rsambuca on 2007-05-21
I agree with jiminy here.  I would probably just go with the i686 build.

Go to your Software Sources:  System -> Administration -> Software Sources

On the Ubuntu Software tab, make sure you have the universe, restricted, and multiverse boxes all checked, in addition to the main.

Then click on the Third-Party Software tab.  Click the +Add... button.  In the box that opens, enter the following (I recommend copy and pasting)```
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./
```
You can then close the Software Sources window.

Next, open a terminal:  Applications -> Accessories -> Terminal.  

In the terminal, enter the following:```
sudo apt-get update
```
Then ```
sudo apt-get install cinelerra
```

You should be good to go!

Good luck.  If you have any problems, post back here, but for now, I am off to bed!

---

### Post by Apeezee on 2007-05-21
THis is great, installed the prog just fine.  I was looking to install this as well.  It worked but i got a funky error when i started the prog for the first time: [IMG]http://oregonstate.edu/~peila/Errors.png[/IMG] Let me know what i should do.  I tried "sudo echo ........." that whole line in terminal, but it gave me "permission denied"  THX!

---

### Post by jiminycricket on 2007-05-21
See this post: [http://ubuntuforums.org/showpost.php?p=1928842&postcount=37](http://ubuntuforums.org/showpost.php?p=1928842&postcount=37)

Echo doesn't seem to run under sudo (nor does the command ls, I think)

This sounds like it could fix that too: [http://osdir.com/ml/video.cinelerra-cv.general/2006-12/msg00077.html](http://osdir.com/ml/video.cinelerra-cv.general/2006-12/msg00077.html)

---

### Post by Apeezee on 2007-05-21
Sweet.  Did the second link and it works now. :)  I tried messing around real quick with it, and it didn't work, the render wouldn't do it right, but i think its just a matter of me not doing it right...  Ill try again real quick

Edit: Can't even bring in a track now, i get this error: [IMG]http://oregonstate.edu/~peila/errors1[/IMG]  RAWR!

---

### Post by jiminycricket on 2007-05-21
Maybe it didn't pull in all dependencies, like recommends.  I wonder if sudo aptitude install cinelerra would work better.

---

### Post by Apeezee on 2007-05-21
Looks like that might be working now.  Although when i did that command, it didn't update anthing...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

I was just able to pull in a video though

EDIT: Wow, ok, i just got it to work.  I had to mess with some of the render settings to get it to output correctly.  BUt i was able to splice out a scene from the office and make the audio go in and out.  Proof is in the pudding!  THanks for the help!

---

### Post by ArtMan on 2007-06-06
Can I add my problem?

I installed Cinelerra on my up-to-date 7.04 Feisty. This was apparently successful.

However, when I try to run it from Gnome, nothing happens, or at least nothing obvious in the GUI.

When I try to run it in a terminal I get the following error msg: 

**[FONT="Courier New"]cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen[/FONT]**

Synaptic Package Manager says the installed version is 1:2.1.0-2svn2007424ubuntu3. However, the 'installed files' tab lists several files including /usr/lib/libquicktimehv-1.6.0.so.

Cinelerra was installed from the AthlonXP repository (which is the CPU I have).

Thanks for your help!

-ArtMan-

---

### Post by finite9 on 2007-06-07
I really dont get why everyone recommends cinelerra!  Seems like a perpetuating myth that it is the dogs doodies for Linux.  it's not.  Compared to Sony Vegas or Final Cut, it stinks!   yes, it is currently the best available on Linux if you run i386 or use another distro where it has been packaged properly and you want free software.  There is no 64bit package for ubuntu despite cinelerra being targetted at 64bit CPUs and despite Ubuntu being the most popular distro at the moment.

I got a redhat 64bit rpm and converted it to deb with alien and it ran, but some basic functions tended to make cinelerra die instantly.

It is quite difficult to use, as the program does not seem to follow any HIG [guidelines] whatsoever and it is not intuitive even for dedicated video amatuers.

I got mixed results with pitivi, lives and kdenlive...at the install level, and I have no idea why pitivi got chosen for ubuntu studio...probably due to gstreamer backend support and that its gnome targetted.  I really hope this means they are going to do some heavy development on it!!

As for kino, I use this exclusively for importing DV, merging, splitting, cutting scenes and adding fade-ins/outs and basic titles, and this is what Kino excels at...it is really easy to do and works well.

As for anything else like advanced titling, speed-ups, credits, effects and multiple audio tacks, it simply cannot cope.

Best bet if you do not need/film in widescreen is to try Main Actor.  It's not free but it's better designed than Cinelerra.

---

### Post by Cryophallion on 2007-06-07
> **finite9 said:**
> 
Best bet if you do not need/film in widescreen is to try Main Actor.  It's not free but it's better designed than Cinelerra.

I tried Main actor, and then was considering purchasing it... And then they decided to stop releasing it or supporting it. See this post [http://www.mainconcept.com/site/index.php?id=15](http://www.mainconcept.com/site/index.php?id=15)

I did try it out, and it was fair, but not premiere by any stretch.

I have been playing with cinelerra and Kdenlive mostly, and can do basic editing with them, but not the advanced stuff I would like to do. Kdenlive is growing pretty well, but the titler has no centering ability which drives me nuts when titling. Cinelerra doesn't allow filters to only cover part of the clips (such as blurring to get rid of text, etc), and while kdenlive can do blurring on a small area, it has very few effects overall. I haven't been able to do a proper picture in picture effect in either of them.

If anyone out there wants to start up a petition or something to get main actor released open source, I'd be happy to help out. I don't think it is likely to succeed, based on the creators post, but if anyone wants to try, I'm in.

As for the other programs:

Kino - Great for importing the video. Too basic besides that (comparable to imovie and windows movie maker)
Lives: tried it a little, but couldn't really find the tools I needed. 
Jashaka: Once again, tried it a little, but the concepts didn't click for me, and I hate not being able to razor in the timeline itself (which I can't seem to do in Cinelerra also - so if anyone knows how, I'd love to find out, as well as drag and dropping the clips to move them in the timline). The layers concept is interesting, but I don't think it is all that great.
Main Actor - As I mentioned, it's discontinued.
Kdenlive - from the ashes of diva comes the next big hope. Supposedly .5 will be out soon. It seems to show major promise, and razors in the timeline, etc.

Due to my experience with premiere, I figured out cinelerra pretty easily, but I also don't like the way you make media clips, and then they have no thumbnail.

I need to sit down one of these days, learn to program, and help out the projects. It's just that real life commitments always get in the way. In the long run, I think kdenlive shows the most promise, as cinelerra doesn't seem to get updated much, and now that main actor is no more.

Just my thoughts, I wish you the best of luck. It seems that a lot of people are having the same problem. These programs are great, but take a lot of hard work. Unless someone knows of a good corporate sponsor with money to throw around, I think we'll just have to be patient... and dual boot for those really tricky jobs.

---

### Post by ArtMan on 2007-06-12
I appreciate the conversation and suggestions, but does anyone have any help for my inability to run Cinelerra?

TIA,
-ArtMan-

---

### Post by kelvin spratt on 2007-06-12
Their is a bug in the feisty version of Cinelerra I use this version it is the earlier version and it works superb
with full permissions and full support for quicktime mov and mpeg4 raw. Mainactor does not support Quicktime  nor does the later version of Cinelerra with the codecs in the packages.these 2 links tell you how i got Cinelerra working it needs careful setting up but then it works perfect for me
[http://ubuntuforums.org/showthread.php?t=464223](http://ubuntuforums.org/showthread.php?t=464223)
[http://ubuntuforums.org/showthread.php?t=463275](http://ubuntuforums.org/showthread.php?t=463275)
the only other linux distro that i have found that supports Cinelerra the same is PURE DYNE

---

### Post by Down8ve on 2007-06-12
This discussion is why I wish folks spent more time developing great applications instead of messing with stuff like Beryl/Compiz.  I have used Ubuntu for two years, and just got handed a MocBook Pro at work.  What a revelation.

Imagine if Shuttleworth decided Feisty was good enough for the next two years and started developing terrific apps.

Mr. Spratt is correct, try the older version.  Good luck!

---

### Post by jacob01 on 2007-07-05
dot use Cinelerra i have tried it and it is verry unreliable although it has some good features and is free it is a night mare to use it crashes constantly, every time i try to import a clip which makes it impossible to use

---

### Post by jacob01 on 2007-07-05
you must be in the wrong forum mac boy get out of here

---

### Post by jacob01 on 2007-07-05
if you still want to use it 
try this        [http://www.robfisher.net/video/cinelerra1.html](http://www.robfisher.net/video/cinelerra1.html)

---

