---
title: "I've had it with NVidia..suggestions?"
date: 2011-08-23
forum: Multimedia Software
---

### Post by kindledwind on 2011-08-23
Ubuntu 11.04 on a P5KE-Wifi mobo...4 gigs of ram.

I've currently got 2 GeForce 6200 LE cards in the machine. It works fine for Windows,but this NVidia crap is old with Ubuntu. 

I had both screens with Ubuntu 10.10, then I'm not sure what happened this week, but Ubuntu 10.10 and 11.04 have decided not to use one of them anymore. The cards are 4 years old, so I'm assuming there's some technical glitch going on with the 2nd card. A clean reinstall of either doesn't help, tried it. Old xorg.conf that used to work doesn't work anymore...and at this point, I'm not sure I care.

I'm gonna throw money at it. What I'm wanting:

A single dual head card that can run 2 20" screens at 1920x1080 comfortably, with Ubuntu 11.04, and fit in an X16 slot. It would be nice if the Unity/Compiz eye candy worked, but if it doesn't, that's alright. If that happens to be a newer NVidia card, then I guess it does...I'm just really sick of screwing with my setup.

I don't play games much, I use it for programming & need the real estate more than the FX. 

Any suggestions?

todd

---

### Post by realzippy on 2011-08-23
Got a GT7950 256Mb that nobody needs,but it hides neighbor slot.
You could get it for free,if your place was somewhere in europe.

---

### Post by kindledwind on 2011-08-23
Sorry, in the north end of Idaho :-)

---

### Post by indrora on 2011-08-23
Refresh My Memory(tm) but isn't that a 96.xx series card? if so, it isn't *nvidia*'s fault but the fault of the folks over at X/Nouveau.

TL;DR: X changed *ONE* number. Now the old nVidia drivers dont work unless you futz with them.

The X Folks changed the ABI version they're using, and now because of that old drivers fail to load because of the new ABI is too new (8 vs. 9). nVidia has released a new version of the kernel module that you can grab off their website. I never trust the versions that a distributor provides as they LIE LIE LIE like lawyers.

As well, do you know if you're using the Nouveau drivers? (nVidia advertises themselves by giving a nice big NVIDIA logo on X startup. Try it some time!)

As well, nVidia will happily tell you through nvidia-settings if you're using Noveau.

Bummer, eh?

You *can* use an updated "beta" version of the driver from nVidia's site -- just go through the hoops of finding what card you have. Once you know that, its easier to just go onto their ftp and find the latest version of the drivers.

---

### Post by realzippy on 2011-08-23
> **indrora said:**
> Refresh My Memory(tm) but isn't that a 96.xx series card? 
6200 LE is supported by 280.xx..
Also only 1 card stopped to work..
xorg.conf existed,so likely using nvidia driver

---

### Post by indrora on 2011-08-23
Then run nvidia-settings as root and fiddle!

---

### Post by handy on 2011-08-23
> **realzippy said:**
> Got a GT7950 256Mb that nobody needs,but it hides neighbor slot.
You could get it for free,if your place was somewhere in europe.

In Europe!? :lolflag:

---

### Post by kindledwind on 2011-08-23
> Then run nvidia-settings as root and fiddle!

Did. Only 1 card available even with a previously proven functional xorg.conf. Used to run okay with 10.10, but would only do 1680*1050...which was fine with me as long as it ran. Last week=no hardware changes, 1 card just decided it didn't like Ubuntu anymore.

I'll put a new card in this machine & keep the old cards around for a server or something.

> Refresh My Memory(tm) but isn't that a 96.xx series card?

Not sure of the series, they've been in there for years. lspci = nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)

todd

---

### Post by indrora on 2011-08-23
I can only tihnk to run nvidia-xconfig and nvidia-settings as root, make sure both cards come up. Are they identical cards? Both come up in lspci? .xsession-errors shows nothing related?

---

### Post by tjones00 on 2011-08-23
> **kindledwind said:**
> Ubuntu 11.04 on a P5KE-Wifi mobo...4 gigs of ram.

I've currently got 2 GeForce 6200 LE cards in the machine. It works fine for Windows,but this NVidia crap is old with Ubuntu. 
[B]
I had both screens with Ubuntu 10.10, then I'm not sure what happened this week,[/B] **but Ubuntu 10.10 and 11.04 have decided not to use one of them anymore.** **The cards are 4 years old, so I'm assuming there's some technical glitch going on with the 2nd card.** A clean reinstall of either doesn't help, tried it. Old xorg.conf that used to work doesn't work anymore...and at this point, I'm not sure I care.

