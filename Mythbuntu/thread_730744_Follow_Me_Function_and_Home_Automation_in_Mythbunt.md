---
title: "Follow Me Function and Home Automation in Mythbuntu"
date: 2008-03-21
forum: Mythbuntu
---

### Post by thejoeshmoe on 2008-03-21
Hey Guys 

I've got really excited about linuxMCE because of features like the "Follow Me" function, and the home automation stuff - dimming the lights and whatnot.  However -- reading more into it -- it sounds like Mythbuntu is MUCH more stable (Linux MCE seems to have very poor support and a lot of bugs).

My question though -- when are these features going to be implemented?  If they were put into place, I think mythbuntu would be the hands down DVR killer!

---

### Post by nasha on 2008-03-21
MythTV is hands down DVR killer... It does its job much better than LinuxMCE not to mention has much more hardware support. But DVR is exactly what it is, and serves its purpose well.

I dont think MythTV is the ideal setting for integration with home automation, and i doubt we'll ever see it, but there are plenty of open source options out there.

```
http://www.homeautomationindex.com/
```

---

### Post by laga on 2008-03-21
> **thejoeshmoe said:**
> 
My question though -- when are these features going to be implemented?  If they were put into place, I think mythbuntu would be the hands down DVR killer!

I've never used LinuxMCE so I can't compare it against Mythbuntu..

As far as I know, no Mythbuntu developer is using Home Automation stuff so it most likely won't be implemented.. but it's open source and patches are always welcome!

---

### Post by thejoeshmoe on 2008-03-21
> **nasha said:**
> 

I dont think MythTV is the ideal setting for integration with home automation, and i doubt we'll ever see it, but there are plenty of open source options out there.

```
http://www.homeautomationindex.com/
```

