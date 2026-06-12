---
title: "Jamu oops"
date: 2010-04-18
forum: Mythbuntu
---

### Post by uncle hammy on 2010-04-18
This morning I was going through some stuff after upgrading to 0.23.  In browsing through my videos, I noticed that I had a dozen or so missing coverart images / backgrounds that were there last night.  A little more thought, and I realized that all the missing ones were ones that I couldn't download automatically, so I had to manually enter the metadata, images, etc way back when.  

It appears that Jamu is deleting any coverart/fanart that it can't download automatically.

---

### Post by dannyboy79 on 2010-04-19
after you manually enter these within mythvideo, go into the metadata editor and change their inetref to '99999999' so that jamu ignores them. if you read through jamu.py or jamu.conf you'll learn a lot about the script. It's a work of art and I don't even know python.

---

### Post by jbman on 2010-04-19
I am finding some fanart doesn't download, yet i can see it on tvdb and i can see and error about resizing it.

Is this the issue you had as well to make you download it manually?

---

### Post by uncle hammy on 2010-04-20
No, I downloaded manually, because the movies weren't in the online db.  So I had to manually enter all meta data, including the images.

---

### Post by dannyboy79 on 2010-04-20
i know this seems stupid of me but after I answered your question I actually found some home videos that I have which do need me to enter the 9999999 for the inetref number. but when I am in mythfrontend, watch videos, then click "E" on the file I want to edit, I don't see inetref anywhere in there. can you help.

May have answered my own question. I was previously hitting "E" to edit metadata, but I found on mythtv wiki mythvideo, that i must hit "Info" to edit metadata. now i just need to find what key is mapped to "Info".

---

### Post by uncle hammy on 2010-04-25
> **dannyboy79 said:**
> after you manually enter these within mythvideo, go into the metadata editor and change their inetref to '99999999' so that jamu ignores them. if you read through jamu.py or jamu.conf you'll learn a lot about the script. It's a work of art and I don't even know python.
Nope, that didn't do it.  All my videos have the IMDB number or 9999999.  Today, all my manually entered artwork is gone again...time to manually do it again.  Going to have to turn jamu off again.  I don't know why it's doing it, but it definitely is.  I have manually run the script, and it lists all those files as the ones it's removing.  Oddly though, I leaves the references to them in the videmetadata table.

---

### Post by uncle hammy on 2010-04-25
They did have preceding 0's in the inetref column, so I removed them.  We'll see if that makes any difference.

---

