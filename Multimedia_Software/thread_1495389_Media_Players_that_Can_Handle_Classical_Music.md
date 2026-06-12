---
title: "Media Players that Can Handle Classical Music?"
date: 2010-05-28
forum: Multimedia Software
---

### Post by Ubuntist on 2010-05-28
Media players generally organize music by track.  If you listen to classical music, that's a bit of a problem, because a classical piece typically consists of several movements (tracks) and you usually want to organize things by pieces, not by movements.  For example, if I'm building a playlist I'd like to be able to add Beethoven's 5th Symphony as such without having to add each track separately.  The Quod Libet player goes part way by allowing one to add whatever tags one likes and to sort on them, but it doesn't provide a way of viewing pieces as a unit.

Does anybody know of a Linux-compatible player that allows this?  I've heard that Media Monkey can do something along these lines, but it's available only for Windows.

---

### Post by cascade9 on 2010-05-28
I'm a little confused as to what exactly you want, so forgive me if I'm mistaken. 

I'd try exaile. It lets you browse your collection by files, not just tags, so if your files are sorted right, you can just go to Beethoven-> 5th Symphony then add the whole lot to a playlist ;)

---

### Post by cchhrriiss121212 on 2010-05-28
Why not just split each album into separate pieces?

---

### Post by Ubuntist on 2010-05-28
> **cchhrriiss121212 said:**
> Why not just split each album into separate pieces?

I tried that, but then I couldn't keep track of albums, and I found that I still wanted to do that.

---

### Post by lazka on 2010-05-30
> **Ubuntist said:**
> ...The Quod Libet player goes part way by allowing one to add whatever tags one likes and to sort on them, but it doesn't provide a way of viewing pieces as a unit.

The **recommended tag** for this in Quod Libet is **"discsubtitle"**. I don't have classical music myself, but I would suggest the paned browser with a setup like: **composer, album, artist or performer, discsubtitle** and of course, a properly tagged library.

With the current development version (2.3) you could also use **"~album~discsubtitle"** which leads to
**"album - subtitle1"**
**"album - subtitle2"**
**"album - subtitle3"** in the paned browser.

---

### Post by frisket on 2010-08-15
> **lazka said:**
> The **recommended tag** for this in Quod Libet is **"discsubtitle"**. I don't have classical music myself, but I would suggest the paned browser with a setup like: **composer, album, artist or performer, discsubtitle** and of course, a properly tagged library.

The problems aren't with the tagging: all my [classical] music is correctly tagged, but there appear to be no players that make use of them properly.

In addition to the OP's requirement to automatically group the movements of a piece, the most fundamental and glaring omission from players is their inability to display COMPOSER and PERFORMER *separately*. It is a great rarity in classical music for a recording to be performed by the composer, and in most cases now an impossibility :-)

From what I have seen, it would be bordering on the trivial to add another few tags to the display and make them selectable. 

Another omission is any distinction between year of composition and year of performance. It doesn't make any sense for my player to show 1966 for Bach's B Minor Mass when it was composed in 1749, and as I have several different recordings, they shouldn't all show 1749: they should show both dates.

Is it too much to ask the authors of at least one simple, competent player such as Totem to make some provision for classical music listeners?

---

### Post by Ubuntist on 2010-08-20
> **lazka said:**
> The **recommended tag** for this in Quod Libet is **"discsubtitle"**. I don't have classical music myself, but I would suggest the paned browser with a setup like: **composer, album, artist or performer, discsubtitle** and of course, a properly tagged library.

Thanks for the suggestion, lazka, but it seems to to me that even if I do this I still won't be able to manipulate entire pieces (consisting of multiple movements) as single entities.  That is, to add Bruckner's Fourth Symphony to a play list, I'll still have to add each of its four movements (tracks) to the playlist separately.

---

### Post by Ubuntist on 2010-08-20
> **frisket said:**
> The problems aren't with the tagging: all my [classical] music is correctly tagged, but there appear to be no players that make use of them properly.

In addition to the OP's requirement to automatically group the movements of a piece, the most fundamental and glaring omission from players is their inability to display COMPOSER and PERFORMER *separately*. It is a great rarity in classical music for a recording to be performed by the composer, and in most cases now an impossibility :-)

From what I have seen, it would be bordering on the trivial to add another few tags to the display and make them selectable.

If I understand you correctly, displaying these tracks *is* possible in Quod Libet.  You can add whatever tags you like to your music, sort on any tags you want, and display any tags.  See Iazka's post (three posts up in this thread).

---

### Post by krapp on 2010-08-22
Quod Libet is nearly there in this respect, but as frisket pointed out you can only have one instance of each tag before the sorting is messed up. For starters there should be two date tags. In any event, part of my reason for leaving OSX was iTunes's decline from a very usable music library organizer to a slow, bloated portal for the latest dispensations from Hollywood and MTV. At least Quod Libet is light and better than most in its organization, and doesn't try to tell me what to listen to a la Genius or Pandora. But count me as another that is still waiting for the media player designed for String Quartets, Symphonies, and Concertos.

---

### Post by Ubuntist on 2010-08-23
> **krapp said:**
> Quod Libet is nearly there in this respect, but as frisket pointed out you can only have one instance of each tag before the sorting is messed up. For starters there should be two date tags.

How about defining two new date tags, say compDate (composition date) and perfDate (performance date)?

I have not done this with dates, but I try use the artist tag this way.  For classical, I set it to the value of the composer tag.  For jazz and pop music, I set the artist tag to the performer's name.

---

