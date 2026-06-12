---
title: "iTunes replacement"
date: 2010-04-06
forum: Multimedia Software
---

### Post by temporos on 2010-04-06
For several months, I've been running Ubuntu 9.10 (Karmic) on two of my computers.  I've been using them almost exclusively.  The remaining machine still has Windows xp SP3 on it.  The only reason I even boot Windows on it is because I *need* iTunes functionality.  I'd *really* like to use iTunes in Ubuntu so I can finally switch completely.

I've run into problems, though.  I own a new iPod Touch (I had to replace my old, broken iPod, and the iTouch was the only decent MP3 player at the time).  I've used iTunes for years to manage my music library.  I have play counts, "smart" playlists, applications and "protected" (m4p) music purchased through the iTunes store.  I would love to dump iTunes entirely and switch to something natively Linux.

I need a Linux alternative that is capable of performing the following:

[LIST]
[*]sync music, movies, pictures, applications, and playlists to my iTouch
[*]connect to the iTunes store for music "validation" purposes
[*]update the iPod software
[*]share my music library over a local area network
[/LIST]
Is there a mutimedia programme (such as Rhythmbox) that will do this in Linux?  I've attempted to run iTunes in VirtualBox using a Windows xp virtual machine, but it crashes upon launch (despite a successful installation).  Any ideas?

---

### Post by Chronon on 2010-04-07
I'm fairly certain that the only application that can decrypt the DRM-infested files purchased from the iTunes Music Store is iTunes.  You could install Windows inside of a VirtualBox to run it if you like.

---

### Post by cascade9 on 2010-04-07
I've seen tools to strip the DRM from protected files from iTunes, but posting them here is a bit of a no-no from what I've heard. 

Maybe a handy search engine will find them for you ;) 

Just backup the files before you try it...and its best not to do the down and dirty trick of decoding the .wav then reencoding the files ;)

---

### Post by dominiquec on 2010-04-07
Just tried Rhythmbox of Ubuntu 10.04 and it works fine with the iPod Touch.  Only syncs music, though.  Still looking for solutions for pictures, etc.

---

### Post by temporos on 2010-04-07
> **dominiquec said:**
> Just tried Rhythmbox of Ubuntu 10.04 and it works fine with the iPod Touch.  Only syncs music, though.  Still looking for solutions for pictures, etc.
Yes, I've read that, too.  I need a solution that will also sync podcasts, apps, and videos (like iTunes will).  I didn't buy an iTouch so I could limit myself to music-only.  ;)

> **Chronon said:**
> You could install Windows inside of a VirtualBox to run it if you like.
In the last paragraph of my original post I mentioned that I installed Windows xp in VirtualBox, and that iTunes will not run in a virtual machine.  It crashes immediately upon launch.

Decrypting the iTunes Store DRM is no longer an issue.  It turns out I had only twelve m4p songs in my library, so I burned them to a CD, then re-imported them into my iTunes library.  The iTunes Store now sells DRM-free music, fortunately.  :)

---

### Post by Chronon on 2010-04-07
I have been using iTunes inside of Virtualbox for almost a year to sync to my iPod Touch, so it's possible to get it working, at least in principle.  If you find a solution that doesn't involve iTunes, so much the better!

Here is some more information:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by temporos on 2010-04-08
> **Chronon said:**
> I have been using iTunes inside of Virtualbox for almost a year to sync to my iPod Touch, so it's possible to get it working, at least in principle.
How did you get iTunes to run in VirtualBox?  I installed Windows xp (fully updated) using VirtualBox, and iTunes installed smoothly in the the virtual machine.  However, every time I attempt to launch iTunes, it immediately crashes.  Here's what I'm running in the virtual machine:

[LIST]
[*]**VirtualBox OS: **Microsoft Windows xp v2002 SP3
[*]**QuickTime: **QuickTime v7.66 (1671)
[*]**iTunes: **iTunes v9.1
[*]**Virtual machine memory: **192 MB
[*]**Virtual machine HDD: **10.00 GB
[/LIST]
Right now, Quicktime and iTunes are the *only* applications installed in the virtual Windows machine.  Did you experience issues like this?

---

### Post by Chronon on 2010-04-08
It could be a few things but I gave my virtual XP considerably more RAM than that (over 1 GB).  It could be due to that as I think iTunes for Windows can be a bit of a resource hog.  Additionally, XP should have at least 256 MB of RAM to run comfortably.  

There are other solutions posted on that community help page that I linked previously.  Maybe one of them will work well enough for you.

---

### Post by Alan James on 2010-04-08
You can run iTunes using Wine.It's pretty easy to do and runs well. I have found that it will not play media over a LAN. I have actually started another thread asking how to play media over a LAN.