I'm gonna throw money at it. What I'm wanting:

A single dual head card that can run 2 20" screens at 1920x1080 comfortably, with Ubuntu 11.04, and fit in an X16 slot. It would be nice if the Unity/Compiz eye candy worked, but if it doesn't, that's alright. If that happens to be a newer NVidia card, then I guess it does...I'm just really sick of screwing with my setup.

I don't play games much, I use it for programming & need the real estate more than the FX. 

Any suggestions?

todd


You are correct it's a technical glitch.

Two nvidia cards not working in the latest Ubuntu is due to the  allocated memory upon boot to the 32b kernel for the 2nd the video driver. It  doesn't seem to be an issue with 64b systems. I first noticed it with  10.10.

There is a fix 

[http://ubuntuforums.org/showpost.php?p=10997758&postcount=2](http://ubuntuforums.org/showpost.php?p=10997758&postcount=2)

---

### Post by kindledwind on 2011-08-23
Hmmm...that got the dead card lit up...sorta.  It's turning the power on for that side, leaves that monitor black, and wipes out the wallpaper on the other side. Also leaves everything non-functional. White desktop, menu bars & nothing works. At least my phone can surf the net.

Giving a radeon card a shot at the moment.

---

### Post by tjones00 on 2011-08-24
I don't understand you upped the kernel memory but did you create a new xorg.conf with --enable-all-gpus? This is important. If so both displays should be active.

Mixing nvidia and ati........I've never read a success story in linux.

---

### Post by kindledwind on 2011-08-24
> Mixing nvidia and ati........I've never read a success story in linux.

Well, I've got it sorted. And I didn't mix anything. 

Yanked the nvidia cards out, replaced them with a single dual head ATI card. Compiz and Xinerama don't work together, so Unity & Compiz were both not going to work. However, the "unity window manager" interferes with "Ubuntu Classic" on 11.04 & wouldn't let me move a window from one screen to another without sticking or screwing up a display. 

Ahh....Unity is sooooo wonderful....

So, rather than go through the headache of sorting out the Unity/Gnome/11.04/dual screen thing  for the 3rd time in 3 11.04 installs, I finally cracked. Kubuntu 11.04 has a working desktop that knows what to do with 2 screens & looks better than my Mac pro.

Anyway, I'm running again, and it's pretty!! Thanks for the ideas though. Great community here!!!


todd

<rant>
To the guy(s) who created Unity: Your narrow little 'my way or no way' mind is a danger to business, and drives users to other solutions that actually make progress, instead of marching directly into incompatibility with already existing hardware. 

Remind me not to hire you...ever...even to mow my yard. I've seen what kind of mess you can make of a wonderful operating system. I'd hate to see what you could do with a lawn mower.
</rant>

---

### Post by realzippy on 2011-08-25
Great you sorted it out.Please set the thread as solved (threadtools)..
I also migrated to Kubuntu after years with gnome,it really is great
meanwhile.Especially the ability to create absolutely independent 
desktops by using Kwin/plasma instead of compiz:
[http://maketecheasier.com/use-kde-plasma-activities/2010/09/01](http://maketecheasier.com/use-kde-plasma-activities/2010/09/01)

The "My way or Highway" philosophy works,at least for apple.But I think
Canonical forgets the important design factor...time will tell.
No doubt that many experienced gnome users are on the run,on the other hand
newbies seem to like unity;maybe the user-base just changes.
But I don't want to turn your thread into another unity discussion..
have fun
zippy

---

### Post by Duncan Williams on 2011-08-25
glad you got it sorted.
Just had to put this in...
nvidia geforce 6200 cards absolutely fly on 280 drivers and all settings correct in nvidia x server settings and compiz Config Settings Manager **with a single** 24" **display**, and I mean fly...

---

### Post by kindledwind on 2011-08-25
> nvidia geforce 6200 cards absolutely fly on 280 drivers and all settings  correct in nvidia x server settings and compiz Config Settings Manager **with a single** 24" **display**, and I mean fly...

I'm still keeping the good one...gives me an excuse to build another machine :-)

I'll mark the thread as solved.

---

