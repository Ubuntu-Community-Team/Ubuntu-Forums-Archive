---
title: "Xorg 1.7.6 and Kernel 2.6.32-22-generic wont work with ATI fglrx  (Xorg 100% CPU)"
date: 2010-06-06
forum: Mythbuntu
---

### Post by axelfoley on 2010-06-06
Hi All,
   FYI I have been messing around with Mythbuntu 10.04 for 2 days to try to get it working with ATI fglrx drivers.

1st of all when installing mythbuntu 10.04 and selecting the ATI proprietary drivers from the install wizard ..... the install scripts do not in fact install fglrx at al. Upon reboot Xorg barfs and goes into low resolution mode because the fglrx drivers were never installed during the initial install. This happens on the 32 bit and the 64 bit dist.

I am using this against a HD 3450 Graphics card (later I will try later on on a X1950)

2nd when you then install the drivers from either synaptic or natively using ATI's scripts (either binary install or .deb generation) Xorg hangs at 100% CPU upon boot.

I saw a post in a forum on Xorg stating that fglrx simply does not work with 10.0.4 LTS until ATI release a new version of the driver that works with xorg 1.7.6 and the 32 release of the kernel.

Great !

I am now experimenting with knopmyth and Mythbuntu 9.10 as if that post is correct I should be able to get fglrx working on the older Xorg and Kernel version.

Why am I doing this you ask.

I like to run my 42inch LCD TV at native 1080x1920 and the ati drivers only seem to support 1240x740 and badly at that with over scan preventing me from seeing the left half of the screen during configuration.

---

### Post by axelfoley on 2010-06-06
Right, I have tried to install mythbuntu 9.10 x64 ... unfortunatly the install hangs again on what looks like a graphics driver issue ... screen goes blank. I can get further using safe mode graphics .... but that is so small you can not see any of the buttons on the partition screens !!

How difficult is it to get graphiics drivers right these days !!!! At least mythbuntu 10.04
is better in that department at least getting the ati driver to work at 1240x720.. shame about the screwed up fglrx drivers and poor HD3540 support at higher resolutions!
 

Tried to install knoppmyth but their disk partition system was so basic that I aborted as it looked like it was going to wipe my WMCE partition.

So I have now started an install using mythdora 12.23 .. looks like a good well polished dist and is installing fine without any issues so far !

Seems like they have a lot of experience on building a myth distro ... they only support nividia proprietary drivers !

Hopefully I can get the screen resolution to 1080p !

fingers crossed!

---

### Post by axelfoley on 2010-06-06
Nope .... even Fedora is affected by the fglrx driver issue. Although at least Fedora offer a experimental mesa-development driver.

I have given up ..... I am going back to WMCE.

I originally started to use myth-tv 4 years ago when they shelved Tivo in the UK and I wanted to go to 720p. 

Back then it was one  of the worst technology experiences I have ever been through. I got it working but then decided it was such a complete pain in the **** to work with it was not worth it and it was not wife proof. I installed Windows Media Center instead and have since had to put up with their bull*** proprietary controls on codec's.

How far has mythtv come in 4 years ?     Very little in my opinion, the biggest advancement is the support for the WMCE Remote and keyboard.

mythtv sucks! simple and plain ... not because of the product but because of the same old  bul**** with proprietary drivers.

3 days trying to get a Video driver to work and only 5% of that looking at mythtv itself.

Speaks volumes !  If the advocates of "Free as in speech" keep raging their battles with hw manufacturers,  90% of the community who just want the kit they paid for to work are collateral damage.

to paraphrase a well known poet ... 

"there are no hero's in war just dead men " (users who abandon Linux) "and flags"

---

