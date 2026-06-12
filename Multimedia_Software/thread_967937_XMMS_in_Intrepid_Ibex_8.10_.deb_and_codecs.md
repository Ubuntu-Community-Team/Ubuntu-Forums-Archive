---
title: "XMMS in Intrepid Ibex 8.10: .deb and codecs"
date: 2008-11-02
forum: Multimedia Software
---

### Post by guayusa on 2008-11-02
**UPDATE for JAUNTY:**

[http://colonos.wordpress.com/2009/04/27/xmms-in-jaunty-jackalope-904-how-to-install-with-codecs/]("http://colonos.wordpress.com/2009/04/27/xmms-in-jaunty-jackalope-904-how-to-install-with-codecs/")

================================================================================================
================================================================================================

Since Feisty XMMS has been missing from the repos.

That is a problem, because XMMS is still the preferred music player for many. One reason for this is that XMMS can handle very large collection in a single play list, where other, so-called sophisticated database oriented players, like Rhythmbox, Amarok or Banshee, simply cannot handle very large collections. 

In other words, in a time of enormous networking and sharing the only player that is up for the job has been left out of the *buntu distros - and the reason, so the learned technicians tell us, is that it is outdated!

However, you can't just throw out a tool that is outdated unless you have a proper replacement, now can you? The commotion around XMMS really casts doubt on the democratic nature of Free Software and does not look promising with regards to the powers of end-users.

Thankfully there are solutions (.deb and extra codecs) and they are collected here:
[http://colonos.wordpress.com/2008/11/02/xmms-in-intrepid-all-you-need-in-a-zip-file/](http://colonos.wordpress.com/2008/11/02/xmms-in-intrepid-all-you-need-in-a-zip-file/)

[RIGHT]Have fun with XMMS - still the one and only!
:guitar:[/RIGHT]

---

### Post by guayusa on 2008-11-12
More than two hundred people have followed links provided in the blog to get to XMMS for Intrepid and the interest is not fading yet, according to Wordpress statistics. Several have explicitly thanked me for pulling the bits together.

Perhaps we should start a serious petition to get XMMS "fully codecs packaged" back into the repositories?!?

You cannot just ignore hundreds of people - can you?

---

### Post by guayusa on 2008-11-14
The XMMS in GNU/Linux Manifesto v.0.1 is posted here:
[http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/](http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/)

...with complete, I think, Ubuntu specific information on how to best get XMMS up and running at the end.

[RIGHT]***Happy Listening***

:guitar:[/RIGHT]

---

### Post by venerix on 2008-11-15
thanks bro...

---

### Post by guayusa on 2008-11-28
Ubuntu specific information on how to best get XMMS up and running - from:
[http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/](http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/)

First go to KnutA’s site:
[http://www.pvv.ntnu.no/~knuta/xmms/](http://www.pvv.ntnu.no/~knuta/xmms/)

…where he kindly hosts an XMMS repository that allows you to add it to your apt-get system and it will pull the dependencies. Set up for Lenny, Hardy and Intrepid (which is just a copy of the Hardy repo, but it works). If you don’t know how to add a third-party software source (or repository) then look here.

That should be your first step. Install XMMS that way:

sudo apt-get install xmms (or search in Synaptic).

Then you have to add various encoding and decoding tools if you need them.

Pulseaudio, the new system: [http://0pointer.de/lennart/projects/xmms-pulse/](http://0pointer.de/lennart/projects/xmms-pulse/)

I do not use that. Choosing ALSA as output in XMMS works better for me. With Pulseaudio there were funny issues with other channels, losing sound for a half a second every now and then.

There is still an mp4 .deb here, which also works in Intrepid:
[https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1](https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1)

To get FLAC follow the second part of this how-to (you don’t need to compile XMMS as outlined in the first part of the how-to, since you can get the .deb with apt-get from KnutA):
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

More relevant compile info here:
[http://blog.xanda.org/?p=436](http://blog.xanda.org/?p=436)

You might also want .wma (but much better is to convert your files), but if you need it, then you have to compile it (or google for an .rpm and use alien to convert it):
[http://mcmcc.bat.ru/xmms-wma/](http://mcmcc.bat.ru/xmms-wma/)

More relevant information here: [http://ubuntuforums.org/archive/index.php/t-21414.html](http://ubuntuforums.org/archive/index.php/t-21414.html)

However, if you trust me you can also just download this file, Plugins.tar.gz and unzip to your:

/home/user/.xmms/Plugins folder (shut down XMMS, of course, for good measure):

That file contains the Flac and .wma plugins that should work in Intrepid and possibly Hardy, but why not go ahead and do it yourself, you might just learn something in the process?! :)

Maybe you also need Shorten (shn) for XMMS: [http://www.etree.org/shnutils/xmms-shn/](http://www.etree.org/shnutils/xmms-shn/)

- about which you can find useful information here:

[http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)

Anything else that anyone’s uses or maintains?

If you have a virtual machine or an extra box to play around with it might be a good idea to compile your things somewhere else then your production system, but a similar environment, since it most likely will send you in dependency hell, chasing packages discerned from compiler output and with the aid of the higher spirits of telepathy. I just couldn’t be bothered to keep track of them. I know, I should have extracted it from the Apt logs and and and …

Anyway, in the end you have a system with a load of stuff that you don’t need and I ended up doing a fresh install, but I mostly do that when a new distro comes out, - first install it to check it out, stress it and try different things, before settling for a plan for the final, hopefully, install. NOTE: If you do it this way do remember to use checkinstall, which generates .debs that you can use the second time around. That is also how you should do it in a virtual or other machine, so that you can transfer it to your favourite stable machine where you just want to play music while you work on something else.

---

### Post by Intangir on 2009-03-19
they need to readd xmms

i mean whats so out of date about it? should we add a new line or two to some source in there so we can say its updated ;)

its still the best by far
it can handle video and audio on its playlist too and launch either
it plays all the streams ive ever wanted

there is nothing else ive tried that is near as good, flexible, stable

thanks for this thread..

---

### Post by guayusa on 2009-04-28
UPDATE for JAUNTY:

[http://colonos.wordpress.com/2009/04/27/xmms-in-jaunty-jackalope-904-how-to-install-with-codecs/]("http://colonos.wordpress.com/2009/04/27/xmms-in-jaunty-jackalope-904-how-to-install-with-codecs/")

[RIGHT]:guitar:[/RIGHT]

---

