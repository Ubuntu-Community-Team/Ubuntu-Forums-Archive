---
title: "Export from MythTV into MythTV"
date: 2010-01-26
forum: Mythbuntu
---

### Post by R3M3 on 2010-01-26
What's the best way to export (unwatched) recorded television shows (and metadata) from MythTV such that they can be re-imported into another MythTV system?

I don't need to have them show up under TV recordings in the new box, necessarily, I just want to be able to watch them *somehow*. I also am only interested in moving the recordings+title+description. (I don't want to clone/merge the entire database, as everything else is in it is less than worthless.)

---

### Post by johnvan on 2010-01-26
I think what you want to do is go into optical disks> archive>export video files> create native archive, and then select a  file instead of DVD.
The file will have all the metadata so you could then do the same thing on your other system except select import video files when you get there. It's very fast, I use it to put things into mythvideo that I want to keep.

---

### Post by R3M3 on 2010-01-27
Excellent! Just what I was looking for!

The only downside that I can see is that when the recordings are exported in the native format, you have to re-import them one at a time - I couldn't get it to import the entire directory. Do you know of a way around this, or am I stuck doing it one-by-one?

---

### Post by johnvan on 2010-01-27
Sorry, I don't know of a way to do them all at once. I only do 1 show every now and then to export to mythvideo.

---

### Post by bcg30506 on 2010-03-03
I too am doing a bunch of these and found the archive import leaves a few things out.  It fails to restore the recgroup and storagegroup.  I had the recordings separated out into groups to not clutter up Default.  I see the proper group in the <recgroup> tag in the exported xml file.  However, when I import them back, they always go into the Default group, ignoring the recgroup tag value.  Anyone have a fix for this?

---

