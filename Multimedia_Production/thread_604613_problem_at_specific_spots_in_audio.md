---
title: "problem at specific spots in audio"
date: 2007-11-06
forum: Multimedia Production
---

### Post by felipe de la muerte on 2007-11-06
hello everybody, this is my first post so please be nice :)

lately i decided to move away from windows (once again). everything worked quite fine, i used feisty with the ubuntustudio packages. i only had a problem with jack and ardour, and when gutsy was released i decided to install a seperate system for audio recording (ubuntustudio 7.10), and one for the rest of my work (gutsy). 

well, the problem did not disappear, but got worse.
at some specific spots in my multitrack recording (ardour 2.1), the system gets in real trouble. lots of xruns appear (strange artifacts in the audio, and so on...). then the whole thing gets extremely slow, i have to wait about 5 seconds until the mouse pointer starts moving when i try to do something. usually this won't go away and i have to restart my computer (with the power-off switch). sometimes i get a message that jackd is zombified. then the jack control crashes and everything works at usual speed again.

these things happen always at the same spots in the recording, which have nothing in common. no new regions, no peaks, nothing.

my system is an athlon xp 2200+, 1gb ram, 250gb sata-disk (samsung). 

any ideas what the whole thing is about? :(

---

### Post by deadgobby on 2007-11-06
If Music is your love. Ubuntu studio may not the way to go.  Go and DL Studio 64 live CD. I had too many problems such as midi timing, jackd, and ZynnAddFX with Ubie studio. 
[http://64studio.com/](http://64studio.com/)
Gobby

---

### Post by felipe de la muerte on 2007-11-06
hi gobby, 

thanks for your hint!
i tried the live cd and i have to say that 64studio feels very nice and smooth. it also seems to be way faster than ubuntustudio. i'm able to get much lower latencies, down to 2.9 ms. so i think i'll stick with it!
most of the problems are gone. however, there's still a single spot where the system has some trouble, but at least it does not hang up completely. ardour tells me that my disk can't come up with the data fast enough. still, its always the same single spot. at this time there are only three active tracks (of about 20). i just cant imagine any reason for this, so i'd appreciate any help!

felipe

---

### Post by disturbed1 on 2007-11-06
This sounds like a disc I/O problem. Check, of course, that DMA is enabled. Close file managers (Nautilus). These have file monitors that will *probe* the files displayed to update them. Try to limit all other open/running apps to only the recording application your using at the time.

Use a faster file system, either JFS or XFS. EXT2/3 and Reiser are too slow for continuous data throughput. Reiser is nice for databases that use tons of small files (NNTP server), but fails when it comes to reading, writing, deleting large files (audio/video work)

You may want to look into a simple 3 drive setup. 1 drive for system files, and a 2 drive RAID setup for increased I/O speed to record to.

Run top from a term while recording the audio, see if a program is *topping* ;) out.

---

### Post by felipe de la muerte on 2007-11-06
> **disturbed1 said:**
> This sounds like a disc I/O problem. Check, of course, that DMA is enabled. Close file managers (Nautilus). These have file monitors that will *probe* the files displayed to update them. Try to limit all other open/running apps to only the recording application your using at the time.
i thought of a standard i/o problem, too, but i just don't get why it happens always at the same spot. it does not matter if i play the whole thing from the beginning or if i start just one second before the spot, it's the same problem.
i use a sata-disk, which is seen as a scsi-device by linux (/dev/sda) for some reason. so there is no dma stuff...
> **disturbed1]Use a faster file system, either JFS or XFS.[/QUOTE]
thanks for this hint, i'll use one of these!
[QUOTE=disturbed1 said:**
> You may want to look into a simple 3 drive setup. 1 drive for system files, and a 2 drive RAID setup for increased I/O speed to record to.
good idea, but no money at the time :(
[QUOTE=disturbed1]Run top from a term while recording the audio, see if a program is *topping* ;) out.[/QUOTE]
thx, i'll check that!

---

### Post by disturbed1 on 2007-11-06
HDPARM can still be used to modify /dev/sd* devices.

Just run

sudo hdparm -I /dev/sda

That's an uppercase i, not an L

look for this line under capabilities 
 DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6


The one that is * is the current mode. More than likely it should be enabled. It's been quite a while since there where DMA issues in the 2.6 branch or kernels.

Be very careful using the different hdparm switches. You can run hdparm by itself to get a list of the different options. Remember google, and man hdparm is your friend :)

Once you've tried a different file system, and the issue still persists, I'd head over to [http://ardour.org/forum/15](http://ardour.org/forum/15), or [http://lists.ardour.org/listinfo.cgi/ardour-users-ardour.org](http://lists.ardour.org/listinfo.cgi/ardour-users-ardour.org) to see if someone else might have some insight to your issue.

I also noticed that you're using an older AMD socket A processor. Some of those mother boards that used VIA chipsets were notorious for having issues with PCI DMA conflicts. Where direct memory access would not be handled correctly across the PCI bus. Meaning that video capture cards and audio were not given the necessary resources to  to function 100% correctly. I've been plauged by that issue using different Creative sound cards, as well as a few pro-sumer capture cards. I did a quick search and came up with this [http://www.realworldtech.com/page.cfm?ArticleID=RWT042501034500](http://www.realworldtech.com/page.cfm?ArticleID=RWT042501034500)
didn't read all of it. May or may not be helpful.

---

### Post by felipe de la muerte on 2007-11-09
thanks again, disturbed. i tried different stuff, like using jfs and checking for udma6 (which is active), but the problem won't go away.

i tried to play around with my recording, and found out that there's probably no problem with my system, but with ardour. it gets in trouble when lots of regions end at the same (eg. 5 drum tracks). i'll see if anyone in the ardour forums can help me...

---

### Post by disturbed1 on 2007-11-09
> **felipe de la muerte said:**
>  and found out that there's probably no problem with my system, 


That's the good news :)

If you happen to find a solution, I'd at least post a link to it here. So that others which may have the same issue can fix it as well.

---

