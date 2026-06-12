---
title: "Getting DVD Shrink to work with Wine"
date: 2009-09-05
forum: Multimedia Software
---

### Post by jukingeo on 2009-09-05
Hello all,

I was looking for a good DVD ripping program to us within Linux, I was told that DVDShrink is a good ripping program that was created for Windows, but will run with Wine in Linux.

Ok, so I figured I would give it a shot considering I have Wine (1.0) on my system already.  Low and behold, it doesn't work.  I believe I have set it up correctly (but not totally sure).

The program DOES launch and I can locate my DVD rom, but when I click on the drive to load the contents, DVD Shrink hangs.

I am using Ubuntu Studio 8.04.

Thanx,

GEo

---

### Post by cariboo on 2009-09-05
I would suggest having a look at acidrip, it is in the repositories.

---

### Post by blackened on 2009-09-05
Here is the entry at WineHQ: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2230]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2230")

The comments section often contains helpful advice that is more program-specific than you're likely to get here.

---

### Post by jimmers on 2009-09-06
Why are you trying to install DVD Shrink in Wine, go to Add / Remove or SPM and install K9 Copy, and libdvdcss2, 


Jimmers

---

### Post by stinger30au on 2009-09-06
dvdshrink is only *HALF* of the picture

it takes a DVD that has *ALREADY* been decrypted and then will shrink it to fit on a 4.7 gig dvd


do yourself a favour.

forget about wine and dvdshrink

use k9copy instead

make sure the dvd will play on your pc first using movie player

if movie player plays it, k9copy will copy it

install k9copy from shell

sudo apt-get install k9copy

---

### Post by Midnighter on 2009-09-06
I'ver installed and run DVDShrink on a number of distros with little or no fiddling. How long do you wait for DVDShrink to do it's thing when it "hangs"? Are you running Compiz? Have you setup WINE correctly first?

I first got hints on making sure how to do dvddecryptor and dvdshrink from here [http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/) , have a look and see if anything you might have missed. :)

---

### Post by jukingeo on 2009-09-06
> **jimmers said:**
> Why are you trying to install DVD Shrink in Wine, go to Add / Remove or SPM and install K9 Copy, and libdvdcss2, 


Jimmers

> **stinger30au said:**
> dvdshrink is only *HALF* of the picture

it takes a DVD that has *ALREADY* been decrypted and then will shrink it to fit on a 4.7 gig dvd


do yourself a favour.

forget about wine and dvdshrink

use k9copy instead

make sure the dvd will play on your pc first using movie player

if movie player plays it, k9copy will copy it

install k9copy from shell

sudo apt-get install k9copy

Ok, I got the picture on DVD Shrink.  When I did my search for a DVD ripping program, many people suggested using DVD Shrink with Wine.  Granted, some of these recommendations were older.

At any rate, I DO prefer the idea of sticking with a Linux program over using Wine.  Thus as of now I HAVE deleted DVD Shrink off my system.

Doing some readings on your suggestions I have decided to check out K9Copy first.  From the screenshots, I like this program.  There was even a mention of it being akin to Window's DVD Shrink.  So that got my vote.  I did look it up in the Synaptic Repository and it is there, however, it says that K9Copy is for KDE.  I am using Gnome.

(As a slightly off topic sidebar, I have been thinking about switching Gnome to either KDE or XFCE.)

> **cariboo907 said:**
> I would suggest having a look at acidrip, it is in the repositories.

I took a quick peek at it, it looks similar to another program that I used a while back called DVDRIP. I remember I wasn't too happy with DVDRIP.  It always left a small "video distorted line" at the bottom of the screen. I wasn't too happy with that.

So the question would be how do the three compare:

DVDRIP v.s. Acidrip v.s. K9Copy?

Thanx,

Geo

---

### Post by lefty_lou on 2009-09-07
> **jukingeo said:**
> 


Doing some readings on your suggestions I have decided to check out K9Copy first.  From the screenshots, I like this program.  There was even a mention of it being akin to Window's DVD Shrink.  So that got my vote.  I did look it up in the Synaptic Repository and it is there, however, it says that K9Copy is for KDE.  I am using Gnome.



