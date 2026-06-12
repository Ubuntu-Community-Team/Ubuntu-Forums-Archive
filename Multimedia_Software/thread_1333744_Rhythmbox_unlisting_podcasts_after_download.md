---
title: "Rhythmbox unlisting podcasts after download"
date: 2009-11-21
forum: Multimedia Software
---

### Post by danielsk on 2009-11-21
I'm using Ubuntu 9.10 32bits with Rhythmbox 0.12.5

When I was updating the poscast sources it listed and started to download the new ones, however, after download the podcast is removed from the podcast list. I can still find it in the music list and the mp3 file is here.

It was working ok until last week. Anyone know what it could be?

---

### Post by alexlinux on 2009-12-17
I have the same problem too! However, the same podcasts show in Music...

---

### Post by alexlinux on 2009-12-17
This problem has already been identified and a workaround as been found: see entry #7 at [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/451176](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/451176).

---

### Post by brookie on 2009-12-23
Hola Ubunteros, 

This problem was nagging me and I couldn't figure it out. I checked those links above for workarounds and thought, why not install the newer version that was fixed for Lucid. 

I'm not good at manually installing sw and like Package Manager to maintain what I install/uninstall so I checked Launchpad and there is a PPA there for [Rhythmbox Development]("https://launchpad.net/%7Ejmatthew/+archive/ppa"). 

I added it, ran Update Manager, and now I'm running Rhythmbox 0.12.6 on Karmic. 

I still have to test the DL Podcast bug though. The only podcast I subscribe to is [This American Life]("http://www.thisamericanlife.org/radio_podcast.aspx") which only has one free podcast per week. 

One question I have is how do you get Rhythmbox to see all those other podcasts I downloaded and saved from previous Ubuntu installs? 

If I put my old podcasts in into my Music/Podcasts folder, Rhythmbox sees them as Music files and they are not listed in the podcast list. 

This kinda sucks when you want to play music on shuffle mode and the next song is suddenly a podcast instead of a tune. 

I checked an xml config file somewhere (can't remember the path), and my old podcasts had a music tag not a podcast tag, but I did not want to muff up the entire db file by manually editing entries. 

Please let me know if anyone knows how to get Rhythmbox to list old podcasts in the podcast window. 

Cheers, 
brook

ps i just tested the fix by adding a new podcast, DLed it, and it stays in the podcast list. sweet!

---

