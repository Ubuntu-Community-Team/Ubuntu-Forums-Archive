---
title: "Customizing Banshee to work with my library (may be a tough one)"
date: 2011-06-25
forum: Multimedia Software
---

### Post by GammaScorpii on 2011-06-25
Okay, so I think I've gone through every media player there is out there for Ubuntu, and the one that's come the closest to managing my library the way it's managed in Windows with MediaMonkey has been Banshee - being that at least it *supports* the albumartist tag.

But it still doesn't work as well as I'd like. In the 'artist' tag field I use the semicolon ( ; ) to separate the artists if there are more than one.

For example the artist tag of a particular song may look like this: Blakroc;The Black Keys;Nicole Wray

MediaMonkey would see this and separate the tag so that each of the contributing artists would have this song under their name. Every media player on Ubuntu (that I know of) sees this as one artist in itself, so in my Artist section I could have a bazillion 'artists' who are in fact all the same artists. :confused:

My first question: is there a way to get Banshee (or another media player) to recognize the ' ; ' in the tags in the same way as WMP and MM do?

My other question: is there a way to change which tagging fields Banshee looks for. For instance, when determining the album artist, some media players look for the 'ALBUM ARTIST' tag, others look for 'ALBUMARTIST' while others look for 'BAND'. They all mean the same thing but when your music is tagged in one program, it turns out completely different in another.

---

### Post by GammaScorpii on 2011-06-27
bump

---

### Post by tkiller420 on 2012-01-27
Sorry for pulling up an older thread, but this is one of very few threads I've found that is the same problem I'm having. I recently migrated from windows media player 12 which uses a similar system for contributing artists.

I'm not sure about some of the tagging issues with Banshee, as I'm a Linux newbie myself; however, I've found a reasonable solution for the problem of keeping the list of contributing artists while classifying it under the "main" artist. (At least it's reasonable for my usage.)I felt I should share it. 

It involved a decent amount of work, but what I did was copy the "artist" tag (the one with the entire list of artists) into the "comments" field (or you could use a different field that your media player of choice recognizes, for the record I'm using Banshee as well). After preserving the "contributing artists" I went through and replaced the original list of artists with the single "main" artist.

This is far from a perfect solution I realize, as this doesn't really let you find particular songs by multiple artists except by the "main" artist. It may or may not work under your circumstances, but it's the only way I've found of not having a lot of duplicates for the same artist while still being able to keep the "contributing artists". I hope this solution helps somebody.

---

