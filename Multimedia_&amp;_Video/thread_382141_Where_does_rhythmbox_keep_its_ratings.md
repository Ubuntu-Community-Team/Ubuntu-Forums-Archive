---
title: "Where does rhythmbox keep its ratings?"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by justinjstark on 2007-03-11
Does anybody know where rhythmbox keeps the ratings that I give to each song?  I would like to copy them elsewhere.

Wouldn't it be nice if the ratings were part of the id3 tag?  Then they would follow the songs everywhere.

---

### Post by bruenig on 2007-03-11
Probably in ~/.gnome2/rhythmbox

---

### Post by justinjstark on 2007-03-11
Okay, so it is in ~/.gnome2/rhythmbox/rhythmdb.xml.  But, I cannot see any easy way to back up the ratings.  If I move my files to another directory and rebuild my library, I will lose my ratings.

---

### Post by bruenig on 2007-03-11
You can edit that file and just change the <location> tags that will keep the ratings.

---

### Post by justinjstark on 2007-03-11
> **bruenig said:**
> You can edit that file and just change the <location> tags that will keep the ratings.

For all 1300 songs?

---

### Post by bruenig on 2007-03-11
> **justinjstark said:**
> For all 1300 songs?

I would hope that there is some pattern to what you are trying to do, so you can use some stream editing to change it in mass.

What do the location tags look like now, and what will they look like after. Give an example of the directory structure you have setup now and what you are changing it to.

---

### Post by medya on 2007-03-17
> **justinjstark said:**
> 
Wouldn't it be nice if the ratings were part of the id3 tag?  Then they would follow the songs everywhere.


I also wish the same, who is in charge of id3 tags ? cant we tell them add it to their tags?

---

### Post by justinjstark on 2007-03-17
> **medya said:**
> I also wish the same, who is in charge of id3 tags ? cant we tell them add it to their tags?

According to [id3.org](http://www.id3.org/Frames), there is no ID3v2 text frame for ratings. But, I see no reason why a ratings frame could not be added in the User Defined Text Information frame.  As it states, "Users can define their own frames, if needed."

So, I might file a bug report in rhythmbox and see what the devs think of adding a ratings tag.  It would sure be nice and would help a lot with migration.

---

### Post by bruenig on 2007-03-18
Rating tags are kind of stupid I think but anyways if you would give an example of what your directory structure for your music looks like now and to what you are changing it, I am sure I or someone else can derive a sed command to change all your location tags so that it will be fine. Or you can continue to complain I guess, whatever you wish.

---

### Post by KaiserMonkey on 2007-07-29
This is quite annoying...every time I change my library folder, it seems that Rhythmbox erases my old ratings, perhaps by overwriting the .xml file mentioned.

Any idea how I could recover "old" ratings or prevent this from happening in the future?

---