You can install kde stuff on gnome just use the synaptic and it will tell you what else it needs to install, apply and let it install then try it out.
Or use DVD95 for gnome it's also in the repos in synaptic.

hope this clears that out for you. :)

I just tested K9 and DVD95  and well i must say K9 was way simpler 

DVD95 seems simple with simple menu but couldn't get it to work yet.

K9Copy well just used the wizard and already burning the .iso as i write this

DVD was original Valkyrie DVD wich was about 6+ gb

so if it was up to me i'll go with K9copy. hope this helps you man.

---

### Post by dawnlove on 2009-09-07
The only way I have found to get wine/dvdshrink to load a DVD is to right click on DVD in file manger and open with other program and you have to find DVDshrink in gui or comand ie; something like=     wine 'C:\Program Files\dvdshrink/dvdshrink.exe'  

> **jukingeo said:**
> Hello all,

I was looking for a good DVD ripping program to us within Linux, I was told that DVDShrink is a good ripping program that was created for Windows, but will run with Wine in Linux.

Ok, so I figured I would give it a shot considering I have Wine (1.0) on my system already.  Low and behold, it doesn't work.  I believe I have set it up correctly (but not totally sure).

The program DOES launch and I can locate my DVD rom, but when I click on the drive to load the contents, DVD Shrink hangs.

I am using Ubuntu Studio 8.04.

Thanx,

GEo

---

### Post by jukingeo on 2009-09-07
> **lefty_lou said:**
> You can install kde stuff on gnome just use the synaptic and it will tell you what else it needs to install, apply and let it install then try it out.
Or use DVD95 for gnome it's also in the repos in synaptic.

I installed it and it DID come up, but I have not fully tested as of yet.  I remember that when I tried Kdenlive for the first time, it too installed and came up, but I had problems when it came to loading up videos. I tried numerous fixes but Kdenlive just wouldn't work in Gnome.  While problems have improved over the past year or so, I still hear that those trying to run Kdenlive in Gnome are having problems.  However, for those using KDE there are no problems.

A couple days ago I tried out an experiment by switching desktop sessions using the XFCE interface. That seemed to work fine.  I am wondering if I could set up KDE on a session as well.  If so then that would be good, because then I will just use K9copy and Kdenlive under the KDE interface and I shouldn't have any problems.  I guess I have to play with K9Copy first and see how well it works in Gnome.

While I like Gnome, I have found out that it isn't very conservative on resources.  So I am looking for something more streamlined.  However, I have noticed that much of the audio and video editing work I would like to do seems to fair better under KDE than Gnome.

> 
hope this clears that out for you. :)

Yes, thank you.

> **dawnlove said:**
> The only way I have found to get wine/dvdshrink to load a DVD is to right click on DVD in file manger and open with other program and you have to find DVDshrink in gui or comand ie; something like=     wine 'C:\Program Files\dvdshrink/dvdshrink.exe'

Hmmm, I remember having to do that with another program as well, but in this case, DVDShrink DID recognize the drive.  It DID acknowledge it was there. But when I clicked on it to access the info, the drive would start up and just keep spinning, just keep spinning.  The contents wouldn't come up.

However at this point in time since there are more Linux recommendations, I am going to go that route. As it is, I like the look and features of K9copy.  I have heard it more than once that K9Copy will do what DVD Shrink does, but it works totally under Linux.  The only thing is that K9Copy is a KDE based program.  Usually KDE doesn't mix will with Gnome.  But as I mentioned above, I am willing to change the interface if 1) improves running KDE programs & 2) If KDE uses less resources.

Thanx,

Geo

---

### Post by lefty_lou on 2009-09-07
> **jukingeo said:**
> 


While I like Gnome, I have found out that it isn't very conservative on resources.  So I am looking for something more streamlined.  However, I have noticed that much of the audio and video editing work I would like to do seems to fair better under KDE than Gnome.




Check my previous post where i did the suggestion i did an update to it :already tested K9Copy under gnome and worked like a charm :P 

