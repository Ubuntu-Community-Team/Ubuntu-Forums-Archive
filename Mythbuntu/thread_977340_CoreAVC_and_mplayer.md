---
title: "CoreAVC and mplayer"
date: 2008-11-10
forum: Mythbuntu
---

### Post by raptorjr on 2008-11-10
I'm trying to get mplayer to work with CoreAVC and dont have much success. I find it hard to get all the right packages so i can compile the source with the same options that i have on my current mplayer.
I wonder if there is or if it is possible to have a custom mplayer package for mythbuntu that is prepared for CoreAVC? So the only thing i need to do as a new user is to buy CoreAVC, follow the guide to register it and then install the custom mplayer package.

It would be very nice if that was possible, since now it seems that it is the only way for me to play 1080p since mplayer refuse to use more than one core.

On the other hand, if someone knows how to get mplayer to use more than one core it would probably be enough to solve my problems. I have tried to get mplayer to use more threads, but that dont take advantage of my second core.

---

### Post by majoridiot on 2008-11-10
> **raptorjr said:**
> I'm trying to get mplayer to work with CoreAVC and dont have much success. I find it hard to get all the right packages so i can compile the source with the same options that i have on my current mplayer.
I wonder if there is or if it is possible to have a custom mplayer package for mythbuntu that is prepared for CoreAVC? So the only thing i need to do as a new user is to buy CoreAVC, follow the guide to register it and then install the custom mplayer package.

It would be very nice if that was possible, since now it seems that it is the only way for me to play 1080p since mplayer refuse to use more than one core.

On the other hand, if someone knows how to get mplayer to use more than one core it would probably be enough to solve my problems. I have tried to get mplayer to use more threads, but that dont take advantage of my second core.

you didn't say what version you are running, what type of file, your processor, etc...

but i just checked and a 1080p .ts seems to work all 4 processors in my quadcore backend
fairly evenly and balances the load back and forth as it should, playing it in mplayer
2:1.0~rc2 (latest version) from the medibuntu repository.

---

### Post by raptorjr on 2008-11-11
I'm running mythbuntu 8.10.
I have a Core 2 Duo E8200 2,6Ghz. I got a clip of Planet Earth and that clip is jerky very often. When it happends one core is on 95% and the other core is on 0,5% utilization. That dont seem right. I see the same thing on other 1080p things i play also, one core working alot and the other core not doing very much.

---

### Post by majoridiot on 2008-11-11
> **raptorjr said:**
> I'm running mythbuntu 8.10.
I have a Core 2 Duo E8200 2,6Ghz. I got a clip of Planet Earth and that clip is jerky very often. When it happends one core is on 95% and the other core is on 0,5% utilization. That dont seem right. I see the same thing on other 1080p things i play also, one core working alot and the other core not doing very much.

not meaning to keep poking at you dude, but the more info you provide, the better.  still
no clue if you are running a 32 or 64 bit ubnutu or what type of file... but for the latter i
will assume a matroska file, since you want to know about coreavc.

