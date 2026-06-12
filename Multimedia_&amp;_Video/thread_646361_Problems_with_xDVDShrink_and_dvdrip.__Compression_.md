---
title: "Problems with xDVDShrink and dvd::rip.  Compression is good, but I just want a copy."
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by Mysticle31 on 2007-12-21
I've been looking at DVD copy software for linux. 

I don't like to have stacks and stacks of movies lying around so I like to back them up on large external drives.  That way I can play them on my PC where my TV and and all that is. 

I've tried xDVDshirnk and dvd::rip.  However I find that both of the "mess" with the structure of the movie.  They create folders called AVI and VOB and place files like VOB1, 2, 3..etc in the VOB folder.

I just want a decrypted DVD VideoTS folder on my drive.  I can't just burn that to a disk and go play it in a DVD player if I want to.  And all of my other movies are stored in /Name of Move/VideoTS/file.xxx format.

How can I do this?

I want the capability to shrink and burn if I need to as well.  I can use another program for that.

It would be nice if I could even create ISO images of them.  This was a pain in Windows so I went with folders with the VideoTS.

---

### Post by heidfirst on 2007-12-21
Hi,
Not sure I fully understand your question, but vobcopy may be what you are looking for.

Gordon

---

### Post by Firestone on 2007-12-21
[DVD2HDD](http://linux.softpedia.com/get/Multimedia/Video/DVD2HDD-17412.shtml) sounds like something you're after. It still seems to merge the vob files though.

---

### Post by Mysticle31 on 2007-12-21
> **heidfirst said:**
> Hi,
Not sure I fully understand your question, but vobcopy may be what you are looking for.

Gordon

I re-read it this morning, and it didn't make much since to me either!  I edited it.

I'll give those programs a shot.

---

### Post by incandenza on 2007-12-21
I'm pretty sure the reason there is no application like this is that you don't need an application: you can simply copy the VIDEO_TS directory over using 'cp' or the regular file browser or whatever.

You may have to load the DVD into Totem (or whichever player you use) so it can process the CSS before you do this.  This happens automatically when I insert a disc so I'm not sure whether it's necessary.

Also, you can create an ISO simply using dd, something like:

dd if=/dev/scd0 of=some-movie.iso bs=64k

---

### Post by Mysticle31 on 2007-12-22
I tried that before I started looking for programs.  I found the video was choppy and had may different color pixels, kind of like snow, but it color.

I figured it was still encrypted.

---

