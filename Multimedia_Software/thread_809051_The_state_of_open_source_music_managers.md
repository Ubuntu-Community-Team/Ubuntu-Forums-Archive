---
title: "The state of open source music managers"
date: 2008-05-27
forum: Multimedia Software
---

### Post by raffraffraff on 2008-05-27
I've been a Linux user for a few years, but I'm having difficulty with two final steps before I can junk Windows entirely. One area is obviously gaming, and the other is the lack of a 'suitable' music manager. 

**In Windows I use: iTunes. **
From a useability perspective, I like iTunes. I just like how the interface hangs together, how the songs can be navigated etc. 

**Tried: Practically every music manager available in Linux. **
Problems: Every single open source music manager I have tried is missing some incredibly basic feature that I cannot live without. Or it's unintuitive. Or downright ugly.

*Examples:*
LSongs - Can't handle my library size. Fail.
Songbird - Nice idea, and shows promise, but not ready yet. Too slow and buggy. Fail.
Rythmbox - Can't see 'Comments' tags. Fail.
Banshee - Can't see 'Comments' tags. Fail.
Amarok - Can't edit m4a tags in most distros (eg Ubuntu). Fail.


**What's with the comments tags?**
I find genres too restrictive and, to be completely honest, useless. For example 'Rock' and 'Pop' are such generic terms that they describe nothing about the actual music. Both Rock and Pop can be depressing or happy, uptempo or downtempo, angry or silly. To get around this, I started using the Comments field to tag each song with 'moods'. (I had originally used the 'grouping' field, but found that iTunes only wrote this to its library and not to the music tags, thus locking me in.) With 'moods', I can create a smart playlist for 'Hypnotic AND Dark', and I get stuff like "I wanna be your dog" by The Stooges, or "Manilla Sunrise" by Luzon - two completely different eras and genres, but you know what? They're EXACTLY what I want to listen to at that time.

The comment tag exists in MP3 and M4a specifications, so why is it that practically every music manager I have tried in Linux (with the exception of Amarok, which can't edit m4a tags) can't see them? Doesn't the TagLib have this facility?

**Current Winner - Amarok**
I'm sticking with Amarok, but I'm going to have to compile from source to enable m4a editing. I'm also not crazy about the interface. I know it's incredibly powerful and has a wealth of plug-ins, but I just prefer the way iTunes presents my collection to me. Amarok is too playlist orientated, and that's not how I listen to my music. I like to select a mood, filter it and play it. However, I'm getting over this. 

**CONCLUSION**:
The lack of m4a tag editing in Amarok is a HUGE oversight.
Failing to display / use 'comments' tags in all other music managers is just plain weird. It's there! It's available! Why not use it? Is it difficult to implement?

**TIP FOR TAG EDITING:**
If you've got problems editing tags in Linux, load the latest version of Wine and install the Windows program MP3TAG. It allowed me to remove all of the junk ITUNGAP and ITUNNORM tags that iTunes uses for gapless playback and normalisation, thus allowing Amarok to see the 'proper' comment tags I added.

---

### Post by sicofante on 2008-05-27
I find your way of managing music styles quite clever. I also find the genre tag somewhat idiotic...

It seems [Banshee has a new beta]("http://arstechnica.com/news.ars/post/20080527-rock-out-on-linux-with-the-banshee-1-0-beta-2-media-player.html"), have you tried it?

---

### Post by jabeez on 2008-05-27
maybe I'm mistaken, but doesn't Amarok have a "moods" system built in? I seem to remember seeing it in the options, but never looked into it. Can't look now cuz I'm at work, but just a thought..............

---

### Post by Yellow Pasque on 2008-05-28
Try Exaile. You can also run foobar2000 or Winamp through WINE.

---

### Post by raffraffraff on 2008-05-28
Hi guys - thanks for taking the time to reply.

> **Temüjin said:**
> Try Exaile. You can also run foobar2000 or Winamp through WINE.

Hi Temüjin; I tried Exaile since it's supposed to be a GTK version of Amarok, but it fails to recognise the 'Comments' tag too! I don't understand why this tag is ignored by so many players. I had considered trying foobar2000 through Wine, but I'm really trying to get away from that way of working. I mean, I could just use iTunes through wine either (although it's a bit unstable). 

Nope, I think I'd prefer to bug the hell out of Ubuntu's Amarok maintainers until they enable m4a tag editing by default! That seems a whole lot easier than picking a 'second choice' music manager like Banshee or JuK and asking the developers to implement the 'comments' tag.
However, I will check out that Banshee beta as soon as I get a chance.

---

### Post by raffraffraff on 2008-06-01
> **jabeez said:**
> maybe I'm mistaken, but doesn't Amarok have a "moods" system built in?

