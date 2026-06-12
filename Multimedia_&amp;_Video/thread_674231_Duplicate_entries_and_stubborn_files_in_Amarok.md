---
title: "Duplicate entries and stubborn files in Amarok"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by Cravethought on 2008-01-21
Hey everyone.

I'm looking to fix a couple problems around my Amarok. Both seem to revolve around a certain foler in my collection: Rage Against the Machine.

My situation is that I am dual-booting Linux 7.10 and XP Pro. I have 4 partitions on my system, two for Linux and XP, a swap, and the rest is a shared FAT drive between both operating systems.

The files in question are .m4a's, and filed in my /media/hd4/Music/Rage Against the Machine/ directory. Two of the albums show up in Amarok as "Rage Against The Machine" (note the capital T). I try to change the tag in Amarok, and it gives me an error saying "Sorry, the tag for the following files could not be changed:". Even though the files are in a folder with the others, they show up as a separate artist.

The second problem is that all of the songs by the band in both artist sections (RAtM and RATM, for short) show up twice. This is not fixed by the "Clear Duplicate Files" under the Playlist menu, because this is a collection problem. I'm suspecting that it's a problem with the face that they are .m4a's, since this doesn't happen to any of my other music. The songs have permissions to read and write, and because of the space in the directory (/Music/Rage Against the Machine), I couldn't run a **ls -l** on the directory.

Help? :)

Thanks.

---

### Post by Lostincyberspace on 2008-01-21
try copying it your home partition and see if it still works that way if it doesn't fix any thing than it is not what I think, if it does fix it then you just need to have that selection available there.

---

### Post by Cravethought on 2008-01-21
It fixed the duplicate problem, but not the tagging.

---

### Post by kko1 on 2008-01-22
Hello.

Two things.

1) You can do an *ls -l* on the directory, either by quoting the directory, or by escaping the spaces. It looks like this:
```
ls -l "R A t M"
```
or
```
ls -l R\ A\ t\ M
```
Easiest is of course to just use tab-completion after you've written *ls -l "Rage * .

2) For the tags - apparently the files contain both versions of the spelling. I suppose you just need to re-tag the problematic files (to the spelling you prefer) with a tagger that can do *m4a* files. (I haven't really used m4a on linux myself. I don't know why Amarok wouldn't do it - perhaps it just can't.) I'd suggest *easytag*, it at least claims to be able to process also MP4/AAC files.

> Even though the files are in a folder with the others, they show up as a separate artist.
Yes, Amarok (as I presume almost any other sensible player would) bases its display solely on the tags, it doesn't care about the folder structure.

Hope this helps.

kko1

---

