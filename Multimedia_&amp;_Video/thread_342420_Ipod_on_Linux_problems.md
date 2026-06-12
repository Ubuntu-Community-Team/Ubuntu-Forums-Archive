---
title: "Ipod on Linux problems"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by Polymira on 2007-01-20
Hello,

 I'm looking to sync an ipod mini in linux, but I'm looking a solution that will address these needs:

*Ability to pick and choose what music on the ipod
*Put podcasts on the ipod that show in the podcast section of the ipod UI
*Auto sync podcasts onto the ipod, even though i'm manually choosing music
*Smart playlists that work on the ipod 

Is this possible? I don't have a problem rss'ing things on my own, but these are issues i've had. I've been able to find a solution to the 1st one, but not the rest...

---

### Post by mlissner on 2007-01-20
I suggest a combination of rockbox and a collection of scripts. That's a pretty complex set of desires for an iPod, and Apple makes it pretty hard to do creative things like that.

If you install rockbox instead, it makes your iPod work like a mass storage device, so it can be handled much easier. 

A thought I suppose. I don't think you're going to have much luck in any other way.

---

### Post by Polymira on 2007-01-20
Meh, it's all things i used on a regular basis via itunes... I'm currently syncing it for podcasts on my macbook in osx, but I wouldn't mind my music as well, as I use it in my car...

I'd do it all on the notebook if I didn't have so much music i'd have to keep on the HD, meh ... as I said, I'll figure something out =/

And it's mounted as mass storage no matter what when I plug it in anyways, even without having to force disk mode or installing anything =/

---

### Post by mlissner on 2007-01-20
Yeah, the thing about itunes/ipod that's annoying is it does a little DRM work so that you can't use your ipod to share music without third party software. I believe the bulk of what it does is to rename all of the files so they are unintelligible and then to build a small database that references the strangely named files. Have a look in your ipod sometime if you don't know what I mean. 

I suppose that's neither here nor there though. You're right about the mass storage device bit...what I meant to say was that if you install rockbox, all you have to do is drag songs onto your ipod, and bingo, they work. You don't need some annoying piece of software like itunes to move songs onto what is really just a harddrive.

You might give amarok a shot through. I like it and it has ipod support built in. I don't know how it handles putting podcasts and such onto your ipod, but I think it has support for them.

If you want amarok, do:
```
sudo apt-get install amarok
```

---

