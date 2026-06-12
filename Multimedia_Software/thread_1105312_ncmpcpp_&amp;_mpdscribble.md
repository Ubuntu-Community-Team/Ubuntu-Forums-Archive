---
title: "ncmpcpp &amp; mpdscribble"
date: 2009-03-24
forum: Multimedia Software
---

### Post by hoheyt on 2009-03-24
hello,

how can i change ncmpc++'s colors, i made a config file named ~/.ncmpcpp/config and paste in someone else's config file but no colors has changed. so i figured maybe mine should supposed to be in another directory. where can it be?

and i can't seem to find mpdscribble's configuration file either (if there is one that is, where should i put my username and password?) where is that?

thank you, and sorry if these were answered before.

running xubuntu in windows with WUBI.

---

### Post by Piraja on 2009-03-24
> **hoheyt said:**
> and i can't seem to find mpdscribble's configuration file either (if there is one that is, where should i put my username and password?) where is that?

/etc/mpdscribble.conf

---

### Post by hoheyt on 2009-03-24
> **Piraja said:**
> /etc/mpdscribble.conf

it's not there:(

---

### Post by Piraja on 2009-03-24
> **hoheyt said:**
> it's not there:(
Strange. Should be there, according to **man mpdscribble**. Generally speaking, one of the easiest ways to look for such info is to type **man <name of the application>** in the terminal. Man stands for manual.

You could simply try reinstalling Mpdscribble, I guess. Or copy a sample config file to /etc/mpdscribble.conf. But something seems to be wrong anyway, since the config file is not where it should be by default, so re-installing might be a good idea.

---

### Post by hoheyt on 2009-03-24
> **Piraja said:**
> Strange. Should be there, according to **man mpdscribble**. Generally speaking, one of the easiest ways to look for such info is to type **man <name of the application>** in the terminal. Man stands for manual.

You could simply try reinstalling Mpdscribble, I guess. Or copy a sample config file to /etc/mpdscribble.conf. But something seems to be wrong anyway, since the config file is not where it should be by default, so re-installing might be a good idea.

i removed and installed again, and now it is there o_O and it works, thank you.

i just found out: while browsing through artists in ncmpcpp, it doesn't show the songs of albums which don't have year tags. thats pretty annoying as i have lots of songs that dont have year tag. at least i want to tag all the songs with empty year tags with 2000. how can i do that?

---

### Post by greed on 2009-04-23
I've got a question about mpdscribble..

I have MP3s loaded up with ID3v2 tags, and mpdscribble seems to throw errors such as the following:

```
 [2009/04/24 02:20:55] notice: new song detected with tags missing (A/Anthrax/Anthrax - (1990) Persistence of Time/01. Time.mp3)
```

Other last.fm interface daemons, such as lastfmsubmitd, produce similar errors.. specifically, they claim that the "artist" tag isn't present.  However, many other programs, such as Audio Tag Tool, recognize the ID3v2 and ID3v1 tags, including the artist and title, in the files.  They all connect to mpd and last.fm just fine, but they simply cannot recognize the tags that exist.

So what sort of tags are mpdscribble and other last.fm daemons actually looking for?  Is there a way to write them into the files in a way that they can understand?

Thanks!

---