I think home automation IS the perfect match for a DVR.  Check out the  LinuxMCE video -- [http://video.google.com/videoplay?docid=-4422887272477313460](http://video.google.com/videoplay?docid=-4422887272477313460)

When the guy sticks in the DVD and the lights automagically fade, oh thats beautiful...

---

### Post by volkswagner on 2008-03-21
Do I smell a new Plugin Brewing?

---

### Post by freymann on 2008-03-21
> **thejoeshmoe said:**
> 
I've got really excited about linuxMCE because of features like the "Follow Me" function, and the home automation stuff - dimming the lights and whatnot.  However -- reading more into it -- it sounds like Mythbuntu is MUCH more stable (Linux MCE seems to have very poor support and a lot of bugs).


 After spending 8 days *trying* to get a working LinuxMCE system up and running, I will warn you_ not to get too excited_ about LinuxMCE. I would be interested in revisiting it in a year (when they've had more time to code it) but LinuxMCE does not concentrate much on the "media part" and it's interface to using and viewing/listening to music, photos and movies is terrible in comparison to MythTV and its plugins.

 The Gyro mouse thing is nice, and getting to your media is easy that way, but actually doing something useful with your media like "Play All Music By Led Zeppelin, in random order", or "Run a Slideshow of this folder of pictures" is complicated. MythTV does it nicely in a few keystrokes.

 Mythbuntu 7.10, on the other hand, works, and works great! Everything about MythBuntu is great. LinuxMCE uses a highly modified version of MythTV. The automation feature is great but do you really need it?

 The follow me feature of LinuxMCE is nice too. I'm sure MythTV could implement something similar, but really all you need to do is quit what you're doing in room 1 and go to room 2 and pick up where you left off (use the bookmark feature to return to where you were in a recording for example).

 Don't believe the hype. You're much better off with MythBuntu!

---

### Post by tgm4883 on 2008-03-21
LinuxMCE is just a ubuntu version of Plutohome (which runs on debian).  To get the home automation stuff working, they sync a lot from Plutohome (ie, they run the plutohome software).  I've spoken with the Plutohome people and the LinuxMCE developers and I must say that I was less than impressed.  As of today, we are still waiting for the Gutsy release for LinuxMCE, and it is to the point that I am wondering if Ubuntu Hardy will beat it to release.  IMO, LinuxMCE is not a viable option if you want home automation.

For Mythbuntu to add home automation into the mix, we would more than likely need to add a backend server for that (something like misterhouse) and then develop frontend plugins for it.  This is a lot of work and while it would be cool, we don't have the time or developers to spend on this sort of thing.  With that being said, if anyone would like to join the team to work on that your help would be greatly appreciated.

:EDIT:

I meant to also add the link to plutohome.   [http://plutohome.com/](http://plutohome.com/)

---

### Post by freymann on 2008-03-21
> **tgm4883 said:**
> 
For Mythbuntu to add home automation into the mix, we would more than likely need to add a backend server for that (something like misterhouse) and then develop frontend plugins for it.  This is a lot of work and while it would be cool, we don't have the time or developers to spend on this sort of thing.


 That is so true... and I think us users would prefer to have a solid product that works than spread the programmers too thin.

 The automation control would have to be available on-screen much like LinuxMCE though... where no matter where you are you can bring up the menu and control lights or whatever.

 There's a neat 'hack' to control X10 from within the MythTV main screen [[link]("http://mythtv.org/wiki/index.php/X10")] but that isn't very useful if you have to quit what you're doing, navigate back to the main screen, select a precanned command, then go back to what you were doing.

 That, at least, is one thing LinuxMCE has thought out well. Now making it work on real equipment is a completely different story. As I said to the poster a few back, don't let that demo video get you worked up! In real life LinuxMCE doesn't run as smooth as the video makes it appear. You need very specific hardware and none of it is cheap.

---

### Post by pssturges on 2008-03-21
I've had a bit of a look at LMCE and I must agree with what others have said here. LMCE is a great concept. But it really isn't a viable option *yet*. You would need a *lot* if spare time on your hands to set it up properly.

Personally, the one feature from LMCE that I would like to see in Myth, is the ability to play the same content at the same time on multiple frontends(syncronized). Particularly with music. ie filling your house with music, not just one room!

The other thing that I *really *would love to see (having come from MSMCE) is the ability to navigate through menus while media is playing. Rather than thumbnailing the media like MSMCE does, it would be better if it the ui was overlayed on the media, as LMCE does, very slick!

There are probably other places I should be mentioning this, but just my thoughts.

Phil

---

### Post by Neural oD on 2008-06-26
Late bump on this post - but wouldn't pulse audio enable multiple outputs to audio devices at the same time - pulse is supported well in hardy - i think ;)

---

### Post by bblboy54 on 2009-01-25
This is even a later bump but I'd still like to put my 2 cents in.

First of all, I agree with everyone NOT to get excited about LMCE.  I mean, the concept is great but the people who run the project are complete idiots and seem to totally not understand what open source is all about.  For instance, if you have a problem with X device and you post to the forums you are most likely going to get a response that you need to buy Y device that is $300 because it's the only one that they support.... then later be made to be an idiot because you'd want to actually use the software on universal hardware.....   I fought with this project for about 4 or 5 months.... I even put money into buying some recommended hardware and I could never get the stuff working right and NEVER got any help on the forums.

I'm back to using MythBuntu now but I feel so empty now without the features that were supposed to work in LMCE.  I would absolutely love to have X10 support in MythBuntu and other home automation features.  I think there is a huge void now with LMCE giving the false hope to so many people.  I actually think that having MythBuntu interact with a Mister House server would be the greatest route to this.

Anyway, I'm not a developer so I can't really help much but I just wanted to toss my 2 cents in that there is another person that would love to see MythBuntu interact with my lights, cameras, and... action? :)

---

### Post by freymann on 2009-01-25
> **bblboy54 said:**
> 
First of all, I agree with everyone NOT to get excited about LMCE.  I mean, the concept is great but the people who run the project are complete idiots.

They are making progress in the way they handle the forums, but you are correct... some people do take a beating! and that's usually because they didn't read up on the suggested configuration and then go complain nothing works.

There aren't a ton of programmers working on the project which is why it doesn't skip along at a fast pace.

> 
if you have a problem with X device and you post to the forums you are most likely going to get a response that you need to buy Y device that is $300 because it's the only one that they support.

I would beg to differ. If you read through the wiki and forums it isn't hard to find out what products work. During my first run, I thought I had purchased equipment that would work, but for whatever reason, my core was a complete bomb. So I went to MythBuntu and set up 3 stations in a day.

But about 4 months later, I had bought another machine to become the main core and installed the LinuxMCE 7.10RC2 version on it, and everything worked the way it was supposed to!

Since June 08, I've been running LinuxMCE with a main hybrid core and a few media directors, with one mythbuntu machine in the mix too.

I now enjoy integrated X10 control and have recently added some telecom equipment too. I now use just one remote instead of 4 (using the USB-UIRT IR blaster). My Media Directors don't need to have local hard drives and you can access and control the entire system in many different ways (what they refer to as orbiters).

You can see my setup with details on equipment and pictures here:

[http://wiki.linuxmce.org/index.php/User:Freymann](http://wiki.linuxmce.org/index.php/User:Freymann)

While I was using MythBuntu, **I did integrate X10 lights to my setup**. I could control the lights (on/off/dim) through unused buttons on my MCE remote or on screen menus, and through a web page. If you're interested in how I did that, have a look at this link:

[http://ubuntuforums.org/showthread.php?p=4733977#post4733977](http://ubuntuforums.org/showthread.php?p=4733977#post4733977)

---

