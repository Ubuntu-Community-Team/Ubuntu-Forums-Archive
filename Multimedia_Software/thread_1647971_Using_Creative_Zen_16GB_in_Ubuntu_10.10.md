---
title: "Using Creative Zen 16GB in Ubuntu 10.10"
date: 2010-12-18
forum: Multimedia Software
---

### Post by BCMerlin on 2010-12-18
A few weeks ago I switched from Windows to Ubuntu 10.10 and since then I don't know how to use my Creative Zen player anymore. I used to have certain software for this but that's Windows required. I tried to install it via Wine, but Ubuntu doesn't even want to take a look at it. And I have to admit I haven't used Wine before so I don't know exactly how to arrange it.

[I]What do I want primarily with my Creative Zen?

[/I] Arranging audio on my mp3 player.
Adding audio from my laptop to my player.
Arranging, editing and adding playlists.

When my player is connected with my laptop I am able to see it.

*Thoughts and questions I have:*

-Is it possible to do all this via Wine, but why doesn't it seem to work?
-Which codes do i need when I try to fix this via terminal? And do I need some extra packages or something like that?
-I read several things about using Rythmbox or Banshee instead, but I don't know how cause Rythmbox doesn't read my player and I think it's a very chaotic prog. Maybe some one can guide me through this or give a good alternative?

Hope you can give me some essentials.

---

### Post by Raff1 on 2010-12-18
I have very much the same issues. I hate to boot into windows every time I am going to add something to my player. I have tried dragging mp3 files directly into the file hierarchy of the player, which I can browse in Ubuntu, trying different folders. However, it seems the files aren't being included in the library, so I can't access them in the player. Editing playlists seemed to be doable though, and one could easily make a little python program to do the job. However, you need to have the music files on the player and in the library already.

Does anyone know if it exists alternative firmware which is Linux compatible for these players? Are anyone able to hack the settings a bit, for example making the dj "rarely heard" being "rarely heard and not one star"?

The main issue is ofc being able to drag music to the correct folder and adding it to the library and editing playlists. I will look a bit into the details of the latter today.

---

### Post by gordintoronto on 2010-12-18
> **BCMerlin said:**
> When my player is connected with my laptop I am able to see it.


So you should be able to copy and paste songs back and forth between your computer and your MP3 player.

I suggest you Google: zen playlist linux

---

### Post by Raff1 on 2010-12-18
> **gordintoronto said:**
> So you should be able to copy and paste songs back and forth between your computer and your MP3 player.

I suggest you Google: zen playlist linux
Yes but where to put them? They must be integrated with the library as well somehow. The tracks I tried dragging over to various folders don't show in the browsing hierarchy of the player.

---

### Post by cottfcfan on 2010-12-18
I have a 16 GB Creative Zen and it works great with Rhythmbox.
Open Rhythmbox, plug in your Zen. You'll see it open on the left hand side of the Rhythmbox window. Then you just drag & drop the albums/songs you want from the playlist and onto the Zen icon. Done.

---

### Post by Raff1 on 2010-12-19
> **cottfcfan said:**
> I have a 16 GB Creative Zen and it works great with Rhythmbox.
Open Rhythmbox, plug in your Zen. You'll see it open on the left hand side of the Rhythmbox window. Then you just drag & drop the albums/songs you want from the playlist and onto the Zen icon. Done.

Thanks! It finally worked after I realized I first have to open Rythmbox, THEN connect the player. Otherwise the player gets mounted on the desktop and Rythmbox can't access it... :S

This solution made it very easy to rip audio-CDs and drag them to my player afterwards. However, I am unable to make a playlist consisting of tracks on my player. It was simply impossible if they weren't stored locally. And I was unable to locate and edit existing playlists on my player. So Rythmbox was only suitable for ripping music/transfering to player/syncronizing player.

I am currently looking into these options for making/editing playlists (the second must obviously be tested in Wine):

> **labinnsw said:**
> Forget Gnomad, Rhythmbox, Bansheee, etc if you have a Creative Zen Style 300

To make playlists, sort your files into subdirectories in the Music  directory. Each subdirectory should contain the files you want in a  particular playlist. (So name the subdirectories accordingly)

[Follow this link]("http://forums.mycreativefansite.com/zen-style-100-300/zen-style-playlist-problem/msg29912/#msg29912")  (make sure to read page 2) to obtain an application that will create  your playlists and instructions on how to install it and get it  working.

---

### Post by haircat on 2010-12-20
haircat

Rhythmbox on sound & video but does not start up

---

### Post by Raff1 on 2010-12-23
> **haircat said:**
> haircat

Rhythmbox on sound & video but does not start up
I had a problem with Rythmbox crashing if the player was already recognized/mounted or something like that. Most times it just reported that it couldn't load the device.

First open Rythmbox, then plug in the player. That worked for me :)

---

### Post by Leighman on 2011-01-02
There's an open bug report for this problem with Creative devices at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/493701](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/493701)
Might be worth mentioning that it also affects these newer ones

---

### Post by MelloNello on 2011-01-25
Not sure if this is any use, but I was having some mp3 tagging problems on Ubuntu (Ubuntu 10.04 LTS Lucid Lynx) with the 16Gb Creative Zen MX.  After trying a few different programs, the only one that worked properly for me was the **MP3 Diags** one (available from the Ubuntu software centre).  For some reason, all the others produced ID3v2 tags that were readable on the computer, but the Zen couldn't see them, so they all ended up under "Unknown Artist".

The good thing about the MP3 Diags program is that you can search a couple of different music databases, which often have the album art, which you can then tag your files with in one go, which is handy.

Anyway, hope that's of use to someone, it took me a few days to stumble upon it.

---

### Post by psychok7 on 2011-06-14
hi, i am thinking of buying a Zen Style 300 CREATIVE , can i mount it in ubuntu 11.04 and drag and drop without having to open with banshee or any other program?

---

