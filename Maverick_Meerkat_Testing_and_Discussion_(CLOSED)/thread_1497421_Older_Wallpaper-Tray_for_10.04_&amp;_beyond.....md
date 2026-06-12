---
title: "Older Wallpaper-Tray for 10.04 &amp; beyond...."
date: 2010-05-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2010-05-30
I have grown fond of Wallpaper-Tray over the years & mourned it's drop from 10.04...Well, I did some experimentation & found that the older version (0.4.6) works very well in both Lucid & Maverick......So if anyone wants it back, here it is.

I also note that this version also works in Gnome Shell just fine--I'm going to see if this older version can be re-introduced into Maverick--In my mind there is not another good wallpaper changer available.

In the .zip are both the x86 & x86-64 .debs  

Test them on your system to see if there are "really" no problems & if not, we can make a good case for it to be re-included in Maverick!!!

---

### Post by rtalcott on 2010-05-30
GREAT!  Thank YOU! I too am a HUGE fan of wallpaper-tray!
rt

---

### Post by Gourgi on 2010-05-30
> **autocrosser said:**
> I have grown fond of Wallpaper-Tray over the years & mourned it's drop from 10.04
...
In my mind there is not another good wallpaper changer available.


i very much agree!


at least there could be a ppa for this package if not an official one.

---

### Post by autocrosser on 2010-05-30
I've been thinking about setting up a PPA--I am waiting to hear back from some developers first--I have asked for re-inclusion in Maverick & backporting to Lucid......We shall see.

---

### Post by ronacc on 2010-05-30
thanks, good find . just for grins I tried the later one (5.5 ) from karmic and that one don't work but I guess you know that already.

---

### Post by 2hot6ft2 on 2010-05-30
Cool, I was missing wallpaper-tray so nice find. Here's another one that works in Lucid if anyone is interested.
[Wallpaper Slideshow]("http://gnome-look.org/content/show.php/Wallpaper+Slideshow?content=125178")
:guitar:

---

### Post by autocrosser on 2010-05-30
> **ronacc said:**
> thanks, good find . just for grins I tried the later one (5.5 ) from karmic and that one don't work but I guess you know that already.

Yes--I tried to bring forward the libboost depends & that did just not work--I was involved in pushing the 0.5.X series into Ubuntu back during Intrepid (removed Wallpaper-Tray from the notifications tray into a "normal" applet), so I was thinking that the old 0.4.X series just might work & it did....

A big plus (in my book) is as the 0.4.X series works in the notifications tray, it would transfer right into Gnome-Shell & it works very well there also---you do need to restart it if you do .gnome-shell --replace, but that's not a very big problem.

