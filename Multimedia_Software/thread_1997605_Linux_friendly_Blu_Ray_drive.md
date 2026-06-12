---
title: "Linux friendly Blu Ray drive"
date: 2012-06-05
forum: Multimedia Software
---

### Post by Kleenux on 2012-06-05
Pretty hard to find a BD player / writer for Linux...

I guess some of the players are Linux compatible, but it's not written on the box.

Any recommendation of a BD (R/W) brand / model that works on a recent Ubuntu?  [ internal preferred, external ok ]

( [COLOR="DimGray"]and an easy way to change the regcod would be a + :cool: [/COLOR])

---

### Post by Kleenux on 2012-06-06
Still looking for a Linux compatible BD drive, thanks

---

### Post by andrew.46 on 2012-06-06
I run an LG BH12LS38 with no trouble, have not tried burning bluray discs with it though...

---

### Post by Kleenux on 2012-06-07
Thanks - any issue with the re9ion c0de5?

---

### Post by CaptainMark on 2012-06-07
is it beginner friendly? last time i checked a year or more ago you needed to get quite hands on with code and compiling to just play blu rays, I cant be bothered with the fuss, if they work out of the box ill reconsider picking one up

---

### Post by Kleenux on 2012-06-07
Captain, it seems the recent Ubuntu plays BD out of the box.

But I live abroad and wonder if regcods will be a problem...

---

### Post by andrew.46 on 2012-06-07
> **Kleenux said:**
> Thanks - any issue with the re9ion c0de5?

I have not yet tried blurays from other regions but [wikipedia suggests]("http://en.wikipedia.org/wiki/Blu-ray_Disc#Region_codes") this is not such a great problem.

---

### Post by Kleenux on 2012-06-07
> **andrew.46 said:**
> I have not yet tried blurays from other regions but [wikipedia suggests]("http://en.wikipedia.org/wiki/Blu-ray_Disc#Region_codes") this is not such a great problem.
Unfortunately, it was the case till a few years (even months) ago, when majors were still pushing the BD to replace the DVDs (in other words, they didn't put a code for BD). Thus the wiki article (that didn't change for a long time).
Recent BDs have a code - and living abroad, using BD from various sources is a pain [ yes, purchasing legally a costly BD can be a PITA when living overseas ].

Moreover, unlike DVDs, the player has to [must] delegate a number of features to the program hard written on the BD. This is again thanks to the majors who trust more their own program than the players firmware [ and this is why sometimes simple features simply do not work because the BD didn't implement them... it's another story :-\" ]

Thus the "hack" is not that simple, as it has to answer the BD requests (following a protocol).

Therefore my worries... 

Some players are easier to control than others - I'd like to purchase one of the "easy" ones ;)

---

### Post by micropit on 2012-08-31
> **Kleenux said:**
> 
Some players are easier to control than others - I'd like to purchase one of the "easy" ones ;)

Hi,

Did you find a good player?
If yes, which one?

Peter

---

### Post by pudlonious on 2012-09-28
I would like to know too.

---

### Post by BicyclerBoy on 2012-09-29
The place to find/discuss this sort of info is doom9 or videolan poss..

I believe the current "good" players are a well kept secret.
This is to protect the player's firmware for as long as possible.
As long as someone has one & feeds the keyDB you're okay with any player.

I suspect one of the current LG players can be flashed with one of the previous "good" player's f/w. Again, go to the source.

The LG drives can be reflashed with linux flash tool. This tool can extract f/w from drive & the firmware update files..

If you don't have hacked firmware you must keep the f/w updated from manufacturer. When f/w updates stop the BD drive becomes a brick/doorstop/DVD-drive. And you have to find alternative ways to get VUKs etc.

If you pay for makeMKV or AnyDVD you should be fine until the drive gets revoked.
BD players are disposable by design.
BD+ could be a whole new ball-game..

---

### Post by nderic77 on 2013-01-01
Quick follow-up questions: do all blu-ray players become obsolete for new movies over time? In other words, does an old ps3 no longer play the latest bd movies?

If I actually find an external blu-ray player for my laptop which works with Ubuntu, will it only play certain movies?

---

### Post by gordintoronto on 2013-01-01
The folks at Tekzilla say the PS3 is the best BD player, because it gets frequent firmware updates. It seems that Hollywood frequently adds new content protection schemes, and old firmware can't play those discs.

---

### Post by Graham C Williams on 2013-01-02
Just watched '5th Element' on Blu-ray. Ubuntu 12.04 64bit, VLC. 
LG player:
 description: DVD-RAM writer
 product: BDDVDRW CH10LS20
 vendor: HL-DT-ST
 physical id: 2
 bus info: scsi@4:0.0.0

---

### Post by ariel on 2013-01-06
> **Kleenux said:**
> Pretty hard to find a BD player / writer for Linux...

I guess some of the players are Linux compatible, but it's not written on the box.

Any recommendation of a BD (R/W) brand / model that works on a recent Ubuntu?  [ internal preferred, external ok ]

( [COLOR=DimGray]and an easy way to change the regcod would be a + :cool: [/COLOR])

FWIW, I have been using an LG WH10LS30 bluray drive for reading/writing BDs for a while in my ubuntu desktop.

I use blu-rays only to burn data backups, not movies. I've burnt very many 25gb disks with no problems. In order to get K3b to burn & verify blurays though, I had to install the cdrecord utilities and get "k3b" to discover cdrecord, running k3b's automatic setup (otherwise, K3b would only produce coasters) - I followed the instructions referenced in post #7 here: [http://ubuntuforums.org/showthread.php?t=2047399. ]("http://ubuntuforums.org/showthread.php?t=2047399")
I have used both BD-R and BD-RE media for backups. I haven't tried any dual-layer (50gb) disk but this drive is supposed to work with them.
I try and avoid what they call "LTH" BD-R disks (which are usually the cheapest)

[]("http://ubuntuforums.org/showthread.php?t=2047399")

---

