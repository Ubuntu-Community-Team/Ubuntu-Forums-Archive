---
title: "Custom cover art in Banshee"
date: 2009-07-05
forum: Multimedia Software
---

### Post by divinityofnumber on 2009-07-05
Hi everyone, 

Banshee works amazingly for me, I love it. It finds 99% of my album art with no problems at all. But, for the very rare and obscure, and self-made remixes, etc, I would like to add my own art to the album. For one group of files, I simply put a .jpg file in the folder named "front.jpg" and Banshee used it for the album. But, for some other albums I have done the same thing, but it won't use the picture. Is there some specific size requirement or some trick to doing this?

---

### Post by divinityofnumber on 2009-07-06
*bump.

---

### Post by jeremyj on 2009-07-10
> **divinityofnumber said:**
> Hi everyone, 

Banshee works amazingly for me, I love it. It finds 99% of my album art with no problems at all. But, for the very rare and obscure, and self-made remixes, etc, I would like to add my own art to the album. For one group of files, I simply put a .jpg file in the folder named "front.jpg" and Banshee used it for the album. But, for some other albums I have done the same thing, but it won't use the picture. Is there some specific size requirement or some trick to doing this?

I'd like to figure this out as well.  Some people might find it finicky, but for instance, if a song is on a "Hits" album of various artists, and Banshee displays the compilation's cover, I'd like to see the original album cover instead of the compilation's.

I'm new to Banshee, just switched over from Amarok because of errors, so I have yet to figure this out.

---

### Post by technoboi on 2009-10-13
You can add your own artwork by calling the file 'cover.jpg' and placing it in the same file as the songs.
eg. /home/yourname/Music/bandName/albumTitle/cover.jpg
I downloaded a file, that matched my CD cover. It was a gif, but I just renamed it cover.jpg without converting the file to jpeg and it worked OK.
A practical example is:- 
/home/nathan/Music/the_ot_quartet/hold_that_sucker_down/cover.jpg
(btw... It's from 1994 but Track 4 'Builds like a Skyscraper MixII'is awesome...if you are into dance)

An even better way is to install a program called 'EasyTag'. It automatically tries to sort out the ID3 tags and you can add whatever art you want to any individual song.

---

### Post by Hilbert20 on 2010-12-19
If anyone is having trouble getting banshee to use art that you have stuck in an album directory (over what it initially chose), I have a fix.  Quit banshee and then go into ~/.cache/media-art/ and strip out the offending images.  Make sure that you get them all (including subdirectories).  The next time you start banshee it should find your custom images.

---