Hi Jabeez,
Amarok does have moods (I think it calls them labels?). The problem I think is that these labels are stored in the Amarok database, and not in the metadata of each song. 

I don't want to time huge effort into labelling more than 20k tracks, only to lose this information in a MySQL blip, or when playing music in another music manager.

Thanks.

---

### Post by aeiah on 2008-06-01
ive not really used it myself, but perhaps you could check out quod libet. i use ex falso sometimes for editing tags and such, which is part of quod libet. perhaps it can edit these comment fields for you or something, i dunno. there's a 'description' tag y'know. is that similar?

---

### Post by rainwalker on 2008-06-01
FYI, Amarok 2.0 is in developement so now would be the time to submit a request for what you want.

---

### Post by raffraffraff on 2010-03-04
Wow, that was two years ago. Guess what? Amarok 1.4 was the dog's ********, if you used the Medibuntu version (that could edit the M4A tags) or if you compiled it yourself. So I was blissfully happy until the Amarok team decided to lose their marbles and ditch the best music manager in the world in favour of something that's ugly and lacking in most of the features that I originally chose Amarok 1.4 for. I know that Amarok 2.2.2 is much better than 2.0, but y'know what? It's still not what I'm looking for. Give me Exaile with the comment field and I'll be happy. Seriously. It's 2010. This feature was requested on the Exaile pages in 2008, accepted in 2009 and still isn't available in the latest package provided in Ubuntu 10.04 Alpha. WTF?

---

### Post by b9k9kiwi on 2010-03-04
> **raffraffraff said:**
> 
...

Tried: Practically every music manager available in Linux. 
Problems: Every single open source music manager I have tried is missing some incredibly basic feature that I cannot live without. Or it's unintuitive. Or downright ugly.
...


Me too.

I would agree that Amarok is the best of pretty poor bunch.

Say what you like about Apple (and most people have), their products may well be overhyped, overpriced and underfeatured - but the design is very good.

And so to iTunes, bloatware without a doubt, but I use it my Windows box to run my iTunes Account and maintain a backup of my music library - although I play my music with Amarok.

The latest incarnation of Amarok is anything but intuitive, but it works and looks pretty enough - I agree the limited tag editing is a pain.

I've given up 'the search' - it seems to me that Amarok gives us all that we can expect from open source music management.

---

### Post by Dayofswords on 2010-03-04
why cant you just play music you like, does how it is organized affect how music you like a song?

---

### Post by b9k9kiwi on 2010-03-05
> **Dayofswords said:**
> why cant you just play music you like, does how it is organized affect how music you like a song?

An odd response.

If we were all be so easily satisfied we would all be running Windows?

---

### Post by raffraffraff on 2010-09-06
> **Dayofswords said:**
> why cant you just play music you like, does how it is organized affect how music you like a song?

If somebody deleted all Google indexes and all of your bookmarks, would you be able to "just surf the internet"?  I categorize and label my music files based on their mood, tempo, feeling, instrument etc. So I can search for "downtempo dramatic piano". If a music program does not provide me with a method of using that information, then it's a piece of ****.

---

### Post by gearond on 2010-11-06
I used the comment field for organizing my music also.

'Genre1/Genre2/Etc ###BPM #-Rating(1-5) Mood'


This makes it really easy to sort music in file navigators that display the comment field.

STATE OF MUSIC MANAGERS:
-------------------------------
After all these years, there's still no better music player than MusicMatch 9 (or was it 8, sometime before yahoo bought it and bastardized it for marketing). The only thing it needed was resizable windows like recording/playing queue and skinnability.

If I ever get real money from my near term web development project, I'm going to PAY for developing the best G***AMN music player out there, or build winamp on linux and have MusicMatch skins.

---

### Post by dondiego2 on 2010-11-06
> **raffraffraff said:**
> I've been a Linux user for a few years, but I'm having difficulty with two final steps before I can junk Windows entirely. One area is obviously gaming, and the other is the lack of a 'suitable' music manager. 

**In Windows I use: iTunes. **
From a useability perspective, I like iTunes. I just like how the interface hangs together, how the songs can be navigated etc. 

**Tried: Practically every music manager available in Linux. **
Problems: Every single open source music manager I have tried is missing some incredibly basic feature that I cannot live without. Or it's unintuitive. Or downright ugly.

Rythmbox - Can't see 'Comments' tags. Fail.



I don't understand what you mean.  I have a huge music collection and I can see comments in Rythmbox.  I can edit them, I can sort by them.  Am I missing something?  All I did was edit preferences and click on comment to show in the player.  It pops up a column showing the comment field from the metadata of the mp3.  I can edit and sort by that field.  Maybe two years ago it didn't have this!  I just noticed the original post was two years ago.

---

