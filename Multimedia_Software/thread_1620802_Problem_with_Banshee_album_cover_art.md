---
title: "Problem with Banshee album cover art"
date: 2010-11-13
forum: Multimedia Software
---

### Post by smirnoff76 on 2010-11-13
Hi All, 

I am running Banshee under ubuntu 10.10 and have a problem with Banshee and cover art. 
I have in all my album dir's a jpeg called cover.jpg so when Banshee is launched it will use that, however in somecases Banshee fails to use the image resulting in a grey placard or gets the image from the internet. 
Any idea's how I can force it to use the local image?

Thanks

---

### Post by tuppe666 on 2010-12-04
Hi, I would suggest embedding those images inside the mp3s it does add a little to the space, but it helps with working with other players software and hardware. I have been using MP3 gain to do this it wont take long.

---

### Post by ndokos on 2013-02-18
Banshee seems to prefer cached media art images (at least some versions: the one I'm running (2.6.0 on Ubuntu 12.04) exhibits this behavior.

In general, I have found that deleting the cached images allows Banshee to find the Cover.jpg (or whatever) file in the music folder and show that. But there are still some cases, where I get the "unknown art" image, even though there is nothing in the cache and the folder-specific Cover.jpg is fine (I can display it fine, permissions are OK, etc). So there more to be done here, but the following worked in 95% of the cases I've had to deal with.

To delete the cached images, I do some SQL queries to find the artworkID and then go looking for it in the cache directory, (you might have to repair bad line breaks in the following), e.g.

$ sqlite3 ~/.config/banshee-1/banshee.db
SQLite version 3.7.9 2011-11-01 00:52:41
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite> select albumId, title, ArtworkId from Corealbums where title like 'Fidelio%';
439|Fidelio|album-cf0d04f14c4efdfdc82b2d93bb5da4bc
440|Fidelio (feat. Nina Stemme, Jonas Kaufman - Lucerne Festival Orchestra - conductor: Claudio Abbado)|album-5d9fdf9efd13e4389b5acda6c75224c8
sqlite> 

and then

$ find ~/.cache/media-art -name 'album-5d9fdf9efd13e4389b5acda6c75224c8*'

I check them over first by piping the output to `xargs display' and after I'm satisfied, I delete them by piping the output to `xargs rm'. Sometimes I have to restart banshee to make it behave, but most of the time double clicking on the album is enough to show the cover art.

---

