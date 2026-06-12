---
title: "creative killed my linux"
date: 2009-03-29
forum: Multimedia Software
---

### Post by zigga15 on 2009-03-29
Creative has never done much for the Linux community, and I have never really complained, but now I have a reason to.

I followed NullHead's tutorial on installing the creative drivers for an XFI sound blaster Xtream Music:

[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

When I ran "sudo make install" It got stuck at "updating module dependencies". I killed off the process, did an uninstall, and rebooted my box.

Ubuntu would not load because modprobe had failed. Does anyone know how to roll back the changes I made?? Or fix this.

It is worth mentioning that when i compiled the creative source I got a few warnings (although make didn't die).

This is a massive PITA, as you can probably imagine - I am in my windows partition now which seems like one more small victory for M$.

Please help me, I have gone for about 2 years with no linux sound (except on board)... 

And more importantly I really want my computer to boot linux again...

Thanks in advance,

~ Dan

---

### Post by zigga15 on 2009-03-29
Bump,

I still cant boot it up, I can run recovery mode but cannot get X...

Any ideas?

---

### Post by gundam1965 on 2009-03-30
well, your at least 1 step ahead of me. I just installed XFI drivers and Now my linux is completely dead, no linux, no recovery.  Recovery gets stuck at manual drivers.

---

### Post by zigga15 on 2009-03-30
That sucks mate... I was lucky that my grub randomly had another version there...

This is really disappointing, I am not sure if it is my fault or creative but I know I have had to reformat about 3 times because of this.

When I get time I will go through the make file and make sure that it is doing what it is supposed to but I am flat out with other stuff at the moment. Please let me know if you make any progress on the matter. Good luck.

~ Dan

---

### Post by zigga15 on 2009-04-05
Has anyone found a solution to this? I have been trying since the post with no luck. I don't particularly want to change distros.

I have come into a bit of money and I am thinking about buying an alternative sound card that supports linux - do these exist?

---

### Post by zigga15 on 2009-04-15
Bump

---

### Post by markbuntu on 2009-04-15
Pretty much any card that is not creative is supported in linux. There is a huge incomplete list at alsa.org

---

### Post by Sidewinder1 on 2009-04-15
Can't really help with your specific problem. Mine was solved by plugging my speaker plug onto a different port on the Blaster sound card. (It was working fine in Winbloze in the initial port and, currently works fine in Winbloze in the second port) Solved everything. Spent hours with all kinds of poop and that did it! Go figure. One thing I will say, once you've got it working,... don't muck with it... Alot of folks enjoy "tweaking" ...
My current philosophy is "If it ain't broke, don't fix it". I know that's not your ordeal; you're trying to get it to run, in the first place. Be patient, these folks will help as best they can. Sorry I don't have more specific instructions.
HTH 
Side
(Shameless Bump)

---

### Post by zigga15 on 2009-07-08
Sorry for the late reply, I have been too busy with University.

I have solved the problem using temudgin's (Excuse spelling) guide to installing the OSS drivers.

Moral of the story: Do no go for creative if you run unix based operating systems - I regret giving them my money.

It is silly for them to deny the linux community as it is a knish target market that always seems to be running great up to date hardware.

Massive thanks to the open source and linux communities for helping me out with this.

~ Dan

PS. Yes I know they have "Drivers" but they are useless!

---

