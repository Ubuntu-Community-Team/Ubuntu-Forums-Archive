---
title: "Visual Effects : Help needed ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000]"
date: 2008-07-02
forum: Multimedia Software
---

### Post by koidenouvo on 2008-07-02
Hi,

I spent last evening and the whole day today trying to configure the what I think is a powerfull video card ATI RV250 to work with visual effects. From my understanding, there are 2 ways and which are from my experience at this point 2 theories :

1° is to install a free code source driver -I have tried all steps explained in a thread on ubuntu it didn't work; I would favour this solution but I have been spending 3/4th of my time since yesterday working around this;

2° is to install a proprietary driver from this process :

[http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts]("http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts")

, I have tried that, it didn't work and did quite mess up the system (keyboard, screen resolution...)

I had to reinstall. To make things more stable, I have formated home folder too so any thing about previous video driver would not bring confusion...

I am running Ubuntu Hardy Heron on a_ Compaq with 512 MB of Ram_. I seek Visual Effects for the fun  (which from version 7.10 until now I never could enable but on a IBM T40...)  because I think this video card is capable of making it work - I have paid for that a computer and for this card. At this point this is not an issue as I have read, I can play with a few 3D games(maybe with some more RAM) from the Windows world on Ubuntu independant from Visual Effects enabled or not - here I am willing to purchase one of these games and see what this video card is up to. Could someone confirm me about this(Visual effect might not work but strong Microsoft Windows plateforms graphic games might)? 

My post here is to have the exact process **to enable Compiz Visual Effects on a Compaq with ATI RV 250** ...if someone has done it and seen it work on a similar configuration. Compaq X1000 users like me who did follow thread with IBM with ATI cards might have been confused, this related post said it would be a bit of a journey, I think they found their way but except one or two, most X1000 users were left half way!

My xorg conf file is new from install ... 
[B]
Section "Device"
	Identifier	"Configured Video Device" 
EndSection[/B]

and at the time I am writting Ubuntu is running fine (keyboard, mouse...) which was far from being the case since this morning!

Thanks if you can help me,

Pascal

Are there any online courses to understanding Ubuntu/Linux programming concepts...database, connecting devices?

---

### Post by markbuntu on 2008-07-02
As far as I know, the ATI proprietary driver does not support the 9000 series cards because full support is now available with the open source drivers. Read this:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

---

### Post by koidenouvo on 2008-07-02
From this site, I understand there is no alternative and this graphic card is useless within Ubuntu, is it useless for Desktop Effects or for more demanding stuff, e.g 3d video graphic games?

---

### Post by koidenouvo on 2008-07-03
So, I guess I can only resign from enabling visual effects.
In any case, Ubuntu is something great and the fact that it's easier and working better in every new release makes decoration tools something not essential enough to appreciate the operating system as a whole!

---

### Post by Rocket2DMn on 2008-07-03
You can enable compiz/effects, see here - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by koidenouvo on 2008-07-09
Hi mate,

It just doesn't work following the thread you sent me. I think I'll buy my next comp with a video card that will fully work with Ubuntu features.

Thanks anyway,

Pcb

---

### Post by Rocket2DMn on 2008-07-09
At any point did you try to install the restricted drivers?  If so, how?  We can troubleshoot the problem if you'd like.

---

### Post by koidenouvo on 2008-07-09
Hi Rocket2DMn,
I did not try to install the restricted drivers, with so many command lines, I thought the installation would be part of the process at one point or another...
I'm not sure of how to install these restricted drivers because last time i did, it really really turned my desktop graphics inside out not talking about mouse and keyboard layout...

Give me a clue if you can on how to proceed with installing a restricted driver for ATI V250 and things to avoid.
[U]
Basic questions[/U]:
[LIST]
[*]Are restricted and propriatary drivers the same thing?
[*]Is fglrx a driver?
[*]What is currently the driver now in my config? Is it an open source driver? I guess it is but there is one that is said to install for other ATI when you don't choose a propriatary driver?
[/LIST]
Hope my questions are not too confusing, nor boring. Just to understand the very basic.

Thanks if you can help on this "accessory thing",

Kdn

---

### Post by Rocket2DMn on 2008-07-09
restricted drivers = proprietary drivers = binary drivers
fglrx is the restricted ATI driver.
Your config doesn't show a driver b/c that is how the newer version of X works.  By default, you are using the open source "ati" aka "radeon" driver.

DO NOT install the restricted drivers, the Radeon 9000s are too old to be supported by them, we are limited to the open source drivers.

So with all that being said, what exactly IS the problem you are having?

---

### Post by koidenouvo on 2008-07-09
Your reply : "At any point did you try to install the restricted drivers? If so, how? We can troubleshoot the problem if you'd like"

I understand I should install the restricted driver and go ahead with the thread about that ATI V250...

But you last wrote : "DO NOT install the restricted drivers, the Radeon 9000s are too old to be supported by them, we are limited to the open source drivers."

What should I do? to install or not to install restricted drivers?

---

### Post by Rocket2DMn on 2008-07-09
The latter - don't install the restricted driver.  MOST people use those, bug our cards (the Radeon 9000) are too old to be supported.  Radeon 9500 is the oldest card that is supported by fglrx.

I have my Mobility Radeon 9000 working just fine on my laptop, and can run compiz with the workaround I posted a link to earlier.  That means that after you install Ubuntu, you are finished dealing with graphics stuff unless you do the workaround for enabling compiz (which is easy).  You don't want restricted drivers.

So now as I understand it, you should be good to go unless something is messed up, like your screen resolution isn't right, or it's glitchy, or something else is quite obviously not how it should be.

---

