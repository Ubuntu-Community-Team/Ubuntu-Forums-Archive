---
title: "Retaining Interface Qualities in .AVI conversions"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by Syndacate on 2007-12-29
Is it possible?

I have a DVD (series DVD, 4eps / DVD, selectable at the main screen in a DVD player).  If I rip the image as a raw DVD format (.iso), I can open it with VLC and still interface with it with the mouse, "Play Episode 1" - "Play Episode 2" - I can select whatever as if it was in a DVD player and my mouse was the remote.

Though when I convert it to .avi format it doesn't retain the "interface" features - it plays straight through.

I would leave it as an .iso except that the .iso is 4.2GB, while at med. quality the .avi is only 1.9GB, and at high it's still only 2.7GB - I'm trying to keep them smaller, you see.

So the way I see it I have 2 options:

1)  I can convert it into .avi and find some program that can hack 'em up and hack the converted .avi off of the .iso into 4 pieces (one for each episode) since it'll play right through.

2)  I can convert it to a file format that will retain the interface options and allow me to select.

Any help on this?  More options I haven't thought of?  Etc.

Thanks in advance.

---

### Post by ron999 on 2007-12-29
Hi
K9copy is designed to shrink a dual-layer movie (or an iso) DVD down to fit on a single-layer DVD-R.
So normally the target DVD size is set to 4400MB.
I don't see why you can't reduce that setting to a different value, around 2000MB.
I think that the shrunk version of the iso will retain the interface options for you to use with VLC but the quality of the video will be reduced.

If you try this method you need to 'Open ISO image' to load your iso. And you need to set Output Device to 'ISO image'.
And use:-

**Settings > Configure K9copy > DVD > DVD size**

to set the size of the output iso.

K9copy is in Ubuntu's repository.

:cool:

---

### Post by Syndacate on 2007-12-29
> **ron999 said:**
> Hi
K9copy is designed to shrink a dual-layer movie (or an iso) DVD down to fit on a single-layer DVD-R.
So normally the target DVD size is set to 4400MB.
I don't see why you can't reduce that setting to a different value, around 2000MB.
I think that the shrunk version of the iso will retain the interface options for you to use with VLC but the quality of the video will be reduced.

If you try this method you need to 'Open ISO image' to load your iso. And you need to set Output Device to 'ISO image'.
And use:-

**Settings > Configure K9copy > DVD > DVD size**

to set the size of the output iso.

K9copy is in Ubuntu's repository.

:cool:

Alright, I'm shrinking an .iso to 2000mb, I'll see if that works, and if it does, I'll compare and see how bad the quality is.

My only beef with K9Copy is that when I was trying to use it to rip DVD's, it simply wasn't working - it would hang and then stop responding, then when I went to "stop" it would say it's not responding, and I'd have to force quit it :( - I'll see if this works though.

---

### Post by Syndacate on 2007-12-29
It completed, but I'm on my way out the door to do some errands, I'll compare vid quality later but from what I just saw it kinda looks like ****.

I'll be back later with the results.

---

