---
title: "New to Linux - need to connect image using Crossover Cable"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by IcanBreakit on 2009-03-03
Inexperienced in linux network setup.  I need to image one HD to another.  I have two laptops, the alpha being the one I want to image to the target.  I was going to run Raptor - live CD (only to make use of the GUI) on the alpha.  I also have Helix3 - live CD.  In any case, I can't seem to figure out HOW to network them together using a crossover cable.  I am terrible at network setups and will continue searching while I have this post.

Could someone please help me with the settings of each and more importantly how I can 'see' the target PC using my alpha PC.

Both PC's will be NTFS.  I have a small amount of experience with command line and have used dd and cp for other things, but time is my problem.

I've read some other posts about how to get into the settings, but I don't know how to set them up.  Any help is appreciated.

---

### Post by IcanBreakit on 2009-03-03
OK, replying to my own post.  I was able to get the 'network' completed.  Used a crossover cable, at command line did an - ifconfg...up - and could use both laptops to ping the other.  Now, just trying to figure out how to dd one HD to the other.

Before doing this, however, I did do an apt-get update and then apt-get install nfs-common

Do I have to mount the target? and if so, what is the command?  I have used mkdir before to make a directory which I subsequently mounted (via network and nfs) with an IP.

But, if I want to dd the 'alpha' HD onto the 'target' HD is it as simple as: dd (or dcfldd) if=/dev/sda of=/192.../dev/sda

If I am really messing this up, please let me know.  Again, any help is appreciated.

---