Hmm well can't really compare as i use Gnome but while converting and burning using K9Copy i was browsing the web and moving some files around to make space while listening to music using Amarok (another KDE app running under gnome) and my Mem usaged did not go beyond 30% of system total. 

I'm using jaunty (9.04) 64bit with Amd Athlon64 X2 5600+ and 4 Gb mem  and NVidia GeForce 9400Gt 1Gb on board don't know if that's an issue but just figured i will post that info for you to compare and check.

As in for the KDE yes you can go to synaptic and download the KDE environment and at the login screen it will let you choose if you want KDE or Gnome.

That my friend is the beauty of LINUX! choices that suit you the way YOU want it and not the way the os wants you to do it.

---

### Post by lisati on 2009-09-07
> **stinger30au said:**
> dvdshrink is only *HALF* of the picture

it takes a DVD that has *ALREADY* been decrypted and then will shrink it to fit on a 4.7 gig dvd



Incorrect. The copy of DVDshrink I use with Windows can handle encrypted DVDs. There has been only one disk that I haven't been able to process with DVDShrink.

To ALL posters: be careful that you don't open yourself to copyright hassles.

---

### Post by jukingeo on 2009-09-07
> **lefty_lou said:**
> C :already tested K9Copy under gnome and worked like a charm :P 

Ok, good to know.

> 
Hmm well can't really compare as i use Gnome but while converting and burning using K9Copy i was browsing the web and moving some files around to make space while listening to music using Amarok (another KDE app running under gnome) and my Mem usaged did not go beyond 30% of system total.

Well, I don't expect most people to have several interfaces on their systems, but I would be curious to find out if there is a performance difference between Gnome and KDE.


> 
I'm using jaunty (9.04) 64bit with Amd Athlon64 X2 5600+ and 4 Gb mem  and NVidia GeForce 9400Gt 1Gb on board don't know if that's an issue but just figured i will post that info for you to compare and check.

Might be, it is a faster machine than mine. But my project does involve using even slower machines than this one.  Most machines I come across or are 'donated' to me are from the Pentium III/Windows 98 era.  Naturally I am interested in running as streamlined as possible.

Granted most of the video/audio editing I will do on my current machine, so being that the other machines are 'presentation playback' machines only, they do not need to be as  powerful.  But I have noticed that some programs do eat up quite a bit of system resources and a good portion of resources goes to the gui interface.  So it is something I am taking into consideration for overall performance.

> 
As in for the KDE yes you can go to synaptic and download the KDE environment and at the login screen it will let you choose if you want KDE or Gnome.

Good!  I did figure as much.  I downloaded and tried out the XFCE interface and I do like that one.  I was hoping I COULD do the same with KDE.

> 
That my friend is the beauty of LINUX! choices that suit you the way YOU want it and not the way the os wants you to do it.


Yup...well the beauty of Ubuntu.  I have tried a couple other Linux distributions before but I ran into problems.  Being somewhat still a beginner, I kept coming back to Ubuntu because of the support.  It was only a couple nights ago I learned that you CAN change the entire gui interface but yet still keep all data and programs intact.  The interface doesn't mess with the kernel either and you don't need a rebuild.  So that is good news to me.

I pretty much was using Gnome or Gnome like interfaces for the other distributions I have used in the past only two were different: Dyne Bolic and I used the KDE version of OpenSuse 11.  OpenSuse was SLOW on my system.  It was VERY resource hungry.  It did work though, but I knew it wouldn't fair well on the slower machines I have...so once again I went back to Ubuntu.

For the most part I had some rough going getting 8.04 (Hardy) to work.  It was VERY buggy when it was first released, but slowly over time, it has improved with various fixes and updates.  For everyday use I have very little problems with it.  Since I heard that version 8.04 is part of the new 3 year support...I have decided to stick with this version.  I have also abandoned distribution hopping for now and I want to stick with Ubuntu.  BUT I do want to explore it's variants.  I am hearing much about the new variant called Lubuntu, which supposedly saves even more on system resources than Xubuntu.  The beauty of being able to switch to those variants' gui interfaces without actually switching the OS is sheer bliss. This way I can try out and see if I like the interface or not.  And yes, that is something you could NEVER do in Windows!

Thanx, Geo

---

