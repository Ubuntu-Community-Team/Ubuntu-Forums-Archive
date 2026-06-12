---
title: "mp3s report incorrect length to Amarok"
date: 2010-06-09
forum: Multimedia Software
---

### Post by pmooney78 on 2010-06-09
Some (very few) mp3 files on my hard drive seem to self-report incorrect (much too long) lengths to audio players. I mostly use Amarok, but I've verified that the problem also occurs with other audio players. The files play just fine, but it's annoying that they're listed with incorrect length. Most of my mp3s are encoded using VBR, but I can't imagine that that's a problem ... and if it were, it would be occurring with a lot more files, I'd think.

I'm guessing there's a problem with the file header itself on these files. Is there some way I can check this and correct it, if that is the problem? A quick check through Synaptic didn't turn anything useful-looking up, and neither did a search through these forums. :)

I'm running Ubuntu 9.10 on an HP Pavilion dv 6000 with a Centrino Duo processor and 2GB of RAM. I have the Universe, Multiverse, and Medibuntu repositories enabled.

---

### Post by pmooney78 on 2010-06-11
Bump.

---

### Post by pmooney78 on 2010-06-20
Anyone?

---

### Post by pmooney78 on 2010-08-04
Figured it out. All of the mp3s involved are VBR, and the programs involved were estimating the length of the song based on the total file size and the bit rate of the first frame ... which was incorrect, because the beginning of the songs were quiet. The problem can be solved by the MP3Diags program, found in the multiverse repository. It adds a Xing header to the file, and players correctly calculate the length of the files once this is done.

---

### Post by beerslayer on 2012-06-24
Belated THANK YOU for this post!  I've been having exactly the same problem and it's been driving me nuts (*) for months now.  Your post enabled me to resolve the problem without attempting to re-rip much of my collection.  Now I can sleep at night again!  :)

-------------------------------------------------
* - This reminds me of an old joke:
Woman: (to man) Why d'ye have that steerin' wheel between yer legs, mon?
  Man: It's drivin' me nuts, innit?

---

### Post by pmooney78 on 2012-10-29
Haha. You're very welcome. I'm glad to be helpful.

---

### Post by wildmanne39 on 2012-10-29
Old thread closed.

---

