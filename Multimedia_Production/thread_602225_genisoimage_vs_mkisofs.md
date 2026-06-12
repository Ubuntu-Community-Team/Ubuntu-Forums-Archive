---
title: "genisoimage vs mkisofs"
date: 2007-11-04
forum: Multimedia Production
---

### Post by michael37 on 2007-11-04
What is the difference between genisoimage and mkisofs?  Their manpage and options are nearly identical to each other.  Which one should I use?

---

### Post by disturbed1 on 2007-11-04
It should be one in the same. I'll have to check to make sure, but, IF Ubuntu set up genisoimage correctly, mkisofs is only a symlink pointing to genisoimage. Meaning that if you call mkisofs, you actually just using genisoimage.

Genisoimage is a new *fork* of mkisofs. Much in the way of wodim to [SIZE=-1]cdrecord.[/SIZE]

---

### Post by disturbed1 on 2007-11-04
Ok, did a bit of digging for you :)

Turns out Ubuntu does not set mkisofs as a symlink to genisoimage, which is a huge plus. Genisoimage is actually an older version of mkisofs that contains bugs. Ubuntu does have the real mkisofs in the repos though.

The reasons behind the fork are the same as wodim, because of licensing reasons. 

[http://lwn.net/Articles/198171/](http://lwn.net/Articles/198171/)
[http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html](http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html)

I quess that explains why I choose to use Nero Linux, and have zero DVD/CD burning issues, while those that use genisoimage and wodim are hit or miss ;)

---

### Post by michael37 on 2007-11-04
> **disturbed1 said:**
> Ok, did a bit of digging for you :)

Turns out Ubuntu does not set mkisofs as a symlink to genisoimage, which is a huge plus. Genisoimage is actually an older version of mkisofs that contains bugs. Ubuntu does have the real mkisofs in the repos though.

The reasons behind the fork are the same as wodim, because of licensing reasons. 

[http://lwn.net/Articles/198171/](http://lwn.net/Articles/198171/)
[http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html](http://lists.debian.org/debian-devel-announce/2006/09/msg00002.html)

I quess that explains why I choose to use Nero Linux, and have zero DVD/CD burning issues, while those that use genisoimage and wodim are hit or miss ;)

Wow, cool, thank you so much.  

Is growisofs a part of cdrecord or wodim suite?  It comes in dvd+rw-tools which doesn't obviously associate itself with either.

---

### Post by disturbed1 on 2007-11-04
man growisofs states this

growisofs - combined genisoimage frontend/DVD recording program.

---

### Post by michael37 on 2007-11-04
> **disturbed1 said:**
> man growisofs states this

growisofs - combined genisoimage frontend/DVD recording program.

Ah.  That makes sense.  Is there a version of growisofs that is based on new mkisofs rather than old one?  Or is there a way to trick growisofs to use the ?  I kinda find growisofs by far the best and easiest way to burn my DVD backups:

growisofs -dvd-video -dvd-compat -Z /dev/dvd -V "DVD Title" ./

---

### Post by disturbed1 on 2007-11-05
What **I** would do, is link genisofs to mkisofs by doing this -

sudo su
enter your password

cd /usr/bin
mv genisofs genisofs.bak
ln -s mkisofs genisofs
exit

This will rename genisofs, then create a symbolic link between mkisofs and genisofs, so that when ever a program calls genisofs, it actually calls mkisofs.

I'm no expert though ;) If it doesn't work, just delete the symlink, and rename genisofs back to what it was. Or, use synaptic to reinstall genisofs and mkisofs.

You could also, just use mkisofs to create the iso image and burn with what ever you like

mkisofs -V "YOUR_TITLE" -o "/path/file.iso" -dvd-video "DIR/CONTAINING/VIDEO_TS/AUDIO_TS/FOLDERS"

But, using that growisofs command seems easier than the above, and one less step to boot :)

---

### Post by michael37 on 2007-11-08
> **disturbed1 said:**
> What **I** would do, is link genisofs to mkisofs by doing this -
(snip)

But, using that growisofs command seems easier than the above, and one less step to boot :)

You got it -- that's why I use genisofs :)
So far, the DVDs are working, so I am not gonna bother.

---

### Post by David Canarias on 2008-07-23
DISTURBED 1 - It's interesting to read you use Nero now for CD/DVD burning. I have just downloaded the test version to try it as I am getting nowhere trying to burn an mp3 CD from normal Audio. Nothing seems to work for me. In order to try Nero can you tell me how to get my Nero file which is in my downloads file in with all the other programs? I have to use sudo in the terminal I think, but I'm a beginner and totally lost. Many thanks if anyone can help me.

---

