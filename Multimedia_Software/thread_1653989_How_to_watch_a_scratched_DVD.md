---
title: "How to watch a scratched DVD?"
date: 2010-12-27
forum: Multimedia Software
---

### Post by infodroid on 2010-12-27
DVD rentals are a lottery for me. I often have the problem of renting DVD's that end up being scratched. I'm sure this is a common experience: during playback there will be a section of the DVD that is unplayable because it skips or stutters.

I always clean the DVD surface but it often doesn't help when the scratches are bad. So I wonder whether there are any hardware tweaks in Ubuntu to help the DVD drive try harder?

I found this post "[Guide to dvd copy and watch even when scratched]("http://www1.ubuntuforums.org/showthread.php?t=1350012")" which seems useful but it requires ripping the DVD. Any other ideas?

---

### Post by Mr James on 2010-12-27
Try using Brasero to copy the disk as an ISO to your HD and run it from there.

---

### Post by infodroid on 2010-12-29
> **Mr James said:**
> Try using Brasero to copy the disk as an ISO to your HD and run it from there.

That did not work as hoped. The rip operation with Brasero simply stops when it encounters an error and complains about disc being unreadable.

Perhaps something a bit more low-level will work.

---

### Post by trinitydan on 2010-12-29
I almost posted this right adfter you asked, but thought it might be too far from what you were asking, but what about a DVD scratch remover device?  I know they sell them for home use, but I don't really have any experience with them.  I did work in a plastic shop at one time though and when we had slow times in the shop we would buff our scratched CDs on the low speed buffer.  It works great!  Basically, if you hold the disc up to the light and you can see holes through it, that data's gone and it's not coming back.  Fine scratches on the other hand, even across the whole surface of the disc could often be pretty successfully repaired.  This was on a big industrial buffer that stood waist high from the floor.  You'll probably have a hard time finding one of those to use, but maybe one of the home devices could help out too.  There's a variety of them offered online in a wide price range.  Maybe read some reviews?

I've found computer DVD drives to be really sensitive to scratches.  It's particularly a problem with  things like Netflix movies and rentals.  :(

---

### Post by infodroid on 2011-01-01
> **trinitydan said:**
> I almost posted this right adfter you asked, but thought it might be too far from what you were asking, but what about a DVD scratch remover device?  I know they sell them for home use, but I don't really have any experience with them.

I'm sure I would invest in a DVD cleaning kit or jewellery cleaner if it were my own DVD's that were damaged. But I take good care of my DVD's and have never needed to repair them. Having said that, there seem to be a lot of bizarre DIY solutions such as [using toothpaste]("http://www.youtube.com/watch?v=sagr4dLSo88"), [using an eraser]("http://www.youtube.com/watch?v=SHzo8STY7K4"), or even [using a banana]("http://www.youtube.com/watch?v=CS2NMeUBArs")!

---

### Post by infodroid on 2011-01-01
> **infodroid said:**
> Perhaps something a bit more low-level will work.

I was looking for something like the DVD equivalent of [cdparanoia]("http://xiph.org/paranoia/index.html"):

> Cdparanoia will read correct, rock-solid audio data from inexpensive drives prone to misalignment, frame jitter and loss of streaming during atomic reads. Cdparanoia will also read and repair data from CDs that have been damaged in some way.

But cdparanoia does not work with DVD's.

I did eventually stumble across a very good solution using *vobcopy*. I get the impression it is faster than using *dd* but just as reliable in extraction.

I used the following command:

```
vobcopy -v -m
```

The only downside is that the extraction took around seven hours! But the results were spectacular and I could view all the scratched content.

---

