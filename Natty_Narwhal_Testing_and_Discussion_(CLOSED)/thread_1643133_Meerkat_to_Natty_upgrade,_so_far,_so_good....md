---
title: "Meerkat to Natty upgrade, so far, so good..."
date: 2010-12-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jay Car on 2010-12-11
Hi all,

A few days ago, after reading someone's post about Unity in the forum Cafe (now in Recurring Discussions), I decided to try installing Natty and Unity myself. Partly to see what all the fuss was about, but also to learn if I could be a good narwhal tester, and maybe learn how to properly do bug reports. 

My first attempt wasn't exactly successful (I am the Queen of Understatements here), but it was because I was impulsive and hadn't taken time to learn before jumping in.  No harm done.

Thanks to advice from cariboo907, I understood that it might be best to wait until the weekend to try again. Since then I spent some time reading the sticky posts here...and trying to track down a USB stick that wasn't already being used for something else, or that the grandkids hadn't run off with. No luck with that.

So, rather than fuss with live USBs or DVDs, I decided to just use a spare drive with a basic Meerkat system installed and do an upgrade.  I was going to wait till Sunday to give it another shot, but decided to try last night instead.  After all, what could go wrong? :D

It took about 2 hours from updating the Meerkat, to finishing the Natty upgrade. I was waiting for it to offer a Partial Upgrade, but it didn't.

During the upgrade there was a message about python 2 (screenshot attached) which I was expecting.  And later a few error messages showed up, some offering solutions, some not, but they didn't seem to keep the upgrade from continuing, so I didn't worry about them.  

I did try to take screenshots during those error messages, but neither Print Screen, nor the screenshot app would work by that point. 

The upgrade progressed through the first four steps of "Preparing, Setting new software channels, Getting new packages, and Installing the upgrade."  But it stopped before the "Cleaning up" and "Restarting" steps, with a message saying the upgrade was finished. Then came a warning that the upgrade was incomplete and my system might be left in an unstable state.

(uh-oh)

Being the eternally optimistic pessimist that I am, I restarted the computer, hoping for the best but expecting the worst. 

Happily it rebooted just fine, but nothing seemed to have changed. According to 'About Ubuntu' the system was still a Meerkat. But when checking the Software Sources, everything showed as Natty. Maybe this is a normal thing for Alphas.

By then I was confused and tired, and just needed sleep. 

This morning I checked Synaptic Package Manager, searched for Unity and found that it was not installed.  So I installed it. :)  

I haven't yet found where the "Help> About Ubuntu" info is located in Natty, so I don't know if it still declares itself to be a Meerkat, or not...perhaps it's now merely a Meerwhal.  

One of the icons in the Unity sidebar is blank, so I clicked on it to find out what it was (it is the workspace switcher), and that's what the last screenshot is of.

Truth be told, at first glance I can kind of see why some folks might be unhappy with Unity, but I can also see some great potential. It's certainly nowhere as bad as I was expecting. ;)

With all that said, and because I tend to be overly wordy when I post (I'm sure no one's noticed this already), I'll try not to make new posts here unless I run into problems that I just can't solve by searching and reading, or by muddling through on my own ('cuz muddling is how I learn).  

Mostly I wanted to let cariboo907 know that I _did_ wait to do the upgrade, and that (so far) all is well. 

So, now I should get busy and see what I can break, right? :D

Jay Car

---

### Post by coffeecat on 2010-12-11
I'm so glad that the tidal wave of negativity and moaning in the 'Stop Unity' thread persuaded you to dip your toe in the water here. Welcome to the "fun" forum.

I'm glad also to hear that the thread has now been consigned to the bottomless pit of Recurring Discussions. It has found its true home.

Enjoy! :)

---

### Post by cpmman on 2010-12-11
Welcome to the world of wonder that is next release testing JC - my grandchild is too far away to cause problems but I install the test releases on an external drive so that I can chroot any problems that may occur.  I also use clonezilla to keep a generation or two of the test environment.

I rarely need to post any questions because time-zone differences and accessing Natty testing and discussions answers most questions I may have.  Because of this marvellous free interchange of information my testing can be more "cavalier" than it was when I did it for a living and it is great fun.

Stick with it and be the first to post a problem on Launchpad - you won't regret it and ... have FUN.

---

### Post by Quackers on 2010-12-11
I too, was pleasantly surprised bu Unity once all the initial teething problems and usability issues were ironed out (by others :-) ). I too think it has great potential and will give a more modern feel to Ubuntu.
Above all, have fun :-)

---

### Post by Jay Car on 2010-12-11
> **coffeecat said:**
> I'm so glad that the tidal wave of negativity and moaning in the 'Stop Unity' thread persuaded you to dip your toe in the water here. Welcome to the "fun" forum.

I'm glad also to hear that the thread has now been consigned to the bottomless pit of Recurring Discussions. It has found its true home.
Enjoy! :)

