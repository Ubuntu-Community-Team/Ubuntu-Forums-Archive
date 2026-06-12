---
title: "Help With an Idea"
date: 2008-07-10
forum: Multimedia Software
---

### Post by Nitewolf121 on 2008-07-10
I'm building a new pc this weekend once the rest of my parts get here tomorrow.  I'm trying my best to make this new pc be Ubuntu mainly.  I'm dual booting for gaming purposes only.  Running XP via VM for database editing for work and minor work programs.  If this works out, I have a laptop I want to swap over also.  Plus I have other plans, which is where I need help.

iTunes - I have a ton of songs I don't want to lose access too, but I don't want to boot to windows just to listen to them.  Workarounds?

Blu-ray on Ubuntu?  And along with that 1080P output with video cards using HDMI output?  <---Probably more a video card question.

Anyway, why I'm asking is this.  I am about to build a Media Center PC to store my DVD's and CD's on.  I'm tired of having around 200+ cases of DVD's sitting around my living room.  Is there a way to do this using solely Ubuntu?  I'm looking for a way to rip and playback my DVD's, same with my CD's and obviously itunes music also.  Play my DVDs to my LCD TV, stream them too my desktop or laptop if I want to watch them in another room or while I'm working on the computer.  A somewhat clean sorting system for music and video searching.  Remote control use, or bluetooth keyboard use.  Main functions are media storage server and media center pc.  

I've fiddled with Ubuntu in the past, but I'm still really new to it.  I'm trying to break away from windows as much as possible.  I'm not even sure this is completely conceivable even in Windows though, as I'm just starting to research this thoroughly.  

Will Ubuntu do what I'm looking for, or Ubuntu with a Windows VM?  I'm new to the whole VM idea, not sure what it will do with video playback or audio playback.  :confused:

---

### Post by snowpine on 2008-07-10
Hi Nitewolf, I used myfairtunes to convert my itunes library. It is a free windows application, and converts them all in one big batch.

---

### Post by Nitewolf121 on 2008-07-10
One problem down, thank you for that.  :)

---

### Post by snowpine on 2008-07-10
Just to be clear, I typed that in a hurry, it converts copy-protected songs you purchased from itunes to a non-copy-protected mp3 format. 

It won't move them over to your linux partition or anything crazy like that. :)

---

### Post by Nitewolf121 on 2008-07-10
All I'm looking for is the ability to play them still.  Now I gotta figure out where to get music from.

---

### Post by Nitewolf121 on 2008-07-10
Just thought of something else.  If I weren't able to make this family friendly enough (so I don't have to be around to run it) wouldn't I still be able to just stream media from a windows media server to my desktop and laptop?

---

### Post by markbuntu on 2008-07-10
You know, most media servers do not run on windows, they run on linux. There is an Ubuntu Media Center distribution around somewhere that may do just what you want and an Ubuntu Server edition. And best of all, these are free and so are all the apps you need to make them do exactly what you want.

As far as setting up a media server, put all your media on a separate hard drive or 2 from your operating system and applications. That way, when vista or ubuntu for that matter, gets just too frustatingly difficult you can change without losing your stuff or having to reinstall it. It will also make it easier to move them around.

---

### Post by jonofan on 2008-07-11
> **Nitewolf121 said:**
> All I'm looking for is the ability to play them still.  Now I gotta figure out where to get music from.


[URL="http://free.napster.com/"]http://free.napster.com/
[/URL]

Cheaper than itunes and compatible with itunes as well.

---

### Post by Nitewolf121 on 2008-07-11
> **markbuntu said:**
> You know, most media servers do not run on windows, they run on linux. There is an Ubuntu Media Center distribution around somewhere that may do just what you want and an Ubuntu Server edition. And best of all, these are free and so are all the apps you need to make them do exactly what you want.

As far as setting up a media server, put all your media on a separate hard drive or 2 from your operating system and applications. That way, when vista or ubuntu for that matter, gets just too frustatingly difficult you can change without losing your stuff or having to reinstall it. It will also make it easier to move them around.

That is what I'm looking for.  I'll start searching around for an Ubuntu Media Center distro, if anyone knows where let me know please.  :) That word you used "free" is a big reason why I'm trying to do this the little bit harder way, for me at least.  

About storing the media on another hard drive.  What I'm thinking of doing is just making to new pc's.   One would be my media center, the other would be a media server that I'm just going to throw in a closet somewhere out of the way.

---

### Post by DariusS on 2008-07-11
in regards to the media server, I read somewhere about a lamp server, had some success myself in setting it up, till my processor blew out.

[http://ubuntulinuxhelp.com/30-dollars-30-minutes-1-nice-fileserver/](http://ubuntulinuxhelp.com/30-dollars-30-minutes-1-nice-fileserver/)
that site has some great tips, bu ti believe it's for an older version of ubuntu. you should however be able to DL the server edition of Hardy and accomplish the same thing.

as far as the media center pc, Ubuntu studio might be of interest, though it's geared more toward production.
[http://ubuntustudio.org/](http://ubuntustudio.org/)

but Mythbuntu is meant to be more like a DVR system, so this might be exactly what you want, though it seems more tricky to set up.
[http://www.mythbuntu.org/](http://www.mythbuntu.org/)
Mythbuntu is an integration of Ubuntu and MythTV into one distro, so it should be seamless, though I had a few headaches getting it set up (not too familiar with server apps)

hope this helps.

---

### Post by tijmz on 2008-07-11
I have similar plans and have found that if you want to run an open source media center, there are a lot of choices. At one point I narrowed it down to:

[LIST]
[*][Linux MCE](http://www.linuxmce.org/): Ugly GUI (imho) but if you like tweaking it promises heaps of functionality (TV recording, house automation)
[*][eAR OS Media Center](http://www.earos.dk/): An Ubuntu-based distro with in-built media center software, DVD-ripping/burning tools, etc
[*][Elisa Media Center](http://elisa.fluendo.com/) - I am mentioning this because I will probably choose this one myself. Great GUI but very limited functionality
[*]MythTV/[MythBuntu](http://www.mythbuntu.org/): I think this is the most used software for building an audio/video jukebox, and it is therefore backed by a vibrant community. Originally designed for TV recording and the like, using plugins you can turn it into a jukebox easily (or so it is said)
[/LIST]

Judging by the stuff you mentioned (streaming it to different frontends, wanting to rip and burn DVDs/CDs) I would guess you're best off with one of the various MythTV flavours. I think these can do everything you want. They are actually built around the idea of having a server with content (a backend) that is accessible from other places on the network (the frontends).

Check video sites like YouTube for demonstrations of these packages to get an idea of what to expect.

---

### Post by Nitewolf121 on 2008-07-11
Mythbuntu looks like it might suit might needs perfectly.  Elisa looks possible too.

Linux MCE does have a nasty looking GUI, I don't know if I could stand looking at that thing all the time.

---

### Post by k420 on 2008-07-15
My main suggestion is if thinking about what distro to use.  I would suggest being very careful about he hardware you choose.  Make sure that you do the research to make sure everything works out of the box.

---

