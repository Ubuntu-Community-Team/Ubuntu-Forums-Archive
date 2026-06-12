---
title: "What really happens? Rhymbox slow xfer to Sansa Fuze."
date: 2011-01-25
forum: Multimedia Software
---

### Post by brookie on 2011-01-25
Hi all,

So my son uses Rhythmbox (RB) with his 8GB Sansa Fuze. Got the Fuze USB set to MSC. Mounts fine, and RB sees it fine too. Both MTP and iPOD plugins activated in RB (default don't know why?).

I told him he can drag and drop music to the player music folders because it mounts just fine in Linux Mint 10 (for all purposes Maverick but the Linux Mint 10 install was easier for him). 

Well, he likes to use RB because RB shows it in the left panel, and he likes to drag and drop from RB Music pane to Sansa Fuze,... but it's painfully slow sometimes. 

So, what is really happening behind the scenes? The music really isn't in RB. I think RB just displays the music from the ~/Music folder, via the RB library db at .local/share/rhythmbox/rhythmdb.xml.

So how is RB actually getting the music onto the player? Just an interesting thought. 

Any ideas how this works? Would MTP be faster? 

Cheers,
brook

---

### Post by tommcd on 2011-01-25
> **brookie said:**
> 
I told him he can drag and drop music to the player music folders because it mounts just fine in Linux Mint 10 ...
I have a Sansa Fuze, and this is how I copy music to it Or I just copy music via the terminal to the Fuze.
> **brookie said:**
> 
So, what is really happening behind the scenes? The music really isn't in RB. I think RB just displays the music from the ~/Music folder, via the RB library ...
This is probably correct.
> **brookie said:**
> 
 Would MTP be faster? 

Using MTP (Microsodt Transfer Protocol) may cause the Fuze to not mount correctly in linux. The Sandisk website says the Fuze supports linux in MSC mode.

---

### Post by brookie on 2011-01-26
Thanks tommcd. 

The Sansa Fuze is pretty cool though right? The only reason I got involved was because, it froze up, with an error: "free 90Mb for db or something". 

We couldn't delete files from the Trash.0000 folder. "Read only system error", in Ubuntu. So...

So I plugged it into my machine with WinXP running in Virtualbox and deleted the files I couldn't delete before. 

One was corrupt. Ran chkdsk on it from WinXP. All good now.

Then, I ran Auslogics disk defrag on the main card and the extra 8gb card as well. Those FAT32 cards were really fragmented.

All's good, and now he (my boy) wants to upgrade to something with a larger screen. I got no funds right now, but the new 8gb [Sansa Fuze]("http://www.sandisk.com/microsites/sansafuzeplus/index.html") looks pretty cool. 

Cheers,
brook

---

### Post by tommcd on 2011-01-26
> **brookie said:**
> 
The Sansa Fuze is pretty cool though right?
Yes it is. I like mine a lot. I got the 4GB model and I added an extra 4GB mini SD card to it for a total of 8GB space.
> **brookie said:**
> 
 The only reason I got involved was because, it froze up, with an error: "free 90Mb for db or something". 
We couldn't delete files from the Trash.0000 folder. "Read only system error", in Ubuntu.
I have never had this problem. Are you running the system as root? (You should not). Or are you using sudo to add or remove music files from the FUZE?
Plug in the FUZE and check the file permissions. You should have read and write access to it as a normal user.
> **brookie said:**
> 
Then, I ran Auslogics disk defrag on the main card and the extra 8gb card as well. Those FAT32 cards were really fragmented.
I never thought about the FUZE becoming fragmented. I suppose it does though since it is formatted in fat32.
On the link to the FUZE model you provided, if you click on "Additional Info", it tells you that the FUZE supports linux in MSC mode.
> Windows® XP SP2, Mac OS® X10.3, and Linux (Mass Storage Class only) 

---