Hi coffeecat, and thanks (love your avatar, by the way), to be honest, some of the negativity made me a little nervous. I have family and friends who are running Ubuntu now, and I thought I'd better find out if Unity was going to cause a lot of future phone calls and help sessions if any of them do an upgrade. Figured I'd better start early and learn how to work with the new changes.

So there's a bit of self-preservation in my motives...fortunately, it's also fun. :) 

> **cpmman said:**
> Welcome to the world of wonder that is next release testing JC - my grandchild is too far away to cause problems but I install the test releases on an external drive so that I can chroot any problems that may occur.  I also use clonezilla to keep a generation or two of the test environment.

I rarely need to post any questions because time-zone differences and accessing Natty testing and discussions answers most questions I may have.  Because of this marvellous free interchange of information my testing can be more "cavalier" than it was when I did it for a living and it is great fun.

Stick with it and be the first to post a problem on Launchpad - you won't regret it and ... have FUN.

Hi cpman! Grandkids are never trouble, really.  But they CAN be a little light-fingered when it comes to things like thumb drives, potato chips, cookies, and my collection of little plush penguins. 

As for Unity, I spent about 3 hours with it this afternoon.  It's ok, but it'll take some getting used to. My biggest problem wasn't Unity though, it was Firefox. Some of my favorite extensions no longer worked in Natty's default Firefox. Made me crazy not to have Tree-style, and Colorful tabs. But that's just temporary, I know. 

Had to fuss with my nvidia driver a bit, but it wasn't a big deal. Tomorrow I'll work with it some more, but so far, so good.

> **Quackers said:**
> I too, was pleasantly surprised bu Unity once all the initial teething problems and usability issues were ironed out (by others :-) ). I too think it has great potential and will give a more modern feel to Ubuntu.
Above all, have fun :-)

Yes, things do always seem to get ironed out.  It's quite amazing to watch the process sometimes.  Though I'm sure it's better than it used to be, Unity does still have some wrinkles...but then, so do I. The important thing, I think, is that Ubuntu finds its own personality (for lack of a better word), and follows its own path. To do that it has to try new things. 

If changes are made that I can't live with, I guess I'd just use something else for a while, but so far, it's been fun watching Ubuntu blossom.

---

### Post by Jay Car on 2011-01-15
Well, it's been a month now. I'm still hanging in there with Natty and Unity - though I really only get to work with it on weekends and some evenings, after work - it's been a bumpy ride, for sure.  Mostly freeze-up  problems. Generally, just waiting for updates, or reading the forums for fixes, has resolved most of the problems.

(Except for Firefox...I know it's not a Natty problem, but I really, really dislike Firefox 4.0b9. blech!)  

Thursday night I updated Natty and nothing broke. Yay!

So I decided to actually do some work.  Installed inkscape and started working on an illustration, and worked for several hours without any freezes or other problems.  Worked on it this morning too, with no problems at all. I even took a screenshot to keep for my Natty notes (I've attached it here). 

But then I did some more updates this afternoon and everything froze up again. :( I know, that's to be expected so I'll just try it again in a few days.  Actually, Natty, without Unity, is really nice and seems quite stable. 

Anyway, just wanted to say how fascinating it's been to watch things change (for better, and for worse) with each week's updates.  

There are a few things I really don't like about Unity, but I'm pretty sure they're all temporary so I can live with 'em for now.  I'll just keep updating, and reading...

...and maybe even learn to like Firefox again, but only when I can have my tree-style tabs back. I hate having the tabs along the top. Yuck. 

:D

---

### Post by akand074 on 2011-01-15
I want to try Natty now.. but if I put it on my laptop I won't use it enough for it to matter, and I use my desktop way too much and I don't have the time to deal with issues too consistently. Perhaps waiting for the final release or at least the beta might be best.

---

### Post by cariboo on 2011-01-16
> **akand074 said:**
> I want to try Natty now.. but if I put it on my laptop I won't use it enough for it to matter, and I use my desktop way too much and I don't have the time to deal with issues too consistently. Perhaps waiting for the final release or at least the beta might be best.

From your signature, you have enough hardware to run Natty in VirtualBox. Install the latest version and give it a try.

@Jay Car, I'm glad to see things are working well for you.

---

### Post by akand074 on 2011-01-16
> **cariboo907 said:**
> From your signature, you have enough hardware to run Natty in VirtualBox. Install the latest version and give it a try.

@Jay Car, I'm glad to see things are working well for you.

Hah, I never thought of that! I could just play around in Virtual Box for testing's sake. Especially since I believe there is 3D support in Linux now with Virtual Box 4.0. If it runs smoothly enough I could decide to install it directly.

---

### Post by Jay Car on 2011-01-16
> **cariboo907 said:**
> @Jay Car, I'm glad to see things are working well for you.

Haha...Somedays things are "well-er" than others. But you warned me there'd be breakage, so I don't get too bothered when it happens. 

Today I couldn't even get the system to boot (still working on it, I'll post a proper help request if I can't figure it out). I'm mostly just doing it for fun, and maybe to learn some new things. 

:)

---