The only problem that I see is Wallpaper-Tray is now a un-maintained app....Earthworm has abandoned the project & I have not been able to get a hold of him to get the development files/info.....I guess if I want to see it move into the future, I need to do this & take over the project.......just another thing that adds to my plate :(

---

### Post by autocrosser on 2010-05-30
Hmmmm--judging by the number of hits in the couple of hours this has been posted, I would think that there is quite a bit of interest in this...I have sent a email to the last address on record & have requested information about where this app stands....

If it is un-maintained, I am thinking of becoming it's maintainer...so here we go...........

---

### Post by ronacc on 2010-05-30
I even grabbed the source for 5.5 and tried to build it against mavericks libs , strangely it would configure with no errors ( once I had all the deps ) make , with no errors and install but would not run or generate any error messages . the 4.6 version works great  so I gave up on 5.5 .

---

### Post by autocrosser on 2010-05-31
I got a reply from the Debian maintainer, Jon Dowland...He has stopped as of  2009-11-25 & Wallpaper-Tray is now un-maintained. He told me that the 0.4.X version was written in C & the newer 0.5.x version was written in C++. Not sure if that is causing the current problems, but could be a reason why the 0.4.X version still works.....

His respond: > Hello,

I maintained wallpaper-tray in Debian from 2007-02-05 until 2009-11-25.
Ubuntu initially took the package from Debian.

The version I packaged was 0.4.6, which was written in C. It would
appear that Ubuntu carried my package in Intrepid, but someone packaged
the later C++ version for Jaunty onwards.

If you want to package it again, feel free, I don't need to have
anything to do with it. The last version in Ubuntu was 0.5.5 and you can
get at the package source from
<[http://packages.ubuntu.com/karmic/wallpaper-tray](http://packages.ubuntu.com/karmic/wallpaper-tray)>

Good luck! I look back to Intrepid: [http://packages.ubuntu.com/intrepid/wallpaper-tray](http://packages.ubuntu.com/intrepid/wallpaper-tray)  & see that we still have good information on it.....Next step is to get it re-included---I have comment on ubuntu-development-list---We'll see where it goes..... As to the reference to Intrepid/Jaunty--that's where I contacted MOTU & asked for the 0.5.X version to be packaged...not sure who really did it......

---

### Post by ronacc on 2010-05-31
the problem with the 0.5x version may also have something to do with it being a panel applet rather than an app that just puts an Icon in the notification area .  I also noted a difference in the behavior of the 0.5x karmic .deb and the same source local compiled on my maverick install . The karmic .deb would put an entry in the right click panel menu ( add to panel ) the local compile from the same source would not . Trying to start the .deb version resulted in a non specific error message , trying to start the local version ( without the menu entry I tried both from cli and by clicking on the applet itself) gave no result at all even though it had installed with no errors .

---

### Post by autocrosser on 2010-05-31
Yes--We were trying to move things out of the notification area at that time, so it was thought it would be better to use the 0.5.X version--looks to have been a wrong decision....

I'm trying to get the older version re-instated--I'll keep this thread updated with my progress.

---

### Post by ronacc on 2010-05-31
good work . If you need us to add our votes to the wish list or anything let us know .

---

### Post by autocrosser on 2010-05-31
OK my friends--the next step:  [https://answers.launchpad.net/ubuntu/+source/wallpaper-tray/+question/113021](https://answers.launchpad.net/ubuntu/+source/wallpaper-tray/+question/113021)

Add comments as you feel are helpful......

---

### Post by ronacc on 2010-05-31
added comment confirming what you said and requesting re-inclusion .

---

### Post by stevepoppers on 2010-06-01
YYYYEEEEEEEESSSSS!!!!!!!!!!!!!

You are AWESOME!

One problem is that I can't add it to the panel. It's not in the list and I don't know how to otherwise.

EDIT: Nvm, it runs in the so-called "Notifications Area" after initiating the command. Added it to start-up programs, configured options and am ready to go!

---

### Post by autocrosser on 2010-06-01
If you edit your menu & checkmark "other", you will have a menu entry---It's the older behaviour--but still works very well.....

---

### Post by SevenMachines on 2010-06-02
you might also want to look at desktopnova and see if thats any sort of replacement, it should be synced from debian soon if it hasnt been already

---

### Post by TerminX on 2010-06-02
Thanks for the heads up on desktopnova... I'd been using one called "drapes" but it hasn't been maintained in years and was exhibiting some pretty buggy behavior at times.  I feel like the UI in drapes was a bit nicer than desktopnova, but I never have to see it so it doesn't matter and I don't really care.

---

### Post by MaX on 2010-08-23
So do we have any progress on this?

my sister just upgraded to 10.04, the only question so far is where wallpaper-tray went... They need this functionality in Gnome main.

---

### Post by autocrosser on 2010-08-23
Well--at this point either hand-install the old Wallpaper-Tray or look at one of the alternatives---I have had 0 answers from the devs about this.....

---

### Post by MaX on 2010-08-23
I just wanted to tell you that I'm running 0.5.5 here on my newly upgraded Maverick system. What's the problem?

---

### Post by autocrosser on 2010-08-23
Hmmm--when did you get it installed?  We were having problems with it late in 10.04 & early 10.10----that's why I went back to the .0.4.x version--also, the 0.5.x version will not work in Gnome-Shell at all....

---

### Post by iRobbyp on 2010-08-27
this worked like a charm no problems at all, i had trouble opening it, when i was installing it, it showed me the folder the application icon is ....and i went there and opened it to have the application running in my panel

usr/share/gnome/apps/:popcorn:

---

### Post by MaX on 2010-09-09
> **autocrosser said:**
> Hmmm--when did you get it installed?  We were having problems with it late in 10.04 & early 10.10----that's why I went back to the .0.4.x version--also, the 0.5.x version will not work in Gnome-Shell at all....

I installed it when it came out I guess...

I think it stopped working now though (10.10). 
They really should include this functionality in Gnome-main instead an external program.

---

### Post by autocrosser on 2010-09-09
Try uninstalling the .0.5.x version & then install the .0.4.x version I have posted on the first page...less problems with it..

I'll contact the Development list again about re-inclusion....

---

### Post by dkozhukhar on 2010-09-15
Thanks for pointing that out. Very nice program, like it! 
Sadly, it stops working on big picture (4000x3000px or so). Any one know how to fix that?

---

### Post by madhi19 on 2010-10-02
I installed the version you posted sadly it crash when I try to add the picture folder. Any idea?

---

### Post by autocrosser on 2010-10-02
Well--it's looking like we are at the end of the road for this app--sadly, it has stopped working in Gnome Shell & as there is no development on it I would say that it's days are numbered...If it works for you--that's good---if not, you most likely need to look at some of the others alternatives listed in the first or second posting page...

Wallpaper Tray--I knew you well :(

Ok--I've installed Desktopnova & it looks to work well...guess that is what I'm using now........

---

### Post by madhi19 on 2010-10-03
Yeah I discovered Nova yesterday. It not so bad.

---

### Post by malspa on 2010-10-03
Yeah, DesktopNova is pretty good.  I like Wally better.  I'm using Wally in Lucid's GNOME, but DesktopNova in Debian Squeeze's GNOME (because I don't see Wally available in the Squeeze repos).

Unless I'm missing something, DesktopNova doesn't give you any options for dealing with photos that don't fit your screen perfectly.  Seems to work out fine other than that.

Sad to see the end of wallpaper-tray, though.

---

### Post by madhi19 on 2010-10-03
> **malspa said:**
> Yeah, DesktopNova is pretty good.  I like Wally better.  I'm using Wally in Lucid's GNOME, but DesktopNova in Debian Squeeze's GNOME (because I don't see Wally available in the Squeeze repos).

Unless I'm missing something, DesktopNova doesn't give you any options for dealing with photos that don't fit your screen perfectly.  Seems to work out fine other than that.

Sad to see the end of wallpaper-tray, though. Go to the appearance menu set the background image on "scale" that will fix your problem. I had the same yesterday!

---

### Post by malspa on 2010-10-04
> **madhi19 said:**
> Go to the appearance menu set the background image on "scale" that will fix your problem.

I see.  So, there are no "style" settings (such as scale, stretch, center, etc.) in the DesktopNova GUI itself, but instead you can go to System > Preferences > Appearance > Background tab, and select the style there.  Thanks for the tip!

---

