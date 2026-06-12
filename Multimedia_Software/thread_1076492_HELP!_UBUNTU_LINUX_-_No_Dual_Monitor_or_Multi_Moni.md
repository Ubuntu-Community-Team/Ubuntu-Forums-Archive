---
title: "HELP! UBUNTU LINUX - No Dual Monitor or Multi Monitor Support w/ Multiple Video Cards"
date: 2009-02-21
forum: Multimedia Software
---

### Post by d2globalinc on 2009-02-21
First up, I've been working and helping others with issues of multiple displays using multiple video cards with composite/compiz effects for some time over at this thread: [http://ubuntuforums.org/showthread.php?p=6773314](http://ubuntuforums.org/showthread.php?p=6773314)

The problem is that now that xserver-xgl has been discontinued, and is also no longer included in Intrepid or greater - we have no solution now as a linux community to support a single desktop display across multiple video cards.  If we cant use the full 3D acceleration of our high powered video cards across all monitors to power an entire desktop, then all of this nice new hardware and advances in GPU's is pointless.  

I understand my 6 monitor solution is a bit extreme, but we have been building 3+ monitor solutions using Windows since Windows 98.  Thanks to advances in Virtualization and Hosted Applications we are now finally able to start migrating clients over to a Linux/Ubuntu solution and away from windows.  But this is all in jeopardy if we can't use some of the best user interface advancements in linux because we can't support multiple video cards with 3d acceleration.  We finally get people to switch, only to have to tell them they can't upgrade to the next version because their monitors will not be supported!?

XrandR 1.3 was rumored to be the new solution to this problem, but now after reading this thread: [http://ubuntuforums.org/showthread.php?t=1058961](http://ubuntuforums.org/showthread.php?t=1058961)  I'm finding that there is NO solution in the works or available.

So my question to the community is?  What is going to be the native solution to supporting multiple video cards with monitors combined into a single desktop display while still supporting compiz / composite effects?

Xinerama could not do it without xserver-xgl, xrandr 1.2 can not do it, xrandr 1.3 is not going to do it.. Is there a replacement or add-on xserver like xserver-xgl that can work into the future?  Is there something not well documented that I'm missing?  Please let me know!  I get asked these same questions daily after others view our threads, and youtube videos, and would love to have a solution!  I'm willing to help start a project to accomplish this if one is not available, the demand is HIGH for this solution, and its forcing a lot of people / businesses / clients / etc. to not make the switch to linux/Ubuntu!

Thanks!

Shane Menshik
D2 GLOBAL INC
[http://www.d2global.com](http://www.d2global.com)

---

### Post by amauk on 2009-02-21
this is probably better suited on the xorg mailing list
(you'll get a proper, technical answer as to the current roadblocks to multi-GPU compositing)

I'm by no means an expert, and almost all of my knowledge is gained from various mailing lists, and Phoronix
So, if I'm wrong on anything, correct me

but I believe this is a problem across all OS's at present

There just isn't a good way of doing it

Vista went for the bodge solution
requiring that all GPUs use the exact same driver for composited desktops to work as a single display
I *believe* there's a special software-driven "virtual driver" that co-ordinates the seperate GPU's into a single feed that then splits the feed down for each card output

This impacts performance (each card needs to know what the others are doing), requiring much beefier graphics cards to do the simpliest of 3D effects

Linux has opted to wait until a proper solution can be found
(and I think RedHat has the makings of a proper solution - but it needs some work)

---

### Post by kobyhud on 2009-02-24
I agree this is a big issue.  Multiple display support is the largest issue I have had with linux since I started using it.  At this point I feel like I know way too much about xorg confs for both ati and nvidia cards.  Its time that this was done right.

I agree this probably needs to head to another forum, but there is no problem with it starting here.

---

### Post by markbuntu on 2009-02-24
The only way to really support compositing across multiple monitors is through the drivers themselves. Xorg is moving toward more autodetection and away from manual configuration and pushing eveything into the drivers. 
The latest ati drivers have multiple gpu/multiple monitor xrander support built in to the driver for newer ati cards. It is a little buggy but they are making great progress and improvement with every monthly release.

---

### Post by pdub on 2009-02-28
I have several systems that have 3 monitors or more, all of which are running Ubuntu 8.04. With Shane's help I was able to get them all working as a single desktop with compiz. At some point we will want/need to move to a newer version of Ubuntu.

Vista works perfectly with 3 or more monitors, PLEASE DON"T FORCE ME TO USE VISTA/Windows 7 once Ubuntu 8.04 no longer meets our needs.

---

### Post by AvatarKava on 2009-03-02
While I understand the desire for a "real" solution, having a hacky solution is better than none at all, especially when some are already depending on said hacky solution.

Shane's guide helped me immensely in getting suitable performance out of my three-monitor setup, and right now I've actually been forced to remove a monitor to keep Intrepid running without seizing up.

---

### Post by MiD-AwE on 2009-03-04
Tonight I'm reinstalling 8.04 over my 8.10 install because of this issue.

---

### Post by RomD on 2009-03-15
The perfect multi-monitor support is really the only thing I'm missing from Windows. I'm currently stuck with three separated X screens, which would be perfectly fine if there was a way to move windows between the monitors. I had tearing problems with Twinview due to different monitor types, so I had no choice but to separate them.

With LCD screens getting cheaper by the day, more and more people will use multiple monitors and the lack of a decent way to use them might be a reason for new Linux users to switch back to Windows.

---

### Post by chambernug on 2009-07-08
Due to this issue, I'm going to have to roll back to 8.04, as well.  Meanwhile, my Windows 7 box is happy as can be running three mismatched video cards and supporting five displays without a hitch.

The ability to utilize several displays nearly flawlessly has been the thing that has kept Windows on my desk for years.  It's not that I like the Windows OS, because I pretty much hate it.  It's the fact that it actually works when I need more landscape.  Let's face it.  In many cases, if we're forced to function on Linux without the ability to spread our work out to multiple displays, then we're forced to keep Linux as a secondary OS.  That's a crying shame.

---

### Post by vertago1 on 2010-01-09
I am running 2 ATI cards (with the crossfire bridges) and haven't found a way to get compositing to work even with dual monitors (and dual cards).

I can get it to work with one monitor, and I can get the second monitor to show the X for the mouse, but I haven't figured out how to get the xserver to load anything on the second screen yet.

Who maintains Xinerama? Maybe they could try and build it capable of running ontop of or bellow Xrand.

---

