---
title: "xmms forever!"
date: 2008-05-15
forum: Multimedia Software
---

### Post by Intangir on 2008-05-15
[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

---

### Post by taxirick on 2008-05-15
Thanks for the post. I was wondering why XMMS got left out of the upgrade. It is my favorite for streaming media as it tackles just about anything with aplomb.
Rick

---

### Post by Lucky LIX on 2008-05-16
XMMS ftw =)

But how come I don't see anyone using the newer 1.2.11 version? Nothing new?

---

### Post by james_xxx on 2008-05-19
Bring back XMMS!!

We need to start a campaign.

XMMS definitely fills a niche. It is the best player there is for streaming media. It starts almost instantly, and kicks Audacious' **** (imho).
It is also very valuable for those wanting to configure minimalist systems.

I finally had to compile it, when i discovered (to my great dismay) that it was gone after upgrading my laptop and desktop both to Hardy, taking my awesome collection of skins along with it!

XMMS forever!

---

### Post by james_xxx on 2008-10-21
I still think we need to start a petition to have XMMS restored to the repos.

Peace.

---

### Post by cozmicharlie on 2008-10-21
I'm all for adding XMMS back.  Is it up to the Ubuntu developers or the XMMS program developers to get it back into Synaptic.

FYI - for anyone interested in installing xmms in Hardy (it also works in Intrepid) there is a great tutorial here ([http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)and](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)and) I beleive there are deb files that work also.

---

### Post by guayusa on 2008-11-02
All you need to run XMMS in Intrepid (and Hardy) can be found here:
[http://colonos.wordpress.com/2008/11/02/xmms-in-intrepid-all-you-need-in-a-zip-file/](http://colonos.wordpress.com/2008/11/02/xmms-in-intrepid-all-you-need-in-a-zip-file/)

NB: This is the new 1.2.11-1_i386.deb and there are codecs and how-tos linked to.

[RIGHT]:guitar:[/RIGHT]

---

### Post by guayusa on 2008-11-15
Check this out:
[http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/](http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/)

[CENTER]:guitar:[/CENTER]

Detailed info on getting XMMS up and running:

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

Maybe you also need: [http://www.etree.org/shnutils/xmms-shn/](http://www.etree.org/shnutils/xmms-shn/)

Anything else that anyone’s uses or maintains?

If you have a virtual machine or an extra box to play around with it might be a good idea to compile your things somewhere else then your production system, but a similar environment, since it most likely will send you in dependency hell, chasing packages discerned from compiler output and with the aid of the higher spirits of telepathy. I just couldn’t be bothered to keep track of them. I know, I should have extracted it from the Apt logs and and and …

Anyway, in the end you have a system with a load of stuff that you don’t need and I ended up doing a fresh install, but I mostly do that when a new distro comes out, - first install it to check it out, stress it and try different things, before settling for a plan for the final, hopefully, install. NOTE: If you do it this way do remember to use checkinstall, which generates .debs that you can use the second time around. That is also how you should do it in a virtual or other machine, so that you can transfer it to your favourite stable machine where you just want to play music while you work on something else.

---

### Post by cozmicharlie on 2008-11-17
> **guayusa said:**
> Check this out:
[http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/](http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/)

Detailed info on getting XMMS up and running:

Anything else that anyone&#8217;s uses or maintains?


This How To provides step by step instructions for setting up flac and shn support in xmms.  It is based on the method described on Sartak's blog. It works for both Hardy and Intrepid.
[HTML]http://ubuntuforums.org/showthread.php?t=833164&highlight=shn[/HTML]

---

### Post by guayusa on 2008-11-17
> **cozmicharlie said:**
> This How To provides step by step instructions for setting up flac and shn support in xmms.  It is based on the method described on Sartak's blog. It works for both Hardy and Intrepid.
[HTML]http://ubuntuforums.org/showthread.php?t=833164&highlight=shn[/HTML]

Great, however, those links are included in the text above already, so now we know for sure! :)

:guitar:

---

### Post by cozmicharlie on 2008-11-17
> **guayusa said:**
> Great, however, those links are included in the text above already, so now we know for sure! :)

:guitar:

Yes, I mainly added the link for the instructions on how to add shn.  You had the link to btree but the link does give instructions for loading the shn plug in and some people (maninly newbies) don't know how to install from source files. It used to be great when xmms was in synaptic but no longer.

Also, I forgot to thank you for putting all this info in one place.  This will really help people so thanks for taking your time to do this.

---

### Post by guayusa on 2008-11-17
Ahhh, yea, I see now. Well done.

I guess that it is pretty much all then!?!?!

However, we still need to bring this issue to the attention of the Ubuntu leaders - surely we can put pressure on them to return XMMS to where it belongs.

[http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/](http://colonos.wordpress.com/2008/11/13/the-xmms-in-gnulinux-manifesto-v01/)

---

### Post by hissyfut on 2009-02-02
had to compile this, just because. the eq and etc.

works great with wavpack and flac plugins.

btw this is off topic, but why in the heck is latest flac source compile end with error?

main.cpp: In function ‘int main(int, char**)’:
main.cpp:75: error: ‘memcmp’ was not declared in this scope
make[5]: *** [main.o] Error 1

Luckily the xmms plugin is built before this error and able to copy to xmms plugins

---

### Post by joron on 2009-02-15
I like / need xmms for flac and shn files, light weight too. I've used most everything else and nothing makes the final cut, some are pretty though...

 After upgrading from Fiesty to 8.10 and back to 8.04LTs. I've spent way to much time fixing xmms, nvidia driver issues, pulsaudio etc. I had xmms working and sounding great but it stopped working recently with the following error;
Gdk-ERROR **: BadMatch (invalid parameter attributes)
and a bunch of libgdk and libx11 errors.

I also had to remove pulseaudio as it was causing choppy audio in any player (vlc, Rhythmbox etc) with high cpu use.

I'll need to back track and figure out which upgrade(s)/installs broke it.

---

