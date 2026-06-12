---
title: "vobcopy vs mencoder"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by mynameisflorian on 2006-12-22
I don't own a tv so I watch all of my DVDs on my computer. I want to backup my dvds to single-sided DVD-Rs and use and abuse those instead of the originals. First, my system recognises 4.7Gb DVD-R disks as 4.2GB disks. Most of my DVDs are larger than this. I want to try to avoid re-encoding my DVDs whenever possible to preserve the original quality. Many of my disks have alot of extra content that can be droped.

Now, here's the confusing part. When I ripped "Big Fish" using vobcopy the resulting files are larger than 4.2Gb. When I ripped that same DVD using mencoder(see below), the file was small enough to fit on a disk but it aparently did not copy any "seek" information. Also, the resulting avi file would only play in mplayer. I used the following command:

```
 mencoder dvd://1 -oac copy -ovc copy -o Big_Fish.avi 
```
note: I don't have internet at home and am submitting this post from somewhere else. I am 99% shure this is the command I used. Unless mencoder complained I would not have passed any additional arguments.

1) Is all that extra data (i think about 500MB or so) seek information? It looks like vobcopy uses mencoder to rip the DVD.

2) How can I rip this DVD into an AVI container, with seek information, that can also be played using Totem(xine, I belive).

Thanks!
- Florian

---

### Post by OzzyFrank on 2007-07-13
Sorry I can't be more helpful, but I can help address the size of DVDs issue. Firstly, the 4.7Gb is never that, just like 1.44Mb floppies were always 1.38Mb in Windows. One way of thinking it "Hey, let's call a Mb 1000Kb" and the other is "No... let's not... since a Mb is 1024Kb". So a DVD is actually 4.38Gb, and if you can set it in your DVD program as megabytes, specify 4486Mb (most can take 4488Mb, but I found 4486 is safer as that size will definitely fit on all brands of discs).

---

