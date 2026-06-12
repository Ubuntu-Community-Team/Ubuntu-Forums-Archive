---
title: "What is wrong with vlc?"
date: 2008-12-17
forum: Multimedia Software
---

### Post by jay li on 2008-12-17
I'm trying to play some video clip in flv format, but I get this weird error: 

"[COLOR="Red"]No suitable decoder module[/COLOR]:
[COLOR="Blue"]VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this[/COLOR]."

Well I tried to play another flv file and vlc play it normally. 
I thought if I'll install win32codecs and libmp4v2 it will solve my problem but no luck. 

BTW only totem can deal with it, not the greatest vlc nor the legendary mplyaer.

---

### Post by khelben1979 on 2008-12-17
Have you tried the [GodLikeMouse]("http://glm-flv.sourceforge.net/") player?

---

### Post by jay li on 2008-12-17
No, and I'm checking the link you just gave me.
Thanks.

---

### Post by binbash on 2008-12-17
[https://trac.videolan.org/vlc/ticket/762](https://trac.videolan.org/vlc/ticket/762)

---

### Post by jay li on 2008-12-17
Thanks binbash, but I get "Secure Connection Failed". 
I think that's the first result from google that I tried and unfortunately the only one that meet my problem.

---

### Post by khelben1979 on 2008-12-17
Try [this one]("http://trac.videolan.org/vlc/ticket/762") instead.

Worked for me. (changed https to just http)

---

### Post by jay li on 2008-12-17
Hi khelben1979 thanks for the link.
Well I check that link but not quite understand what I'm suppose to do with it. 
If you meant by downloading the flv file and check it, well I just did and vlc play it well. 
I guess all my problem is apparently with a specific flv file. 
But the question is why it's happening from the first place. 
I mean, if totem could do it why not vlc, as I expect from a powerful multimedia player like vlc.

BTW my vlc version is 0.9.4

---

### Post by khelben1979 on 2008-12-18
Okay.

According to the latest version of the VLC player (0.9.8a), [these video formats]("http://www.videolan.org/vlc/features.html") are supported. From what I can see in the list, the flv format should be supported by the VLC player. 

So you could try installing the latest version to see if it works better.

---

### Post by jay li on 2008-12-19
According to "[COLOR="Blue"]_*[vlc downloads documentation page]("http://www.videolan.org/vlc/download-ubuntu.html")*_[/COLOR]", I have to make sure "multiverse" repository is activated (and it is) to get the most latest version of vlc. 
But last time I checked synaptic, vlc comes only with 0.9.4 version. 
I also tried search deb file of vlc 0.9.8a but found nothing. 
Any ideas?

---

### Post by khelben1979 on 2008-12-19
I don't know. 

But you could try to download the source from freshmeat.net. You'll see the link [here]("http://freshmeat.net/projects/vlc/").

---

### Post by jay li on 2008-12-19
Source code is beyond my knowledge, too complicated for me. 
No other way to update vlc?

---

### Post by khelben1979 on 2008-12-19
None that I'm aware of.

---

### Post by jay li on 2008-12-19
khelben1979 it was pleasure to chat with you. 
Thank you for your help.

---

### Post by khelben1979 on 2008-12-20
Yes. :popcorn:

If you're interested in getting the source and trying to get it to work anyway, one usually needs to go through these steps if you're interested:

First unpack the archive.
Then do this inside the path of the unpacked archive:

./configure
make
make install

Then VLC should be installed in the /usr/bin or /usr/local/bin path. (Sometimes the steps above don't work for some applications, but for most applications it works.)

---

### Post by jay li on 2008-12-20
Hi khelben1979, 
Glad you ask me that, but let me ask you something. 
In case I'll go for it what will happen to the old vlc?

Thanks.

---

### Post by mc4man on 2008-12-20
> In case I'll go for it what will happen to the old vlc?
If your going to run a 'sudo make install' after building than you'll need to uninstall your current version first.
If you wanted to remove the built version later you need to keep the build folder so you can cd to it and then run a 'sudo make uninstall.

You don't have to install your built version to use or test (leaving your current version installed

You would just cd to the folder and run ./vlc, or browse inside the folder and d. click on the the vlc exec. You can also make a desktop launcher or new menu item. In other words you can use to the same extent as if you had installed it.

---

### Post by jay li on 2008-12-20
Hi mc4man, 
Forgive me to newbie like me, the last part of your answer I understand, but not the first part and the middle. If you can explain your post I will appreciate that. 

Thanks.

---

### Post by mc4man on 2008-12-20
Well the typical (and with vlc) way to build would be to
 run a configure, (./configure
and then compile the source, ( make
Then install it (sudo make install

On the other hand after running the make the app is functional and can be run without installing, 

Ex.
I run a configure and make on vlc 0.9.8a, then to run without installing I'd cd to the build folder & run vlc

doug@doug-desktop:~/vlc-0.9.8a$ ./vlc

Or I'd make a launcher like in screen and put it on the desktop or top or bottom panel.


For instance on 8.04 because I'm not totally thrilled with vlc 0.9.x I have keep 0.8.6 installed and run 0.9.8a and a recent 1.0 unstable from their build folders, waiting to see if some of the regressions and or bugs are fixed.

---

### Post by jay li on 2008-12-20
So if I get you right I can keep both vlc and none of them interfere one another.

---

### Post by mc4man on 2008-12-20
> So if I get you right I can keep both vlc and none of them interfere one another.

AS long as only one or none are installed, I've had up to 4 versions or variations of versions available at once.

All 0.9.x versions use a config in ~/.config/vlc so your option changes will extend to all. The only thing you'll notice is when switching from one 0.9.x ver. to another it will take about 10 sec to open vs. immediatelly when reopening the same ver.

As an aside I'm starting to think that atm a current mplayer with smplayer frontend when needed is a better choice for video.

---

### Post by jay li on 2008-12-20
Ok, I downloaded the tarball of vlc 0.9.8a to my desktop. 
What is the next step?

---

### Post by mc4man on 2008-12-20
> What is the next step

Well it's not quite as simple as 1,2,3 even for a simple vanilla  config.

I'm assuming your using 8.10, if not say so before doing below.

So I could help you do a decent first build and you can take it from there as far as educating yourself to extent you want.

A few things to get out of the way.

Most of your build-deps are going to be acquired from an apt-get command. In 8.10 all the packages you install from build-dep, (a LOT), will be marked as auto installed. 
What this means is that they will also be marked for auto removal. The upside of this is if you decide you don't want to do any further compiling you can remove everything that was installed by running apt-get autoremove.

The downside is if you wish to keep building then the autoremove feature is made worthless, there's no differentiating in apt between packages you need for compiling and junk that's not needed.

So first add medibuntu to your sources if not already.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Add the repo and then the key. then ...

For marking build-deps for autoremoval

```
sudo apt-get build-dep vlc
```

for keeping them out of auto removal

```
sudo apt-get -o APT::Get::Build-Dep-Automatic=false build-dep vlc
```

Before you type y to install, please copy all the package names from the terminal and save in a text file so you can post for me.


Then get back and post that list of installed build-deps

---

### Post by meka4996 on 2009-05-23
Try this one...
[http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)

---

