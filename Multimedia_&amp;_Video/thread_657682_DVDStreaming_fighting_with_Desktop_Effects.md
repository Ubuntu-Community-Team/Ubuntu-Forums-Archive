---
title: "DVD/Streaming fighting with Desktop Effects"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by kreeeka on 2008-01-03
Ok so,

After fighting for days trying to get my DVDs to play properly. I realized after restoring my original xorg.conf file that DVDs will play fine as long as I have no desktop effects on. Once I turn them even to normal... they basically don't even play..  I have a pretty nice graphics card and I have the drivers setup (restricted) and I followed almost every single piece of advice I could find on forums related to getting dvds to play..  can anyone help??

Thanks a lot.

---

### Post by theacoustician on 2008-01-03
> **kreeeka said:**
> Ok so,

After fighting for days trying to get my DVDs to play properly. I realized after restoring my original xorg.conf file that DVDs will play fine as long as I have no desktop effects on. Once I turn them even to normal... they basically don't even play..  I have a pretty nice graphics card and I have the drivers setup (restricted) and I followed almost every single piece of advice I could find on forums related to getting dvds to play..  can anyone help??

Thanks a lot.
It would be helpful to know
-Which *buntu and version you're using
-Hardware specs
-What you mean by "play back properly".  Did they not play at all, skip, etc?
-What program you're using to play the DVD
-What you've tried so far

Not trying to answer a question with a question, but that would help narrow things down quickly.

---

### Post by kreeeka on 2008-01-03
Okay.. I guess I should mentioned all that..
I just thought maybe someone had run into the EXACT same issue..

 7.10 (gutsy) 64 bit
Amd Dual Core 5200+
Ati Radeon X 1950pro 512MB

I've tried using ENVY.. (had some issues but eventually worked them out)
I've installed countless codecs and other things recomended.

Bascially what happend.. is as soon as I setup my OS... I wanted to setup the effects..
But it wouldn't let me.. because I hadn't installed my video drivers... so I used ENVY.. and then it worked fine.. then I tried to play a DVD.. noticed it didn't work... Tried multiple programs.. (Xine, gzine, Totem, VLC)... at first it wouldn't play them.. was getting some random error... so I started looking for help on the forums.. and I believe I basically installed a bunch of codec packages.. and then I would get no more error.. but the video would basically be so choppy.. that it might as well been flashing black.. maybe 3 times a second.

I tried turning off the restricted driver... and when I rebooted.. my OS wouldn't even load.. so I had to restart in Recovery mode.. and replace my xorg.conf file with a backup I had made as soon as I installed ubuntu.. When I got back into the OS... The first thing I did was try and play a DVD... the DVD played fine.. but my effects were off... so I turned my effects back on.. and then the DVDS started flashing blank again. (Streaming video does the same thing)..

Also on a note... Even the main screen that comes up when you first open totem flashes. (when effects are on).

Edit: I guess I also should have mentioned that the audio when playing a movie works fine. even when the video is flashing.

---

### Post by theacoustician on 2008-01-03
> **kreeeka said:**
> Okay.. I guess I should mentioned all that..
I just thought maybe someone had run into the EXACT same issue..

 7.10 (gutsy) 64 bit
Amd Dual Core 5200+
Ati Radeon X 1950pro 512MB

I've tried using ENVY.. (had some issues but eventually worked them out)
I've installed countless codecs and other things recomended.

Bascially what happend.. is as soon as I setup my OS... I wanted to setup the effects..
But it wouldn't let me.. because I hadn't installed my video drivers... so I used ENVY.. and then it worked fine.. then I tried to play a DVD.. noticed it didn't work... Tried multiple programs.. (Xine, gzine, Totem, VLC)... at first it wouldn't play them.. was getting some random error... so I started looking for help on the forums.. and I believe I basically installed a bunch of codec packages.. and then I would get no more error.. but the video would basically be so choppy.. that it might as well been flashing black.. maybe 3 times a second.

I tried turning off the restricted driver... and when I rebooted.. my OS wouldn't even load.. so I had to restart in Recovery mode.. and replace my xorg.conf file with a backup I had made as soon as I installed ubuntu.. When I got back into the OS... The first thing I did was try and play a DVD... the DVD played fine.. but my effects were off... so I turned my effects back on.. and then the DVDS started flashing blank again. (Streaming video does the same thing)..

Also on a note... Even the main screen that comes up when you first open totem flashes. (when effects are on).

Edit: I guess I also should have mentioned that the audio when playing a movie works fine. even when the video is flashing.