[http://ubuntuforums.org/showthread.php?t=1448875](http://ubuntuforums.org/showthread.php?t=1448875)



 You may want to take a look at it as it relates to your question.

---

### Post by Dolmio on 2010-04-08
> **temporos said:**
> How did you get iTunes to run in VirtualBox?  I installed Windows xp (fully updated) using VirtualBox, and iTunes installed smoothly in the the virtual machine.  However, every time I attempt to launch iTunes, it immediately crashes.

I had the same problem. I solved the problem by installing an older version (9.01) of iTunes.

You can download it from here: [http://www.oldapps.com/itunes.php](http://www.oldapps.com/itunes.php)

---

### Post by temporos on 2010-04-09
> **Dolmio said:**
> I had the same problem. I solved the problem by installing an older version (9.01) of iTunes.
Unfortunately, that's not an option, since I use the iTunes Store for nearly all my music purchases, as well as updating podcasts and managing my iPod's apps.  I've attempted to use an older version, but Apple disables the iTunes Store for older versions, because they want to force their user base to upgrade.

[QUOTE=Alan James]You can run iTunes using Wine.It's pretty easy to do and runs well.[/QUOTE]
I've tried that.  You need to use an outdated version of iTunes.  Unfortunately, I can't do that for the reasons above.  :(

---

### Post by Alan James on 2010-04-09
I really wish Apple would port iTunes and Quicktime over to Linux. Just because they are on Linux doesn't mean they have to be open source and it would expand their customer base, although not by much. But Apple was always a company that played by its own rules.

---

### Post by Chronon on 2010-04-09
> **temporos said:**
> Unfortunately, that's not an option, since I use the iTunes Store for nearly all my music purchases, as well as updating podcasts and managing my iPod's apps.  I've attempted to use an older version, but Apple disables the iTunes Store for older versions, because they want to force their user base to upgrade.


I've tried that.  You need to use an outdated version of iTunes.  Unfortunately, I can't do that for the reasons above.  :(

There are other online music stores that will allow you to purchase media from a Linux system.  Maybe you could consider supporting one of those instead of Apple.  There are apps like gPodder that claim to allow syncing of Podcasts to iPods.  The sticking point would seem to be the apps, since Apple are the sole source for Apple applications.  They truly are masters of proprietary lock-in.

---

### Post by wme on 2010-04-14
i downloaded virtual box and  set up it  works  good   
but  i have 2 issues 
first  is that  i cant get  full  screen  i  click  machine  and  put  full screen 
and it just leaves a  box inside the fulll screeen so it  stays the  same  size  
idk wat to do   ive checked  for  updates  went to  settings and  put the best i can 

:confused:

---

### Post by Chronon on 2010-04-14
Install VirtualBox Guest Additions.

---

### Post by wme on 2010-04-14
thanks it worked :guitar:

---

### Post by wme on 2010-04-15
i had one more question i have virtual box runing a pre activated windows 7 ...
and i wanted to use to run itunes so i can sync  
its been giving me  prob  i was  wondering does itunes search  if my windows is  legit ?

---

### Post by hopstah on 2010-04-15
iTunes doesn't care if your windows is legit, but Windows Update does.  Get a legit copy to keep yourself as protected as possible on your Windows.

---

### Post by wme on 2010-04-15
true yea legit is better  i had a  xp legit key but since i was  messing with virtual box i used my key up 
now it says  invalid  but yeah i found win 7 works  great just the  i tunes dosent want to 
work on it  and iam trying to run itunes on  wine 
iam basically trying  get itunes to work so ican use it to  sync my  iphone ...
soo wat should i do >? 
:confused:

---

### Post by Chronon on 2010-04-15
Is your problem due to the guest system not having access to USB?  The OSE version of VirtualBox doesn't have USB support yet.  You can get the proprietary version for free from here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by temporos on 2010-04-15
**@WME: **The latest version of iTunes (9.1.0.79, as of this post) will not run under Virtualbox.  Apple has once again crippled it for non-Apple/Windoze users.  If you want it to run under Wine, you need to use iTunes v8.1 or prior.  But be warned that only v9.x will connect to the iTunes Store.

---

### Post by wme on 2010-04-15
actually i have the  latest version of   virtual box  its  just that  during the   installing the
itunes  says complete   but   as  soon  as i  click on the icon  on the  desk  
it it pops up a  error  that it cant  run   i unistalled  and installed  like  5 TIMES  so  i dont 
know wat to do iam runing the  latest  win7 and lastest virtual box

ps. its   a  pre acviated win 7

---

### Post by cybrsaylr on 2010-04-15
Thought Apple was going to drop all that DRM stuff?
That's another reason I never got into all that pricey Apple stuff. I always stuck with the universal mp3 that works anywhere with no problems.

---

### Post by Chronon on 2010-04-15
Dropping DRM is not the same as dropping proprietary lock-in.  I'm pretty sure the applications still bear some form of DRM too.

Anyway, this business is a big reason I don't upgrade the firmware on my device.

---

### Post by wme on 2010-04-15
well guys  i had a  old  computer  that  had a  sector that was not  recognizable 
 so wen i installed   only  120g of my  complete  drive  was  showing so  i was  wondering how  could  i  format it all   and   get back  the   complete  250g hardrive
so  i cant  reinstall   i think i would  have to  format but idk how to  format it  so 

i can  recognize it with ubuntu  
ps  dont care about  any data  saved on it

---

### Post by temporos on 2010-04-15
> **wme said:**
> well guys  i had a  old  computer  that  had a  sector that was not  recognizable 
 so wen i installed   only  120g of my  complete  drive  was  showing so  i was  wondering how  could  i  format it all   and   get back  the   complete  250g hardrive
so  i cant  reinstall   i think i would  have to  format but idk how to  format it  so 

i can  recognize it with ubuntu  
ps  dont care about  any data  saved on it
What does this have to do with running iTunes in Linux?  :confused:

---

### Post by Chronon on 2010-04-15
> **wme said:**
> well guys  i had a  old  computer  that  had a  sector that was not  recognizable 
 so wen i installed   only  120g of my  complete  drive  was  showing so  i was  wondering how  could  i  format it all   and   get back  the   complete  250g hardrive
so  i cant  reinstall   i think i would  have to  format but idk how to  format it  so 

i can  recognize it with ubuntu  
ps  dont care about  any data  saved on it

That's pretty thoroughly off-topic here.  You should start your own topic.

---

