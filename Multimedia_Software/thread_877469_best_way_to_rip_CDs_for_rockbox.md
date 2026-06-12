---
title: "best way to rip CDs for rockbox"
date: 2008-08-01
forum: Multimedia Software
---

### Post by nomis3613 on 2008-08-01
Hi,
Just thought I'd put the question out there to see if there's a less convoluted way of getting my CDs onto my Rockbox player. Here's what I do currently

1) Rip CD using SoundJuicer, which automatically downloads track names
2) Rename tracks using Bulk Rename to change "14 - Italian Leather Sofa.ogg" to "14 Italian Leather Sofa.ogg". I can't find a way to change this setting in SoundJuice (and, yes, I am obsessive compulsive...)
3) Cover art using AlbumArt-qt. Rockbox doesn't do album art resizing yet, and this is the only program I've found that lets you choose the output size.
4) Occasionally I scan all my tracks in Foobar2000 (using my Windows PC at work) to assign the AlbumGain tags so that all my albums are similar volume.

I haven't really investigated Foobar2000 much but I might get it working under Wine sometime and see if it can remove some of my steps above.

Any suggestions for programs that will reduce my 4 step process? (sounds petty, but I'm ripping my 300+ cds which is quite a task!)

Thanks,
Simon

---

### Post by vanadium on 2008-08-02
My workflow is different but as convoluted.

2) The "Rename" step can be well configured in Rubyripper, which I am using for the moment. The tagger "easytag" allows you to rename files according to the tags, but this remains an extra step.
3) I am even more primitive in my cover art: I look it up with my browser and fetch it from internet sites. I do not care for resizing for the moment: I just attempt to get the largest size/best quality I find.
4) For replaygain, there is a Linux native solution:

for f in *.ogg ; do vorbisgain -a *.ogg ;  done

---

### Post by nomis3613 on 2008-08-02
Thanks for the suggestions, Vanadium. I forgot to mention, but I also use Media Monkey on my work PC. It doesn't put the dashes in filenames, so that would remove a step. But, alas, Windows only.

---

