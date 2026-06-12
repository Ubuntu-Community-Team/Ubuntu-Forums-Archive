---
title: "iTunes for Ubuntu Petition"
date: 2008-04-26
forum: Multimedia Software
---

### Post by thebigbluecan on 2008-04-26
[http://www.petitiononline.com/eb221998/](http://www.petitiononline.com/eb221998/)

I Love iTunes for managing music and syncing to my iPod. In my opinion there are no great iPod syncing programs for ubuntu. I hate going to windows just to do music. (Thats all windows is used for now) And I want to get rid of Windows Completely. This possibly could help bring iTunes to Ubuntu.

[http://www.petitiononline.com/eb221998/](http://www.petitiononline.com/eb221998/)

"    To:  Apple, Inc.

    Now that Ubuntu is going to be preinstalled onto Dell computers, it's only a matter of time before Ubuntu becomes a household name along with "Mac OSX" and "Windows Vista."
    Apple Inc. owns a astounding share on the mp3 player community with their Apple iPod product line. With the introduction of Intel based Macs, dual operating systems are now easily able to be installed. With the latest "Fiesty Fawn" release of Ubuntu (7.04) there will be more computers running the free operating system. With iTunes being available for Windows and Mac users, how long will it be until Apple releases an Ubuntu version of iTunes? I, for one, would gladly ditch Windows for Ubuntu but no iTunes support is keeping me from doing that. Yes, I have a Macbook but my music collection is kept on my PC whose speed is getting slower every day.
    With this petition, I want to let Apple Inc. know the demand for an Ubuntu iTunes. Each and every signature is a voice that Apple needs to hear.

    Sincerely,

    The Undersigned"


[http://www.petitiononline.com/eb221998/](http://www.petitiononline.com/eb221998/)

---

### Post by cogadh on 2008-04-26
iTunes still uses some DRM for its music. DRM will never work on Linux. Therefore, iTunes will never be ported to Linux. 

Unless, of course, the iTunes store goes 100% DRM free and all previously purchased tracks get their DRM removed. Then the chances of a Linux port increase slightly, but not by much.

---

### Post by Mr.Macdonald on 2008-04-26
Have you tried using some Wine

i haven't because i use Amarok (Amazing)

Also look into a replacement of the Apple junk instead of a port. I use Rockbox for my iPod it is far superior (i think) to Apple stuff.

[rockbox.org]("rockbox.org")

try it. its easy to get rid of, and even easier to sync (just drop music in the root of the ipod)

---

### Post by mrsteveman1 on 2008-04-26
> iTunes still uses some DRM for its music. DRM will never work on Linux. Therefore, iTunes will never be ported to Linux. 

You are confusing things. DRM works on Linux just fine. iTunes on Windows doesn't rely on the platform for its DRM either, it is entirely self contained. iTunes for Linux similarly doesn't require the system to support DRM and would work perfectly fine. If you want to make the claim that there shouldn't BE a Linux port of iTunes because it uses DRM, thats different, but if Apple wants to release packages for Ubuntu they can, and obviously some people would use it.
 
You can replace some of the things iTunes does with random other programs, most of which aren't all that good, but some things you can't do without iTunes, like restore iPods, upgrade firmware, rent movies etc. If you read some of the comments on the petition, this is crystal clear:

> 	It is very difficult owning an iPhone without access to iTunes on my Ubuntu computer. 

gtkpod and the rest all suck, we need you to support your hardware

I want to use Ubuntu, but am reluctant to do so until it supports iTunes.

gtkpod and rhythmbox unfortunately do not measure up to the simplicity of itunes. I would really like to see this application for Ubuntu.

 iTunes would likely be the first real supported movie rental service on Linux if they did port it.

Rockbox isn't an answer either, it is only relevant for iPods that are at this point over 2 years old, and it will always be behind the real firmware because people have to reverse engineer the platform to get drivers for the devices in the iPods. Theres also a reason you can't just drop songs into the ipods drive, they use a database to keep track of things ID3 tags can't do, which requires a program to manage that database on the device.

If i could speculate for a minute though about WHY there isn't a port, marketshare of course has something to do with it but doesn't explain everything. There are SIGNIFICANT problems with Linux audio/video subsystems, people routinely get severe screen tearing regardless of the video drivers in use, which makes video difficult to support. What do you tell a customer who calls up and complains about poor video playback on a movie rental that Apple can't really fix? 

And there have been MASSIVE changes to the way Ubuntu works between releases. Hardy just implemented a completely new sound server, if iTunes had been ported before this, they would have been using an older subsystem and would have to substantially change the program to support things like that.

I think they simply are waiting for things to work out on the platform, like i said there are technical reasons for them to stay away for the moment.

---

### Post by piratesmack on 2008-04-26
Apparrently, iTunes is making progress in Wine

[http://www.winehq.org/?issue=345#iTunes%20support%20is%20making%20progress](http://www.winehq.org/?issue=345#iTunes%20support%20is%20making%20progress)!

Personally, I don't like iTunes very much

---

### Post by thebigbluecan on 2008-04-26
I tried iTunes in wine and it didn't go too well.

---

### Post by piratesmack on 2008-04-26
```

Hi all,

I submitted the ipod patches to wine-patches. This won't add support for ipod touch or iphones. I expect that all patches will be merged soon. If anyone feels adventurous they can try it. With the amount of people interested in it I decided to post an update on the mailing list so that everyone who picked up on the earlier threads can find it.

Instructions:
- Apply attached patch
- Get a clean wineprefix
- Set wine version to vista
- Download the installer from itunes.com, and install.
- wine net start ipod\ service
- run itunes
- Hopefully the ipod is detected now. Dapper might have a bug in hald which case it won't detect any usb hard drive that's plugged in. sudo killall hald; sudo hald; wineserver -k; wine net start ipod\ service seems to work as workaround.

So far there seems to be some confusion, so for the sake of clarity: This won't add support for ipod touch or iphones.

Cheers,
Maarten.

```

---

### Post by tamoneya on 2008-04-26
iTunes only causes trouble for me.  While I like to see more companies developing software for linux i think we should push for something that is better than itunes.  It would be awesome if Photoshop ran natively in linux(yes i know it runs in wine)

---

### Post by Bubba64 on 2008-04-26
I am assuming that you all know that Amazon has a Mp3 downloader now that can download whole files on Linux.

---

### Post by mrsteveman1 on 2008-04-26
Sure amazon MP3 works in linux, that doesn't solve the numerous other reasons people need iTunes though. The music store isn't why most people use iTunes.

It's also worth noting that iTunes for Windows is a very poor application, which is why most people hate it. The OS X version works fine.

With the Windows port, they had to include substantial portions of the APIs and frameworks that would otherwise be native on OS X inside the application itself, because otherwise it would be a major effort to port the program. So they at least have some experience porting stuff like this, porting to Linux by including a bunch of OS X frameworks in the app would be no different than they already do for Windows now.

---

### Post by tamoneya on 2008-04-26
it isnt so much the way that iTunes is ported to windows from OSX and therefore has extra frameworks and stuff that bothers me.  What I don't like is how it messes around with my music no matter how many times I tell it not to touch it.  It insist on moving it into different locations and it makes it very difficult to work with the music outside of itunes.

---

### Post by Bubba64 on 2008-04-26
> **mrsteveman1 said:**
> Sure amazon MP3 works in linux, that doesn't solve the numerous other reasons people need iTunes though. The music store isn't why most people use iTunes.

It's also worth noting that iTunes for Windows is a very poor application, which is why most people hate it. The OS X version works fine.

With the Windows port, they had to include substantial portions of the APIs and frameworks that would otherwise be native on OS X inside the application itself, because otherwise it would be a major effort to port the program. So they at least have some experience porting stuff like this, porting to Linux by including a bunch of OS X frameworks in the app would be no different than they already do for Windows now.

I don't own an Ipod, my reason for posting was that I personally wouldn't own a proprietary device, supporting Apple to me is no more different then supporting MS. Have we stopped to notice that the free market is in the end destroying our planet and each other. Unfortunately though this will never change, I have no better answer to this predicament other than not supporting it the best I can.

---

### Post by mrsteveman1 on 2008-04-27
There aren't many non-proprietary music players out there. It's Apple vs. Playsforsure at this point, and the Zune of course. 

iTunes does like to move files around but its only supposed to do that if you tell it to keep your music organized and if you tell it to copy music when added to the library. If you turn those 2 options off it shouldn't touch anything. It organizes the files according to the ID3 tag which helps a lot sometimes. It doesn't coexist well with other players though, they assume if you use iTunes you won't be using anything else, which isn't the case a lot of times.

I'll take Apple over MS any day.

---

### Post by Bubba64 on 2008-04-27
[QUOTE=mrsteveman1;4807878]There aren't many non-proprietary music players out there. It's Apple vs. Playsforsure at this point, and the Zune of course. 

Fortunately being a multi instrumentalist who used to play jazz professionally, and other types of fully improvisational music, and having studied music theory to the level of a fully chromatic approach by using the The Lydian Chromatic Concept of Tonal Organization, By George Russel The music is always in my head.
[http://en.wikipedia.org/wiki/George_Russell](http://en.wikipedia.org/wiki/George_Russell) 
All I have to do is think of it and I can hear it, so that saves me money on a music player other than my computer. In the end though it is a positive thing for the devices to be available, it means a lot to many people to have something to listen to.

---

