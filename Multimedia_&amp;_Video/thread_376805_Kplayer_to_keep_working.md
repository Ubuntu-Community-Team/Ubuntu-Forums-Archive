---
title: "Kplayer to keep working?"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by miggols99 on 2007-03-05
I tried installing Kplayer 0.6 to play music from my samba network. I got it working with my music, but when I try to do something with the updater or Adept, they say that Kplayer is broken! I think that the dependencies are out of date. Can someone help me? Thanks in advance.

---

### Post by panch0 on 2007-03-05
Right now KPlayer is not in Ubuntu repositories, so if you want to update to the new KPlayer 0.6.1, probably the best thing is to install the package from the [home page]("http://kplayer.sourceforge.net/") manually, or add an extra repository like the home page says.

---

### Post by miggols99 on 2007-03-06
Ok I tried installing from the deb file, but it still has the same problem. Which repositories are they? The ones under Debian?

---

### Post by panch0 on 2007-03-07
Yes, those are Debian unstable packages, roughly the same as Feisty.

I think you can ignore the KPlayer dependency problems, it can work fine with the older versions.

If/when you upgrade to Feisty, Adept won't show any problems anymore.

---

### Post by miggols99 on 2007-03-07
When I try to do something in Adept with Kplayer installed, it will try and delete Kplayer. It's not really a big problem, so I guess I could wait for Feisty...but do you know of any other players that don't crash when you try and play networked files? I could use one of them until then.

---

### Post by panch0 on 2007-03-09
KPlayer is really the best. I think what many people do right now is just add some Feisty repositories and install newer versions of some packages like Qt, just to keep Adept happy with KPlayer.

---

### Post by mocha on 2007-03-10
How do you install KPlayer in Edgy?  The deb package on their website complains about a few libraries that need to be updated.  I don't want to add the Debian repository and screw up my system.

---

### Post by miggols99 on 2007-03-10
So what are these repositories? Could you list them? I really like Kplayer with playlists and everything :)

---

### Post by mocha on 2007-03-10
I don't understand what you are asking.  I was just saying that I use Edgy and the deb package on the KPlayer homepage installs on my system but then complains about some libraries not being the proper version.  Everytime I update the system KPlayer is shown as broken and gets uninstalled.

I **don't** want to use the KPlayer homepage installation procedure for Debian since it requires adding Debian repositories and from past experience I know that adding another repository is asking for a major disaster.

---

### Post by miggols99 on 2007-03-10
I mean the Feisty packages.

---

### Post by panch0 on 2007-03-12
You don't need Debian repositories, you need the Feisty ones.

The easiest thing is to just take the ones you have for Edgy, replace "edgy" with "feisty" and add those.

Then install newer versions of the packages Adept is complaining about.

---

### Post by mocha on 2007-03-12
OK, that's easy enough, but do I just keep using the Feisty repositories then for daily usage?  If I have both the Edgy and Feisty repositories enabled at the same time, won't the Feisty packages always be more updated anyway?  Does this screw up the system in anyway?  Should I just go ahead and do a dist-upgrade now?

---

### Post by panch0 on 2007-03-13
You shouldn't need to dist-upgrade unless you want to. You can keep Egdy as the primary repos if you want to, look through the Adept settings for that. Or else just download the Feisty .deb packages and install them manually with dpkg -i.

---

### Post by miggols99 on 2007-03-13
I tried adding the Feisty repositories, but then adept said it could update around 700 packages! I only want to upgrade the packages I need.

---

### Post by panch0 on 2007-03-14
To update just the required packages try this (as root):

```
wget http://archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/libfontconfig1_2.4.2-1ubuntu1_i386.deb
dpkg -i libfontconfig1_2.4.2-1ubuntu1_i386.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.15~beta5-1_i386.deb
dpkg -i libpng12-0_1.2.15~beta5-1_i386.deb
wget http://archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8-0ubuntu1_i386.deb
dpkg -i libqt3-mt_3.3.8-0ubuntu1_i386.deb
```

If it complains about other packages, do the same for those too.

---

### Post by miggols99 on 2007-03-14
I fixed it now! Thank you for helping me. I actually did it the hard way by downloading the packages from the Ubuntu package area. I could have done it that way, it would have been much easier!

---

### Post by mocha on 2007-03-15
miggols99,

Do you mind posting exactly how you got KPlayer installed?  I installed the deb file from their website and then attempted to try the suggestion from panch0, but after I downloaded and installed the libfontconfig1 it totally buggered up the packages listed in Apt and I had to use aptitude to correct everything in order again.  I'm using Edgy by the way.  Thanks.

---

### Post by miggols99 on 2007-03-16
Well actually, it worked fine, but Adept started complaining again and wanted to downgrade the packages I just upgraded! What I did was download the packages manually from the packages.ubuntu.com website. It didn't take too long, but I don't think it should be that hard to install Kplayer! It solved the dependencies though. I guess that's a start.

---

### Post by taurean on 2007-03-16
I really have to say that until simple things such as this are sorted, Linux will continue to be an outcast OS compared to the not-so-cranky doze systems.

A hobby OS.

I mean, apt is such a great idea. Yet to install simple things its often a pain. I dont want 5 million KDE apps just because I want konquerer (since Firefox is about as good as a parachute under water). I dont want it to uninstall everything except the kernel because I want to uninstall something else.

I had aptitude warn me it was going to uninstall the kernel once, warned me how bad this was and I thought WTF ?  Thank gawd for ghost images.

Being FORCED one way or another, is a typical M$ tactic. But make it easy, don't make it compulsory.

I cant even use Audacity because it whines about stuff, and yet Sound Recorder works fine, and thats independent of my system sounds being enabled.

I cant play streaming video if it's mms, because the mplayer plugin is as crook as two dogs dieing. 

SIMPLE things, that make day to day use painful. 

Beryl ?  How can a thing work once then cause xserver to fail every time after I log in. Over and over with no error.. Just a log back out. C'mon..  

Last time I try anything groovy on nix.  Sure it teaches you a lot about how to fix things, but ffs...  

Sorry to hijack the thread, but really.. I'm about up to the top of my scorn with one little thing after the other. I'm not going to bother learning for the next 5 years when something else just works, even with all its flaws and rubbish instability. ;(

I came to this thread to see if this app might help, and now I wont bother, it seems its going to be more of a bloomin hassle than it's worth. So-long streaming video.. :(

Damnit.

---

### Post by mocha on 2007-03-16
Streaming video is not a problem, it's actually easier in Linux to look at Shoutcast TV using Tunapie and MPlayer.  There's no solution for that in Windows except for spyware laced AOL Winamp 5.  Actually I take that back, you can use VLC, but its Playlist preparsing totally sux.  I just wanted to get KPlayer installed cause I heard it supports bookmarks.  For now I'll just continue to use Streamtuner and Tunapie.

---

### Post by miggols99 on 2007-03-17
Oh well. I'll just wait until Feisty. But it's good to know that it will work. Soon anyway.

---

### Post by mocha on 2007-03-17
> **miggols99 said:**
> Oh well. I'll just wait until Feisty. But it's good to know that it will work. Soon anyway.

Huh?

I thought you were able to get it installed by manually upgrading all your packages?

---

### Post by miggols99 on 2007-03-18
> Huh?

I thought you were able to get it installed by manually upgrading all your packages?
It mostly worked but other programs that depended on the packages I upgraded didn't like it. So I'm stuck.

---

