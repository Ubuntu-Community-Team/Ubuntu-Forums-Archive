---
title: "playing DVD"
date: 2012-11-08
forum: Multimedia Software
---

### Post by monkeybrain2012 on 2012-11-08
I am trying to figure out what is happening. I installed Ubuntu 12.04 on an external hard drive and tested it on two different machines for playing DVD. I use the same rented DVD from the neighbourhood video store. In one machine the DVD plays immediately while in the other it doesn't play but I can hear the dvd drive working hard grinding forever and the DVD doesn't even mount.

The DVD drive in the second machine does work though because it can play unencrypted DVDs with no issues. Because of this experiment I think it is not that libdvdcss2 cannot crack the encryption but it is somehow hardware related. I set the region code to be the same in both, now the first one (the one that the DVD works) is really old so maybe it doesn't enforce region codes, but am I correct in thinking that Linux players don't enforce region code anyway and I just need to set it to something to initiate the drive?


For the machine that the DVD doesn't mount, here are the outputs of lshw

```
*-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-L633C
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/sr0
             version: SC00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```


BTW it says status=nodisc, there is actually a dvd in it,--the one that doesn't mount on this machine but plays perfectly on the other with identical Ubuntu 12.04 (because it is the same one booting off different machines)

Some suggestions and insights please? Thanks

---

### Post by monkeybrain2012 on 2012-11-09
I found something yet more peculiar about this machine (where the disk doesn't mount) 

I found another movie that comes in two disks. D1 is the actual film, D2 contains director commentaries and trailers. If I just put D1 in the drive then it just churns forever without mounting the disk. But if I put D2 in it plays right the way and if I remove it and insert D1 again it suddenly plays!!! (i.e have to play D1 after inserting and removing D2)  I have to only do this once and afterwards if I insert D1 it will play automatically even after reboot. But if I insert D2, remove it, play another DVD which is not D1, then when I insert D1 it may not work again (that seem to depend on what dvd I insert after D2, some are fine but others would prevent D1 from mounting) I would need to reinsert D2 and remove it and then insert D1 for it to play.

This is really bothering me, please offer some insights and theories. Thanks.

---

### Post by BicyclerBoy on 2012-11-09
The extras discs are often region "none".
Is the setting region to none a solution?

The region protection is in the licenced OS/player & drive f/w.
The old drive firmwares are RPC1.
Some people report they have to use regionset tool but I would not use except as last resort.

Some drive firmware does allow the required access without region match.

The firmware in tray/slot loading optical drives in laptops/notebooks are often problematic.
Panasonic/matsushita are a problem brand.

Yours is a toshiba/samsung.
I would look/search myce or doom9 for a f/w modding tool & see if auto-region resetting or RPC1 mode works..

I find that after a failed attempt to access a CSS DVD it needs to be ejected/remounted.

---

### Post by monkeybrain2012 on 2012-11-09
> **BicyclerBoy said:**
> The extras discs are often region "none".
Is the setting region to none a solution?

The region protection is in the licenced OS/player & drive f/w.
The old drive firmwares are RPC1.
Some people report they have to use regionset tool but I would not use except as last resort.

Some drive firmware does allow the required access without region match.

The firmware in tray/slot loading optical drives in laptops/notebooks are often problematic.
Panasonic/matsushita are a problem brand.

Yours is a toshiba/samsung.
I would look/search myce or doom9 for a f/w modding tool & see if auto-region resetting or RPC1 mode works..

I find that after a failed attempt to access a CSS DVD it needs to be ejected/remounted.

Hi, Thanks for the suggestions. The drive was originally in region none and I have had some problems with some dvds but setting region really didn't help. I don't know how to set it back to region none because it is not one of the options in regionset (only 1 to 8)

---

### Post by BicyclerBoy on 2012-11-09
From reading here..
[http://club.myce.com/f105/mini-faq-samsung-dvd-writers-220607/](http://club.myce.com/f105/mini-faq-samsung-dvd-writers-220607/)

I think the MSCE tool should let you patch your drive f/w to RPC1.
That looks to be windows only & but you also need dos/win tool to dump & then reflash the modded f/w back.

Make sure you have made an original f/w backup safely stashed..

There are good linux flashing tools for LG drives.

---

### Post by monkeybrain2012 on 2012-11-09
> **BicyclerBoy said:**
> From reading here..
[http://club.myce.com/f105/mini-faq-samsung-dvd-writers-220607/](http://club.myce.com/f105/mini-faq-samsung-dvd-writers-220607/)

I think the MSCE tool should let you patch your drive f/w to RPC1.
That looks to be windows only & but you also need dos/win tool to dump & then reflash the modded f/w back.

Make sure you have made an original f/w backup safely stashed..

There are good linux flashing tools for LG drives.

Thanks for the info, but I have gotten rid of windows long time ago except for a copy in Virtualbox. Anyway, no big deal, just want to find out what the problem may be, it just bugs me. :)

One more question, if dvds play in RPC1 that means css encryption has nothing to do with it, right?

---

### Post by BicyclerBoy on 2012-11-09
don't think region has any direct effect on libdvdcss.

The region protection in RPC1 is player software control/lock. So does nothing in linux.
The problems come from the drive f/w.

AFAIK All commercial DVDs use CSS.
libdvdcss breaks the cryptographic protection by brute force if the generated list of player keys fail.
Being a generated list of potential keys & not actual "stolen" keys is probably why we are still using it.

Brute force is likely causing the disk thrashing noises..

A virtual-box of XP might have problems doing the low level scsi cmds for dumping/flashing f/w.

---

### Post by monkeybrain2012 on 2012-11-16
Hmmm.. This is getting very strange.

I can confirm that it is neither the region code problem nor libdvdcss's failing. Somehow last night I wasn't able to mount even some dvds that I used to have no problem watching before. Trying to access the video with a player on the terminal (vlc) gave some I/O errors, then after popping in and out a few dvds suddenly it worked again, and not only that, it even worked for rentals which I had problem mounting before and again playing them with vlc on the terminal it turned out that one of them doesn't even have region code protection (regioncode 1 to 8, that is, anything should work) I tried my roommates' purchased dvds (which didn't mount before) and they all played. 

So in conclusion Linux plays dvd just fine, it was not libdvdcss's fault, nor does it have anything to do with region codes.

But this morning it doesn't work with the rentals again but still works for the others.

So, it is not libdvdcss, it is not region code, it is not even mechanical thing (otherwise it wouldn't just fail with the rentals) So what are the possible reasons? 

Will try again tonight when I get home.

---

### Post by BicyclerBoy on 2012-11-16
I would suspect the optical drive is stuffed ..laser diodes in cheap drives age badly & are temperature sensitive.

Try cleaning the lens with cotton-bud & meths etc..
But the time & trouble needed to do this is greater than buying a new one.

---

### Post by monkeybrain2012 on 2012-11-16
> **BicyclerBoy said:**
> I would suspect the optical drive is stuffed ..laser diodes in cheap drives age badly & are temperature sensitive.

Try cleaning the lens with cotton-bud & meths etc..
But the time & trouble needed to do this is greater than buying a new one.

Thanks, will try that. It is a slightly less than 4 years old moderately priced laptop, dvd is getting a bit freaky (I suspect it has always been a bit odd) but otherwise everything works great and super fast under Ubuntu so I am not planning on replacing it any time soon.

---

### Post by BicyclerBoy on 2012-11-16
Bear in mind that these problems could be the optical drive f/w..
And the laser lens assembly is very delicate..

You would have to use a DVD playback licenced OS & player to really be sure.

---