here is some good info on how to custom-compile mplayer for intrepid:
[http://smplayer.berlios.de/forums/viewtopic.php?id=741](http://smplayer.berlios.de/forums/viewtopic.php?id=741)

and here is good info on how to get coreAVC to play nicely with mplayer in linux: 
[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)

hope that is enough to get you going...

not sure how well your core2 will handle 1080p, but if you can at least get the loads balancing 
a little better and get coreavc working, you might have a decent chance.

as a side note, have you tried playing the files in VLC to see if it does any better?

also, there was no mention of what video card/driver you are using and that makes all the difference
in the world as well.

good luck!

---

### Post by raptorjr on 2008-11-11
Dont mind the questions, i appreciate all the help i can get. And i want 1080p to work.
Yes it is matroska files. And i have a Abit N73HD motherboard with GeForce 7100 onboard graphics. According to what i found on the net before i bought it, it should be able to play 1080p.
And 32bit Ubuntu. I heard that you dont get that much extra with 64bit besides problems. 

Haven't tried VLC yet, will do that.

I am able to compile mplayer, but my biggest problem is that i'm obviously missing a lot of files because after the compile i lack a lot of features that the preinstalled mplayer has. Subtitles, video renderes and alot else. I would need a guide how to compile it to get it like the preinstalled version. But i will have a look at the links you provided. Thank you.

---

### Post by rvm4000 on 2008-11-11
> **raptorjr said:**
> Dont mind the questions, i appreciate all the help i can get. And i want 1080p to work.
Yes it is matroska files. And i have a Abit N73HD motherboard with GeForce 7100 onboard graphics. According to what i found on the net before i bought it, it should be able to play 1080p.
And 32bit Ubuntu. I heard that you dont get that much extra with 64bit besides problems. 

And I heard mplayer is about 10-20% faster on a 64bit processor.
I actually have installed the amd64 version of kubuntu 8.04, and I have no problems at all with mplayer. I can play 720p videos without problems (even with the gl driver). Didn't try 1080p, though.

(BTW, IMO a 64bit distro works as good as a 32bit distro, with more or less the same problems. For instance I had problems with the ATI driver, but the ATI driver also causes problems in a 32bit distro, doesn't it?)

> **raptorjr said:**
> I am able to compile mplayer, but my biggest problem is that i'm obviously missing a lot of files because after the compile i lack a lot of features that the preinstalled mplayer has. Subtitles, video renderes and alot else. I would need a guide how to compile it to get it like the preinstalled version. But i will have a look at the links you provided. Thank you.

This will install all build dependencies:
```
sudo apt-get build-dep mplayer
```

But I really suggest to read this:
[http://smplayer.berlios.de/forums/viewtopic.php?pid=3064#p3064](http://smplayer.berlios.de/forums/viewtopic.php?pid=3064#p3064)

---

### Post by raptorjr on 2008-11-13
Yes, that guide made it a lot more easier. And now i have CoreAVC running. With both cores i have no problem playing 1080p. Too bad mplayer couldn't use both cores.

But anyway, back to the original question. Since MythBuntu is all about making it easy to get a good multimedia system i think it would still be nice with a mplayer package that had support for CoreAVC. I dont think it would break anything else and you can still use mplayer without CoreAVC. But it is easier for those who would like to go down that path.

---

### Post by rvm4000 on 2008-11-13
> **raptorjr said:**
> Too bad mplayer couldn't use both cores.

I think the ffmpeg developers (mplayer uses libraries from it) are working on it.

---

### Post by majoridiot on 2008-11-13
> **raptorjr said:**
> Yes, that guide made it a lot more easier. And now i have CoreAVC running. With both cores i have no problem playing 1080p. Too bad mplayer couldn't use both cores.

But anyway, back to the original question. Since MythBuntu is all about making it easy to get a good multimedia system i think it would still be nice with a mplayer package that had support for CoreAVC. I dont think it would break anything else and you can still use mplayer without CoreAVC. But it is easier for those who would like to go down that path.

glad you got that working!

since you know the drill now, maybe *you* could join mythbuntu development and help them
with packaging coreAVC enabled mplayer for the project? 

;)

---

### Post by raptorjr on 2008-11-14
I'll look into it. Se if i can get something together worth sharing.

---

### Post by maxim99 on 2008-11-21
I put together a How-To on doing this and wrote a short script to help do it a while back. This mplayer supports almost every video file i've come across and any subtitles I throw at it.

Building the deb package is cake, but I probably did it wrong. I don't know the first thing about building a deb.

Here is the link: [http://forumubuntusoftware.info/viewtopic.php?f=7&t=1581](http://forumubuntusoftware.info/viewtopic.php?f=7&t=1581)

Building the debian install is pretty easy, it's just the fine tuning of putting the files where they need to be and making changes to files that are currently there that's a hassle. The install has to be dynamic in that if there are any preferences from the previous install they need to be duplicated, and also there shouldn't be two different versions of mplayer installed. I, personally, would welcome a package like this on the mythbuntu repos, or any repo for that matter. Too bad there isn't just some kind of plugin that could be downloaded to add it as a feature.

---

