---
title: "DEVEDE - No sound on finished DVDs"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by Goodson1974 on 2007-11-22
Hi all
 
I've found that when i convert an avi to an iso in Devede and burn it to DVD, there is no sound when i play it in my DVD player.
 
This has only happended since installing Gutsy and Devede worked perfectly in Feisty.
 
The weird thing is, that there will be sound when i play the DVD in the DVD drive of my PC, but when i play it in my DVD player, there's no sound at all!
 
Has anyone got any ideas as to why this is happening?
 
I thought that it might be an mplayer or mencoder problem, but both of these packages upgraded from the repositories last night, so i assumed that the problem would be fixed, but sadly it wasn't.

---

### Post by mtgo29 on 2007-11-23
Try this: install "[COLOR="DarkOrange"]libtwolame0[/COLOR]" ( fron synaptic manager) then System-Administration-Software Sources-Click on [COLOR="DarkOrange"]Updates[/COLOR] then put a [COLOR="DarkOrange"]tick[/COLOR] in the [COLOR="DarkOrange"]Unsupported updates (gutsy-backports)[/COLOR] you will receive some updates install then try _Devede._
Works fantastic with sound output excellent.:guitar: check this link:[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by MGStreak on 2007-11-23
I have the same problem, and am about to try the suggestion from mtgo29... I'm leaving my laptop on overnight to convert/make an .iso, I'll try and burn it tomorrow, and we'll see how things go...

EDIT:
Also, just to save people the time, here is the info from the links mtgo29 specified (direct from the DeVeDe home page):

> Note for Ubuntu Feisty users: currently (as April 20, 2007), the Mplayer/Mencoder version in Ubuntu Feisty is buggy and produces noisy sound when used with DeVeDe. While the maintainer doesn't fix it, you can use the package with the previous version, available in the Download section).

Note for Ubuntu Gutsy users: by default (as November 21, 2007) Gutsy comes with Mplayer/Mencoder buggy version 1.0RC1 (like Feisty); but fortunately there's the version 1.0rc2 avaiblable in the backports repository, which fixes the sound bug. To install it, just go to System->Admin->Software repositories and activate the Backports source.


EDIT #2:
Having tried to do all the above steps, I have concluded that my problem is that the repositories are only up to version 2.13, whereas the DeVeDe website shows the current version as being 3.4!!!  I have *no* idea why the repositories are so far behind, but I imagine that once I upgrade DeVeDe, all will be solved.  Also, I found that I already had the Gutsy Backports repository enabled, so I was already using the 1.0RC2 version of Mplayer/Mencoder!

EDIT #3:
Here is a link to a .deb for version 3.3 of DeVeDe, for those who wish to be a little more adventurous (like me!):
[http://www.getdeb.net/release.php?id=1712](http://www.getdeb.net/release.php?id=1712)

---

### Post by Goodson1974 on 2007-11-24
I've just tried the backport solution and converted some avi's and burnt them to a DVD, but unfortunately there is still no sound when I play it in my DVD player :(

---

### Post by MGStreak on 2007-11-27
> **Goodson1974 said:**
> I've just tried the backport solution and converted some avi's and burnt them to a DVD, but unfortunately there is still no sound when I play it in my DVD player :(

So I tried the backport solution AND I tried to burn a DVD after updating to a newer version of DeVeDe (3.3) as I mentioned in my last post.  After converting/burning a DVD, the problem remains.

Anyone have any ideas?

---

### Post by curiousnoob on 2007-11-29
Bump.  
I am also having the exact same problem.  

Worked on Fiesty but not on Ubuntu.
I also have downloaded the Back Port updates with no fixes.

---

### Post by mtgo29 on 2007-12-03
> **Goodson1974 said:**
> I've just tried the backport solution and converted some avi's and burnt them to a DVD, but unfortunately there is still no sound when I play it in my DVD player :(

Hi what version Devede are you using? The version I'm using is 12.13 as of Gutsy 7.10 installed from synaptic package manager. I use the backport option and created an iso and tested with K3b & Gnome Baker to burn the files and had no sound problem. I played the dvd and cd on my dvdplayer with no sound problem. [COLOR="Lime"]Make sure to install [/COLOR][COLOR="Red"](libtwolame0)[/COLOR] from synaptic manager before doing the backport option.
Hope this helps everyone.:)

[COLOR="Red"]Re[/COLOR]: my previous post-Try this: install[COLOR="DarkOrange"] "libtwolame0"[/COLOR] ( from synaptic manager) then [COLOR="DarkOrange"]System-Administration-Software[/COLOR] [COLOR="DarkOrange"]Sources[/COLOR]-Click on Updates then put a tick in the Unsupported 
updates (gutsy-backports) you will receive some updates install then try Devede.
Works fantastic with sound output excellent. check this link:[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)


Just a keen Linux learner not expert but getting there

Ubuntu user #15804
Ubuntu Gutsy 7.10

---

### Post by MikeRussell on 2007-12-11
Hey all,

    I am having the same problem on Kubuntu 7.10...  I have enabled backports and am using mplayer version 1.0-rc2 (as suggested by the devede homepage) along with the 3.3 version of devede.  I can play my newly burnt dvds fine on my computer, but they lack sound when played on my standalone dvd player.  Any suggestions would be hugely appreciated.  Thanks!

Mike

---

### Post by Goodson1974 on 2007-12-12
I've just found out that my DVD player can play avi files directly from CDs or DVDs, so this isn't a problem for me anymore.
 
Has anyone else discovered this?  I don't know if it's something that most modern DVD players can do.
 
I'm still interested in getting it fixed though, as my family sometimes need things converted to DVD and i wouldn't want to disappoint them!

---

### Post by gigaferz on 2007-12-31
hello, in feisty i had devede installed and never gave any problems, now in gutsy  is working fine too,

however I just realized im missing the option to put a menu ,because I have an old version 2.13 (from synaptic). Also I think  the videoCD option doesnt work at all.

 Did anybody here ever  get it working ?

by the way I found this...

[http://www.my-guides.net/en/content/view/75/](http://www.my-guides.net/en/content/view/75/)

---

### Post by Geekkit on 2007-12-31
Seems another reason to go back to Feisty. 7.10 is not ready for real use.  :(

---

