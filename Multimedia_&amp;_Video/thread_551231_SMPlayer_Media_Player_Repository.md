---
title: "SMPlayer Media Player Repository"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by TheMono on 2007-09-14
[b]EDIT: WARNING! ANY PACKAGES INSTALLED THROUGH THIS METHOD ARE NOT OFFICIAL UBUNTU PACKAGES - MERELY BUILT WITH THE UBUNTU BUILD SYSTEM. PLEASE DO NOT FILE BUGS WITH THEM ON LAUNCHPAD - THEY ARE NOT SUPPORTED BY THE UBUNTU DEVELOPERS! 
If something goes wrong: PM me or post in this thread.[/b]

I've already announced this in a couple of threads that involved building debian packages for SMPlayer. However, as SMPlayer development has just moved over to Subversion, I thought I'd announce this in its own thread.

I'm maintaining an Ubuntu Repository through launchpad using the official Ubuntu build system for SMPlayer - see the following website for more information on the program:

[http://smplayer.sourceforge.net/en/index.php](http://smplayer.sourceforge.net/en/index.php)

The repository contains a daily sync from the SMPlayer SVN, and supports both feisty and gutsy. To use it, first use the command 

```
sudo nano /etc/apt/sources.list 
```

Enter your password, and you will be given a list of sources currently used for software. Add to this one of the following two lines, depending whether you use Gutsy or Hardy:

```
deb http://ppa.launchpad.net/themono/ubuntu gutsy main universe
```
```
deb http://ppa.launchpad.net/themono/ubuntu hardy main universe
```

Packages available for Feisty are: smplayer, smplayer-classic, and smplayer-themes
For Gutsy are: smplayer and smplayer-themes

Install these by running

```
sudo apt-get update
```

and then running

```
sudo apt-get install smplayer smplayer-themes
```

The themes package is not mandatory, but is recommended.

---

### Post by loell on 2007-09-14
hi, what are the recent changes in smplayer?

---

### Post by rvm4000 on 2007-09-15
The latest changes are in order to make it work in the SVN (display the revision number in the about dialog, create deb packages with the SVN revision in the filename and so on). But there's no new features yet.

---

### Post by TheMono on 2007-09-16
Sorry, I was a bit late in updating this morning - slept in! But new packages are being built now I'm home from work.

---

### Post by TheMono on 2007-09-21
After tomorrow morning's update, there will be a two day period where there will be no updates as I am out of town for a concert.

The 24th will see the next update after the 22nd.

---

### Post by dixon on 2007-09-23
Great work TheMono, thx. Is there also some repository for mplayer svn?

---

### Post by TheMono on 2007-09-24
OK, we're back and going.

dixon, I'm not doing mplayer svn at the moment, and I don't know anyone who is, but, having said that, I don't see any reason why I can't. I do compile it from SVN myself on occassion. The only reason I'm not sure is that I have no way of informing people that use my repo that I would be adding mplayer svn, and they may accidentally upgrade to it when they would rather have the stability of the Ubuntu packages.

---

### Post by rvm4000 on 2007-09-24
I'm afraid your packages display a wrong version number: *0.5.60+SVN-rget_svn_revision.sh* when it should display something like: *0.5.60+SVN-r80*

The script get_svn_revision.sh should be run before compilation (the Makefile does it automatically). That creates the file src/svn_revision.h with the right svn revision number.

---

### Post by TheMono on 2007-09-24
Yes, I know about this. I'm still trying to figure out how to fix this. The problem is that when I build the package on my PC, it works fine, but when the sources are uploaded to launchpad it doesn't seem to execute that script properly. I'm not sure why. If you have any ideas, I'm happy to fix it, but at the moment I figure it isn't the end of the world.

EDIT: Plus, you will note that my packages are actually at 0.5.61 rather than .60, this is because I uploaded packages with the wrong appending (DD/MM/YYYY), and so I needed to increment up in order to switch to YYYY/MM/DD - though from now I'm dropping the .60 completely in favour of 0.5+svn naming, as there aren't really nicely nameable point releases now.

I'm playing round with how to fix the version problem now. However, as I can't reproduce it on my computer it isn't easy.

---

### Post by disturbedite on 2007-09-26
smplayer-themes 0.1.12 has been out for a little while, just thought i'd give you a heads-up mono.

---

### Post by TheMono on 2007-09-27
Oh, thanks. Sorry, I missed it. I meant to add the svn themes and update it maybe once a week, but forgot lol. I'll have it up with tomorrows builds.

---

### Post by disturbedite on 2007-09-27
cool, thanks mono.

---

### Post by TheMono on 2007-09-27
Uploaded, should be present in ~20 minutes.

---

### Post by TheMono on 2007-09-28
Updates will be late today, the build system seems temporarily broken. The build computers don't seem to be connecting to the main repo's, and as such the chroot is failing.

---

### Post by TheMono on 2007-09-30
Should be good to go now. Sorry about that.

---

### Post by TheMono on 2007-10-01
I'm pretty sure that the current package is broken. Unfortunately, I can't manually remove it from launchpad. I'll try and get an old package re-upped over the top of this one. In the meantime, you should be able to select (in synaptic, at least) to force the version to smplayer 2:0.5+svn070930 - the last confirmed working. Or simply don't upgrade to smplayer 2:0.5+svn071001.

---

### Post by dixon on 2007-10-01
> **TheMono said:**
> OK, we're back and going.

dixon, I'm not doing mplayer svn at the moment, and I don't know anyone who is, but, having said that, I don't see any reason why I can't. I do compile it from SVN myself on occassion. The only reason I'm not sure is that I have no way of informing people that use my repo that I would be adding mplayer svn, and they may accidentally upgrade to it when they would rather have the stability of the Ubuntu packages.
I wanted the mplayer svn just because I've read somewhere, that the mplayer svn supports seeking in wmv streams. Is it true? If it's I'd be very gratefull if  u could post here the deb package if it's not a problem. THX in advance

---

### Post by TheMono on 2007-10-01
Sure, I can do that for you Dixon. On another note, smplayer 2:0.5+svn071002 is up now which should fix the problems in 071001.

---

### Post by gebeleizis on 2007-10-04
I am trying to update mplayer svn, with svn up or svn update and I got this:
> root@Medion-Asus:/media/sda5/temp/_nicu/Workspace/svn/mplayer# svn up
Skipped '.'
root@Medion-Asus:/media/sda5/temp/_nicu/Workspace/svn/mplayer# 

I searched about it, but it doesn't make much sense to me 'cause I am not that deep into compiling and stuff. So, if someone can help me, please do.
Thanks.

---

### Post by TheMono on 2007-10-06
gebeleizis, I'm sorry, I'm not sure what this is. I don't know enough about how subversion works.

Dixon, I sent you a PM a few days ago... did you get it?

---

### Post by TheMono on 2007-10-10
Tomorrow will be the last update for about four days as I will be away. Builds will be resumed Monday, New Zealand time.

---

### Post by TheMono on 2007-10-14
We're up again, though it seems that nothing has really changed in svn.

---

### Post by TheMono on 2007-10-18
Away again, will be back updating soon. Promise this is the last time I'll be away for a while ;)

---

### Post by TheMono on 2007-11-07
Support for Feisty is going to be dropped soon, and support for Hardy will be picked up later in the dev cycle - at the moment, if you are running hardy, you are the sort of person who compiles it yourself anyway...

---

### Post by TheMono on 2007-11-15
Today is the last build for Feisty - time to roll over to gutsy & hardy.

---

