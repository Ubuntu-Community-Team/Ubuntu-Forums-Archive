---
title: "Ripping flac with SoundJuicer results in inferior sound quality"
date: 2021-04-03
forum: Multimedia Software
---

### Post by lister171254 on 2021-04-03
I ripped my CD collection to flac a fair way back using Grip and never had any issue.

I recently decided to repeat the progress to take adavantage of the improved metadata avaliable via MusicBrainz.
As Grip isn't available any longer (I'm now on Ubuntu 20.10), I used SoundJuicer to rip to flac and Picard to get the correct metadata.

I checked the initial few CDs and everything seemed to be ok, but after ripping my entire collection, I now find that some of the flacs are skipping and that's on all devices I try and play the file(s) in question.

I have no explanation for this and would appreciate any feedback.

Thanks

---

### Post by CatKiller on 2021-04-03
> **lister171254 said:**
> I checked the initial few CDs and everything seemed to be ok, but after ripping my entire collection, I now find that some of the flacs are skipping and that's on all devices I try and play the file(s) in question.
If the cds are scratched or there's dirt on the lens then the signal that's dutifully and perfectly translated into FLACs will have skips. Error correction can only do so much. That's my first thought.

---

### Post by The Cog on 2021-04-03
It may be worth trying Asunder - the default utility provided with Xubuntu. I have used that a lot over the years.
But I agree with CatKiller that this could just be deterioration of the CDs or the player over time.

---

### Post by vanadium on 2021-04-04
This is where secure ripping is needed. It there is an error, such software will retry until a consistent signal is obtained, and if that fails, at least you will know there was a problem with the specific rip. SoundJuicer does not do secure ripping at all: it just reads and registers anything that comes in. cdparanoia is a command line tool designed for more errorproof ripping. Rubbyripper was a graphical tool with focus on accurate ripping, but I do not know if it still is around.

---

### Post by lister171254 on 2021-04-06
Didn't Grip use cdparanoia?

---

### Post by Dennis N on 2021-04-06
If you're willing to venture outside Ubuntu Land, at least temporarily, grip is alive and well on some other distros - Fedora is one example. Below is grip in Fedora 33 workstation.

I replaced freedb.org with gnudb.org, and that worked ok in a very limited lookup test of two cds. One shown below.

---

### Post by lister171254 on 2021-04-07
Found the issue. I don't know why, but the fault is on the CD and no amout of error correction will fix this.

Given that I didn't play the CD after I ripped them years ago and they were in a secure box, some seem to have deteriorated.

Thanks

---

