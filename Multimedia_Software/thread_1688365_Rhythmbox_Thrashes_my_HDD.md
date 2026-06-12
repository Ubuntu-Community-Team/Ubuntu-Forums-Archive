---
title: "Rhythmbox Thrashes my HDD"
date: 2011-02-15
forum: Multimedia Software
---

### Post by ffixcollector on 2011-02-15
I enjoy the features of rhythmbox, but whenever I load rhythmbox it eats up my HDD for about 7 minutes. Is there anyway to make it stop? I have 130gb of music and have already unselected the "monitor folders" box.

---

### Post by Koffeehaus on 2011-02-15
> **ffixcollector said:**
> I have 130gb of music

Deewd!!! It took me like 4 years to salvage 14 gigs of music I have!

But what I do is use VLC media player and then drag and drop the folder with music I want to listen to into the playlist box. Not that my Rhythmbox lags when scanning the folders, it's more of legacy habbit, when it DID lag on Windows. Using VLC as my prime player ever since.

---

### Post by Kirboosy on 2011-02-15
If you didn't have so much music it wouldn't lag like that. I would recommend cleaning out your music folder. Less than 50 GB would probably run alot better. I'm sure you have some duplicate songs you could remove.

You could always try banshee or amarok just to see if they do the same thing. (I have a feeling they will)

---

### Post by tgalati4 on 2011-02-15
Time to break up your music collection:

Put all of your death metal in one directory then use Amarok to listen to it.

Put all of your speed metal in another directory then use Exaile to listen to it.

Put all of your cookie-monster metal in another directory then use Rhythmbox to listen to it.

Put all of your Klingon Metal in another directory and use Listen to listen to it.

Or get a faster computer.

---

### Post by ffixcollector on 2011-02-25
Are their any helpful tips anyone can give me? If I wanted to work around the problem, I'd keep doing what I'm doing.

---

### Post by Hawkoon on 2011-02-25
I think number of files is more relevant than the overall size of the music collection. I have +15000 songs (+90GB) and Rhythmbox scans for about 20-30sec with the "watch folder" option on. That is with Rhythmbox version 0.12.8 on ubuntu 10.04.2, powered by an old laptop with Pentium M 1.6GHz, 1GB RAM. System resides on a slowish USB stick, data sits on an external USB 2.0 drive. System and data are fully encrypted, so really not a high-performance setup.

I have configured Rhythmbox to use several folders, like music, audiobooks, education... but I cannot see that making a difference.

So I can only think of issues like filled up drive/file fragmentation, slow hardware or a software version issue.

---

### Post by ffixcollector on 2011-02-25
I only have 5500 songs, maybe I have to many watch folders? I am running Rhythmbox 0.12.8 on Ubuntu 10.04. I also just migrated to a raid 5 setup. But have not seen much improvement with Rhythmbox.
I have 7 playlist which I added songs to by doing the old "drag and drop" method.

---

### Post by Hawkoon on 2011-02-26
Maybe you can use iotop, lsof and fuser to investigate further how exactly rhythmbox is keeping your drive busy?

What is the normal read performance from your music drive? For pure read performance testing  I setup a folder and copy the content to /dev/null

```
time for FI in *; do cp $FI /dev/null ; done
```or I rsync couple of folders to RAM (/dev/shm/)

```
rsync -av /source /dev/shm/test
```

---

### Post by cascade9 on 2011-02-26
Or you could use a media player that doesnt do that library scanning at all. Thats what I do.

---

### Post by ffixcollector on 2011-02-28
I've tried IOTop before, but I might give it another go. What other media players are recommended? I have used songbird before, but it is no longer supported.

---

### Post by cascade9 on 2011-03-01
I'm using deadbeef. If you actually liked songbird then deadbeef might not be for you, they are very different players.

---

### Post by ffixcollector on 2011-03-01
The screenshots look pretty good. What else can you tell me about it? How do I install it? Does it work with logitech's media keyboards? Have you had any problems with it?

---

### Post by Hawkoon on 2011-03-02
ffixcollector, did you see this thread?
[HTML]http://ubuntuforums.org/showthread.php?t=1204619[/HTML]Maybe you use some odd codecs amongst your songs and "resetting" your library works for you as well?

---

### Post by ffixcollector on 2011-03-04
I actually switched to deadbeef, it is simple, gets the job done, is very configurable, and sounds beautiful. With the right settings it sounds better than rhythmbox.

---

### Post by Hawkoon on 2011-03-05
Just had a look. I actually like deadbeef's interface, especially the quick info on selected song at the bottom. It doesn't support lirc, daap and jamendo yet though. Some of this stuff has been requested already, so I'll keep an eye on deadbeef.

---

### Post by cascade9 on 2011-03-06
> **ffixcollector said:**
> I actually switched to deadbeef, it is simple, gets the job done, is very configurable, and sounds beautiful. With the right settings it sounds better than rhythmbox.

The simple interface is why I though that it might not be your thing, its very different from songbird. 

I'm glad you like deadbeef, its a great little player. Its replaced foobar2000 in WINE for me. 

Now I just need to fiure out how to get the album art display to worth with bitmaps. Or replace my album art .bmps with .png/.jpg/.jepg.

---

