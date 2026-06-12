---
title: "iTunes ratings on Linux"
date: 2009-09-22
forum: Multimedia Software
---

### Post by mikeypizano on 2009-09-22
What is the best way to get my ratings form iTunes onto Linux. I will probably use Rhythmbox, or Songbird if the iPod sync works well.

---

### Post by mikeypizano on 2009-09-24
Bump???

---

### Post by laluz on 2010-02-06
old post, but anyways, in case somebody looks for this still. 
What you could do is to create 5 playlists: one star, two stars, etc. Than just import those playlists and manually rate all files in them accordingly.

---

### Post by tgalati4 on 2010-02-06
No direct way that I know of.  I'm not sure if the method of storing the star rating has been decoded.  Since the iTunes database is a proprietary format, it's difficult to mimic in an opensource fashion.  It also changes depending on what version of iTunes you are using.

iTunes does have a decent printing facility, so you could make playlists as suggested above and print out lists of songs or just try to import the playlists and manually star them.

I think the real issue is that the ID3V2 header doesn't contain star information so that it doesn't travel with the song.  It's stored in the overall music library database but doesn't get exported when you move songs from one music library to another (say songbird to listen to exaile, etc).

Some things to try:

apt-cache search iTunes
sudo apt-get install atomicparsley
man atomicparsley
AtomicParsley --longhelp
AtomicParsley --stik-list

You will see from the above that there is no place for the star rating in any of the tag formats available.  You can work around it by putting a rating in comments or in the "stik" field, or some other little-used field.

Another method is to use Floola and put floola on both the iPod and on your linux machine.  It can parse the iTunes database on an existing iPod.  I haven't tested to see if it can read the star ratings.

---

### Post by laluz on 2010-02-07
> **tgalati4 said:**
> I'm not sure if the method of storing the star rating has been decoded.  Since the iTunes database is a proprietary format, it's difficult to mimic in an opensource fashion.  It also changes depending on what version of iTunes you are using.

When I was interested in this topic iTunes was keeping a copy of the database in xml format. There was a tag "Rating" or something. So the matter of decoding was just grepping the filename and rating out of it. On the Amarok forum you will find a script that does it. 
But really IMHO this all is too much complication.

---

