---
title: "PC Upgrade advice pls!"
date: 2008-05-01
forum: Mythbuntu
---

### Post by Al_Vampyre on 2008-05-01
Hi there,

Happily running 8.04 (great work guys) but I'm just about to do a couple of things to my media centre box and wondered if someone could clarify a few things for me.

Currently running a P4 2.4 with 1Gb of DDR400 and a single 250Gb IDE disk along with a Nova T 500 PCI dual DVB-T tuner. My gaming system is just about to be upgraded (woot!) so I was going to transfer the old gaming system to my media centre box, add another disk, and another tuner to the mix. New media centre would then be;

Asrock 939 Dual SATA Mobo
Opteron 165 @ 2.4Ghz
4Gb of DDR400
nVidia GeForce Fx 5200 (AGP)
2 x WD 500Gb SATA HDD's in RAID1
2 x Nova T 500's

So my questions are;

1 - Any issues with the specs above?
2 - Given the 4Gb memory I would prefer Mythbuntu64 - any issues I should know about?
3 - Is it at all possible to do this non-destructively? My other half has a lot of recordings on there and a lot of scheduled recordings coming up. Is it just a matter of backing up the recording and home folders and then putting them back once the upgrade is done? If not, is there any way I can do it? Obviously I'm a bit concerned that moving from 32bit to 64bit may screw this up anyway.
4 - **RAID Question now answered, thanks guys!**
5 - Will Mythbuntu automagically pick up both Nova T 500's or will this require some extra configuration on my part?

Thanks for taking the time to read this and thanks in advance for any help or advice you can give.

---

### Post by njparton on 2008-05-01
You probably won't be able to use the onboard raid as linux drivers wont exist.
 
You can do software raid in linux, I'm sure someone else will chime in about that.
 
My advice though would be to invest in a cheap highpoint software raid card (most have drivers available) or if you can afford one, a 3ware hardware raid card.
 
I run the amd64 distro with 4GB RAM with no issues.
 
Good luck!

---

### Post by bah1976 on 2008-05-01
I'll chime in on the RAID, based on my research to this point.  I too am building a myth server that will be my primary file server &  myth box, and I'll share what I've found so far.  My plan is to have 3 500GB drives in a RAID5 array, mostly for the redundancy & increased capacity of 1TB, so it's a little different than what you want.

I will agree that the onboard RAID will probably not work.  Everything I've found in this forum & other linux forums say to stay far away from it.  Drivers are not likely to work, and even though the RAID is built into the MB, it's actually a software component that does the RAID work.

Second choice is a hardware raid card - the problem there is cost & available slot in your box.  I had been considering a LSILogic raid controller that retails for $300, way more than I wanted to pay for this project.  However, to answer your question - if you have an appropriate raid card, you configure the array at boot time through a (probably) BIOS or CD-based utility.  Once you configure the RAID1 array there, you load the LSI or 3Ware driver in linux, and it should see it as a single disk.

Third choice, and what I am going to be doing, is use software RAID & LVM, based on instructions from this site:

[http://www.gagme.com/greg/linux/raid-lvm.php]("http://www.gagme.com/greg/linux/raid-lvm.php")

This seems to give me the best of all worlds - no high-priced RAID card, redundancy of RAID5, capacity of 1TB, flexibility of LVM...  I should mention that this is all based on theory, I have not actually tried it yet - the test will come over the next few weeks as I acquire hardware and start building.  I am not a linux expert (yet) so it's also possible that this won't work on Ubuntu, although my gut feeling is that it will.


On the other question of destructiveness, I've been thinking about that.  I have a old crappy box that I have built as a test to see how mythbuntu installed, and I have a couple things on there now.  What I've been contemplating is installing my new box on completely different hardware as a second back-end, and then doing some hocus-pocus to switch the primary role over to the new box.  I haven't figured out how to do that yet (because I've just been thinking about the idea while driving) but it seems viable.  If you could get two myth boxes as related backends, then the scheduled recordings should (in my mind) stick with the primary role.  But that's all in my head - I've seen information that talks about how to back up and move the database (which holds all the scheduled stuff) and the recordings are just files - copy them and it might work.  It doesn't look like you're re-using the 250GB drive, so you could probably pop it into the new server and just copy the data around that way.

Disclaimer - I have not yet built a fully functioning mythbuntu box - I may be way off base and talking out of my a$$ - so make sure you work carefully and have a backup - just in case...

---

### Post by njparton on 2008-05-01
Unless you buy a cutting edge 3ware card, the drivers will be built into the kernel. No installation necessary.
 
If you've got deep pockets, 3ware is the way to go.

---

### Post by bah1976 on 2008-05-01
Agreed - hardware raid is by far the best option.  I don't think I made that clear enough...  With software raid (including the built-in MB RAID) the CPU does the RAID work, which may take a toll on performance.  Hardware RAID cards do that work and do not impact your processor.  The ONLY reason I decided not to go with the hardware RAID was cost.  

<edit> Of course, if all you want is RAID1 with 2 SATA ports, that lowers the cost significantly.  I was looking at the 4-port - 8-port range of models because of my RAID5 config, which are pricey.  2-port cards aren't nearly as bad.  It all comes down to cost & future expandability, in my opinion.  With a two-port RAID1 card, there's no room for expansion.

---

### Post by Al_Vampyre on 2008-05-02
Thanks guys, having just spent a lot of money (for me anyway!) on my gaming machine I'll probably go down the software raid route.

Anyone know the answer to the other questions?

Thanks

---

### Post by njparton on 2008-05-02
You may need to re post with just the remaining issues in as this has become a bit of a raid oriented thread.  Once threads get to a certain size a lot of people will skip over them thinking they've been solved.
 
Check out ebay for cheap used highpoint software raid cards :wink:

---

