---
title: "Convert DVD to MKV"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by booljayj on 2007-08-01
I've found a site, [http://gentoo-wiki.com/HOWTO_DVD_to_Matroska](http://gentoo-wiki.com/HOWTO_DVD_to_Matroska), which describes how to convert a DVD video to the MKV format. However, this is for the Gentoo operating system, and not everything is the same. For one, I had to search through multiple packages to find the proper binary commands, because no exact package existed. This is what I have so far:

```
#Rip DVD to a .VOB file
mplayer dvd://${TITLE} -dumpstream -dumpfile ${RIPPATH}movie.vob

#Create a text file defining the chapters and edit the names of those chapters manually
dvdxchap -t ${TITLE} /dev/dvd > ${RIPPATH}chapters.txt
gedit ${RIPPATH}chapters.txt

#Copy the file which defines subtitle placement and color
cp /media/${MOUNTPOINT}/video_ts/vts_01_0.ifo ${RIPPATH}
```

Any further than that requires some use of the command 'tccat' and 'tcextract'. I searched through the package database and found no sign of either of these commands. Does anyone know how to do this, or has anyone created a program to do this sort of thing? MKV seems to be the perfect format for those that want their DVDs as close to the original as possible, and I really hope it becomes a popular standard in the future.

---

### Post by david_2001 on 2007-08-02
tccat and tcextract are part of the transcode package.

---

### Post by booljayj on 2007-08-08
Yeah, I found that out after some trial and error. Also, I've found a better way to do this: OGMrip. It's a pretty good program, but it's not made for Ubuntu. I found a modified version on getdebs.com. I like the program, but I wish it had some more options. It basically does everything on that howto with a nice, easy to use interface.

---

