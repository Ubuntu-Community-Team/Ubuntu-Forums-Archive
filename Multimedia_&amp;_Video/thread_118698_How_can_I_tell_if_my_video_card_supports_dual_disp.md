---
title: "How can I tell if my video card supports dual display?"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by aysiu on 2006-01-17
Dumb newbie question here.

I'm thinking about setting up a dual display for my computer. 

How can I tell if my computer's video card supports dual display? There's a jack in the back of the computer for dual display. Does that mean it's supported?

If I boot into Windows and see something like this (see attached screenshot), does that mean my video card supports dual display? And if I don't see it, does it mean my video card does *not* support dual display?

Apparently, it's an NVidia GEForce4 MX. I'm not sure what that means.

---

### Post by earobinson on 2006-01-17
yes it should.

all of those things suggest it supports dual display, + when you google it [http://www.firingsquad.com/hardware/geforce4/default.asp](http://www.firingsquad.com/hardware/geforce4/default.asp)

EDIT: even better link [http://www.nvidia.com/page/pg_20020201403631.html](http://www.nvidia.com/page/pg_20020201403631.html)
> Integrated Dual 350MHz DACs
Drives two independent CRT displays with crisp and clear image quality at 2048x1536 resolution @ 75Hz.

I have been told this can be hard to setup

---

### Post by aysiu on 2006-01-17
Thanks for the reply, earobinson.

So, in other words, yes for Windows, difficult for Ubuntu?

Would the best approach be to set it up in Windows, make sure it works there, then set it up in Ubuntu and do a ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by earobinson on 2006-01-17
That would be my guess, having never set it up before I cant help you much with the setup, I just know that your card can support it, at least in windows. I have seen some posts that look helpfull.

[http://www.ubuntuforums.org/showthread.php?t=20128&highlight=dual+display](http://www.ubuntuforums.org/showthread.php?t=20128&highlight=dual+display) (they seem to have had it working with horay)

Sorry I couldent be more helpfull

---

### Post by aysiu on 2006-01-17
Thanks, earobinson. I'll do some trial and error and some searching.

---

### Post by earobinson on 2006-01-17
Let us know all the same.. ill be following this.

---

### Post by aysiu on 2006-01-17
I ultimately decided a dual-display was too much trouble. I'm just using a spare monitor that's larger and has a better max screen resolution. Thanks for your help, though.

---

### Post by WildTangent on 2006-01-21
It's actually quite easy to do Aysiu, I just set it up on my friends computer with a Radeon 9600. What kind of card do you have? 

-Wild

---

### Post by aysiu on 2006-01-21
[QUOTE=WildTangent]It's actually quite easy to do Aysiu, I just set it up on my friends computer with a Radeon 9600. What kind of card do you have? [/QUOTE] Hey, WildTangent. Thanks for answering. Please treat me like a total newbie, because as far as hardware goes, I *am* one.

Okay, what it says on my computer is **NVidia GeForce4 MX Graphics.**

I've also attached a picture of the back slot of my computer that has me even thinking about a dual display (the picture circled in red).

What has me confused, though, is the part circled in green. It looks like a male outlet and most monitors have a male plug. So, presumably, I'd need some kind of splitter that would be one female (to fit the male outlet) that splits into to female (to fit the two male monitor plugs)? I can't find those anywhere... am I just dumb?

Or is that not a monitor outlet at all but something else altogether?

---

### Post by aysiu on 2006-01-22
Actually, my original post was wrong.

I was at work when I posted that, and my work computer had that (I seemed to have remembered my home computer having the same thing, but I guess not).

My home computer's Windows video settings look like this (see attached screenshot). Is that a bad sign?

---

### Post by aysiu on 2006-02-01
Okay, I'm revisiting this dual-display idea.

Assuming that what NVidia has to say [here](http://www.nvidia.com/page/geforce4mx.html) about my video card (most of which I've quoted below), what would you say my odds are of having dual display support? Sounds good, right? I just want to double-check.

Okay, and then if that's good, do I just get a splitter cord like [this one](http://www.amazon.com/gp/product/B000234MHC/sr=1-1/qid=1138771324/ref=pd_bbs_1/103-3639379-0351817?%5Fencoding=UTF8) and plug the two monitors in? Forgive me, but I have very little experience with this.

If that's it, then... I would install the NVidia drivers and then configure it through that somehow? Or *sudo dpkg-reconfigure xserver-xorg*?

[quote=NVidia]With the GeForce4 MX and GeForce MX 4000 graphics processing units (GPUs), NVIDIA provides a new level of cost-effective, high-performance graphics to the value PC user.

With their incomparable NVIDIA® nView&#8482; multi-display technology, Lightspeed Memory Architecture II, and Acccuview Antialiasing&#8482; technology, the GeForce4 MX and GeForce MX 4000 GPUs deliver feature-rich graphics technology, performance, and flexibility.

**	nView Display Technology**
	The nView hardware and software technology combination delivers maximum flexibility for multi-display options, and provides unprecedented end-user control of the desktop experience. nView allows end-users to select any combination of multiple displays, including digital flat panels, analog CRTs, and TVs, and to modify the display properties using an intuitive software interface.

**	AGP 8X**
	Provides double the bandwidth of AGP 4X&#8212;2.1GB/sec. vs. 1.1GB/sec. AGP 8X enables more complex models and detailed textures, creating richer and more lifelike environments. Uninterrupted data flow allows for smoother video streaming and faster, more seamless gameplay.

**	Accuview Antialiasing (AA)**
	The Accuview Antialiasing subsystem with advanced multisampling hardware delivers full-scene antialiased quality at performance levels never before seen.

**	Lightspeed Memory Architecture (LMA) II**
	LMA II boosts effective memory bandwidth by up to 300%. Radical new technologies&#8213;including Z-occlusion culling, fast Z-clear, and auto pre-charge&#8213;effectively multiply the memory bandwidth to ensure fluid frame rates for the latest 3D and 2D games and applications.[/quote]

---

### Post by robinl on 2006-02-01
[QUOTE=aysiu]Hey, WildTangent. Thanks for answering. Please treat me like a total newbie, because as far as hardware goes, I *am* one.

Okay, what it says on my computer is **NVidia GeForce4 MX Graphics.**

I've also attached a picture of the back slot of my computer that has me even thinking about a dual display (the picture circled in red).

What has me confused, though, is the part circled in green. It looks like a male outlet and most monitors have a male plug. So, presumably, I'd need some kind of splitter that would be one female (to fit the male outlet) that splits into to female (to fit the two male monitor plugs)? I can't find those anywhere... am I just dumb?

Or is that not a monitor outlet at all but something else altogether?[/QUOTE]

That should be a serial/RS232 port. And by the position of your VGA port, I am pretty sure that you are using intergrated graphics, probably NForce 2. I have yet to  see an intergrated graphics that support dual display alone (ie. without any other card). So basically, dual display is a no-no. Although you could get some cheap graphic card and put it in - you should have an AGP slot, unless it's one of those budget boards.

---

### Post by frodon on 2006-02-01
**aysiu**, you will find all the needed informations about dual monitor display here, this guide is really well written, not for ubuntu but there isn't a lot of things to change : [http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

---

### Post by BLTicklemonster on 2006-02-01
I have a couple of 17 inch monitors that I'd like to attempt using together, so I'm very interested in this. I have an ati 9200 se that has a normal monitor outlet on the back, plus another rectangular outlet that I recognize from having installed an evga card before. I wonder if this card would support dual display. Not that I would use an ati for linux, but I am going to be purchasing an nvidia soon, and I want to have the option to try dual displays. Seeing that my board only has one agp slot, it would appear that one would be able to purchase an agp video card that would work two monitors at the same time, right? (prolly will just ask the dude at the store, but I'm going to follow this thread, too)

---

### Post by aysiu on 2006-02-02
Wow. Somehow I didn't even realize people were still tuning into this thread. I was off doing my own internet research. So, yeah, I realized that a splitter cable will basically just present two of the same screen and that I need another video card.

[quote=robinl]That should be a serial/RS232 port. And by the position of your VGA port, I am pretty sure that you are using intergrated graphics, probably NForce 2. I have yet to see an intergrated graphics that support dual display alone (ie. without any other card). So basically, dual display is a no-no. Although you could get some cheap graphic card and put it in - you should have an AGP slot, unless it's one of those budget boards.[/quote] I'm not sure what AGP is, exactly. I do have an old extra video card from our five-year-old (no longer in use) computer. Can I just put that in?

[QUOTE=frodon]**aysiu**, you will find all the needed informations about dual monitor display here, this guide is really well written, not for ubuntu but there isn't a lot of things to change : [http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)[/QUOTE] This will definitely come in handy once I get the hardware part figured out. Thanks.

---