Actually, you may be making it harder by using Envy.  Try going to System->Administration->Restricted Drivers Manager and install them that way.

---

### Post by kreeeka on 2008-01-03
When I reboot after installing that way..
The OS wont load... (screen goes blank at one point..).. had to reload xorg.conf file.

;o(

---

### Post by theacoustician on 2008-01-03
> **kreeeka said:**
> When I reboot after installing that way..
The OS wont load... (screen goes blank at one point..).. had to reload xorg.conf file.

;o(

Try this [http://ubuntuforums.org/showthread.php?p=4035799#post4035799](http://ubuntuforums.org/showthread.php?p=4035799#post4035799)

---

### Post by kreeeka on 2008-01-03
Ok.. so this time..
I used Envy to uninstall the ati driver.. then I disabled the restricted driver...
and rebooted..

As expected in wouldn't load into the OS again..
So this time..
instead of reloading the backed up xorg.conf file...
I tried what was in that post..

The update.. and the download seemed to work fine..
But when I went to configure the driver...

It basically said.. nothing to configure.. or something along those lines..

I tried to reboot anyway.. to see what would happen.. and it just went blank before loading the OS again.

poo.

---

### Post by wesswei on 2008-01-04
hi kreeka,

I just wanted you to know I have the exact same problem, and my only remedy has been to disable the desktop effects. I know that's very annoying to disable and re-enable everytime you want to watch a video or dvd, but that's how it is for me. 

compiz is still pretty much beta (maybe even alpha) so just report your bugs to launchpad and hope the coders can reproduce the same error and fix it with future releases.

it shouldn't be that hard to get media files to work alongside the effects.

My system is a little slower than yours: 
Ubuntu Gutsy, 
ASUS a7n8x mobo, 
512KB DDR, 
Amd Athlon XP 2500+ (1.8ghz) 
Radeon 9600 pro agp (128mb ddr) 

I installed the 7.11 (8.43) ATI driver manually (after many times trying to get the "restricted driver 8.40" to work from gutsy) I actually ended up reinstalling because everytime I installed the ati restricted driver, it booted in safe graphics mode. Finally I have an xorg.conf config I like (without dual monitors; don't get me started on that)

Now effects are awesome, but video flickers just as you described. 

If anyone has any ideas, don't forward links if it doesn't relate to the problem. Thanks!

---

### Post by wesswei on 2008-01-04
> **theacoustician said:**
> Try this [http://ubuntuforums.org/showthread.php?p=4035799#post4035799](http://ubuntuforums.org/showthread.php?p=4035799#post4035799)

What does this thread have to do with anything? We're talking about DVD/Streaming and flickering with desktop effects. Sounds nothing like TV in/out.

---

### Post by kreeeka on 2008-01-04
> **wesswei said:**
> What does this thread have to do with anything? We're talking about DVD/Streaming and flickering with desktop effects. Sounds nothing like TV in/out.


I think the thread that he mentioned was to fix the blank screen I was getting without resetting my xorg.conf file.. but it didn't seem to work. 
> **wesswei said:**
> 
I just wanted you to know I have the exact same problem, and my only remedy has been to disable the desktop effects. I know that's very annoying to disable and re-enable everytime you want to watch a video or dvd, but that's how it is for me.
 


I was thinking about just doing that..but I wasn't sure if there was a quick fix or not.. but knowing that you have the same problem makes me feel a ton better. Thanks for posting about it.. and thanks for trying to help out Theaccoustican. I appreciate it. 

Hopefully someone will find a fix for this.. or like you said.. it will be fixed in the next update.

---

### Post by theacoustician on 2008-01-04
> **wesswei said:**
> What does this thread have to do with anything? We're talking about DVD/Streaming and flickering with desktop effects. Sounds nothing like TV in/out.
Try reading it again.  Its how to install the fglrx drivers from a command line startup.  I have the same issue on startup with a machine here at work (boots fine, then goes black at the login screen) and that was the only way I got the drivers to behave.  I'm guessing if he follows that and install the drivers himself, he'll have better luck with desktop effects and playing DVDs.  Script installers are something to be avoided.  

To the thread starter : If you keep running into graphics related issues, you may want to bite the bullet and get a low end nVidia card.

---

### Post by kreeeka on 2008-01-04
Yeah, not really sure what I'm gonna go about it yet... Kinda sucks.. there must be something I can do to make it work right with the card I have.. just going to mess around a lot and see what I can learn.

---

