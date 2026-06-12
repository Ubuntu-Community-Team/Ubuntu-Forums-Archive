---
title: "Cant make copy of my DVD"
date: 2009-05-22
forum: Multimedia Software
---

### Post by GirlofTime on 2009-05-22
Hello,

I'm trying to make a back up of my DVD.  I'm using K3b and have chose to make an exact image only file of the dvd.  It then tries to retrieve all CSS keys.  Then the program says it failed to retrieve all CSS keys.  I have used K3b before and successfully made back ups of my DVDs in the past.  Any idea why its doing this now?  I tried Braseo and the same thing happened.  Thank you  :KS

---

### Post by GirlofTime on 2009-05-23
bump-didaly-bump

---

### Post by ALIENDUDE5300 on 2009-05-23
It may be DRM on the particular DVD you are trying to duplicate.

---

### Post by GirlofTime on 2009-05-26
> **ALIENDUDE5300 said:**
> It may be DRM on the particular DVD you are trying to duplicate.

Dang-or-Rang.  That stinks.  :D.

---

### Post by ricardisimo on 2009-05-26
Is there a way to identify DRM on a disc?

---

### Post by zobcat on 2009-05-26
1. Can you play the dvd you're trying to rip?

2. Have you tried k9copy?

3. If it is an encryption problem, some Windows Rippers can handle the newer encryptions. (DVD2HDD, DVD Decrypter, and AnyDVD)

---

### Post by ricardisimo on 2009-05-26
My understanding is that K9Copy does not make exact duplicates of DVD ISOs, but rather shrunken copies of the DVD. Is this not correct?

---

### Post by zobcat on 2009-05-26
It is capable of doing both.

---

### Post by ricardisimo on 2009-05-26
Fantabuloso. Thanks.

So, what's the story with K3B? No one has even offered any explanation for why it worked before Jaunty, but now it won't. Also, didn't nautilus (with some tweaking) used to be able to back-up DVDs and CDs with just a drag-n-drop motion? Is that no longer an option?

---

### Post by lisati on 2009-05-26
If it's a DVD you've made yourself, it *should* work.
If it's a commercial DVD: be careful of potential legal hassles. In some areas an archival copy *might* be ok but it can depend on local copyright laws and the EULA. (I'm not a lawyer, so don't ask!)

---

### Post by doas777 on 2009-05-26
> **ricardisimo said:**
> Is there a way to identify DRM on a disc?

I hear that gspot works in wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=4541](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4541)

---

### Post by doas777 on 2009-05-26
> **ricardisimo said:**
> Fantabuloso. Thanks.

So, what's the story with K3B? No one has even offered any explanation for why it worked before Jaunty, but now it won't. Also, didn't nautilus (with some tweaking) used to be able to back-up DVDs and CDs with just a drag-n-drop motion? Is that no longer an option?


are you sure you have all the codecs and encoders you had in previous versions?

as for the integration, I seem to recall hearing, that jaunty is the first version to fully integtate braseao, so that may have something to do with it.

---

### Post by andrew.46 on 2009-05-26
Hi GirlofTime,

> **GirlofTime said:**
> I'm trying to make a back up of my DVD.  I'm using K3b and have chose to make an exact image only file of the dvd.  It then tries to retrieve all CSS keys.  Then the program says it failed to retrieve all CSS keys.  I have used K3b before and successfully made back ups of my DVDs in the past.  Any idea why its doing this now?  I tried Braseo and the same thing happened.  Thank you  :KS

I know nothing about K3b and Brasero unfortunately but have you tried vobcopy? It uses libdvdcss and libdvdread as I believe the 2 gui programs do but this might be another avenue to try. I presume this is a commercial DVD?

Andrew

---

### Post by subslug on 2009-05-26
dvdbackup if you're not afraid of the command line. It doesn't shrink and, you may need a dual layer disc to burn it's resulting iso file.

I'm not 100% sure on this but, I don't think it removes encryption either... not that it makes it any more legal but, just sayin.

---

### Post by ricardisimo on 2009-05-27
Everyone is, I think, **_way_** too circumspect about discussing copying DVDs. My understanding is that US copyright law (arguably the most draconian) allows people to make one backup copy of DVDs they have legally purchased. This is fair use, and we can all proceed on this assumption until we receive cease-and-desist orders from a court of law.

Now, downloading pirated copies of films off of the internet is almost certainly another matter altogether... but that's not what we are discussing here, is it?. I'm sorry to vent, but I get real tired real quick of people answering sincere requests for technical help regarding DVD copying with scaremongering legal advice.

You mention dual-layer discs, which brings up another problem I'm having: I've tried Memorex and TDK dual-layer discs, with no success (although the TDKs will at least work in the same disc drive that burned it). Can anyone absolutely guarantee that Verbatim brand DL-DVDs will burn DVD isos successfully? K3B is my preferred app, and I know that brasero has even less success than K3B at burning DL in my system. Thanks for any help.

---

### Post by GirlofTime on 2009-05-28
> **zobcat said:**
> 1. Can you play the dvd you're trying to rip?

2. Have you tried k9copy?

3. If it is an encryption problem, some Windows Rippers can handle the newer encryptions. (DVD2HDD, DVD Decrypter, and AnyDVD)

I just tried K9copy after seeing your post.  It successfully copied the ISO.  But it shrunk the DVD down to 4 gigs.  The DVD should have an ISO of over 7 gigs.  Is there something i need to do in K9copy to make it copy the exact/full ISO?

---

### Post by GirlofTime on 2009-05-28
@ricardisimo

is your picture from Princess Mononoke?  I love that movie.

---

### Post by mc4man on 2009-05-28
> Can anyone absolutely guarantee that Verbatim brand DL-DVDs will burn DVD isos successfully?

I can absolutely guarantee that verbatim dl's burned with Imgburn will always burn correctly and work in any Os//player//hardware (software or standalone as long as they support dl media. (works well in wine with a little time spent to learn

I've never tried k3b for dl's but of all linux burning apps it seems the best.( **by far**

Verbatim dl's are superior, the ones made in singapore are the best verbatims. I'd try not to buy pancakes bigger than 10, occasionally places have a sale on the 3 pack in individual cases, those are the best. (5.99 - 6.99 a 3 pack.

Don't waste your time or money on the -r's, only use the +r's

I'd burn at either 2.4x or 4x, no higher  or lower (burning too slow can be as bad as burning too fast

( one of the **many **advantages of Imgburn is it shows you all the layer break possibilities, rates them and allows you to preview the break



> My understanding is that US copyright law (arguably the most draconian) allows people to make one backup copy of DVDs they have legally purchased.

While that may be true (fair use), dmca doesn't allow the circumvention of copy protections, somewhat of a catch 22

---

### Post by GirlofTime on 2009-05-28
> **ricardisimo said:**
> My understanding is that K9Copy does not make exact duplicates of DVD ISOs, but rather shrunken copies of the DVD. Is this not correct?

Yeah i just made an ISO last night with the DVD in question using k9copy and it shrunk it down.  Seems to be a "bunch" of options though.  maybe theres something i'm missing.

---

### Post by ricardisimo on 2009-05-29
> **GirlofTime said:**
> @ricardisimo

is your picture from Princess Mononoke?  I love that movie.

It is indeed. I would have preferred the toad in the road from *Totoro*, but no one would have recognized it.

The TDK DLs do work after all, but only in higher-end players. I tried the disc out in a Sony BluRay/DVD combo player, and it ran beautifully. Thanks for the details on the Verbatims anyway. Once I run through the TDKs, I'll stick with Verbatims.

---

### Post by GirlofTime on 2009-05-29
> **zobcat said:**
> It is capable of doing both.

How can i get k9copy to copy a full ISO?

---

### Post by mc4man on 2009-05-30
> How can i get k9copy to copy a full ISO? 

Don't have k9 installed, but somewhere in the settings is a place to set the target size, (or similarly named), the default is 4.3Gb 

Just set the size above your dvd size (7.8Gb will suffice

---

### Post by rookcifer on 2009-05-30
> **GirlofTime said:**
> Yeah i just made an ISO last night with the DVD in question using k9copy and it shrunk it down.  Seems to be a "bunch" of options though.  maybe theres something i'm missing.

Go to "configure k9copy" then click on the "DVD" category.  You will see "dvd size" there.  It seems to default to 4.4 GB.  Try changing it to 9 GB (or whatever the correct DL size is).  I have never tried this, but I do know that K9copy says it can do DL DVD's.

P.S. K9copy may not install "libdvdcss2" by default (it doesn't on Fedora, it might on Ubuntu, I don't know).  But if you want to be able to crack CSS keys, you are going to have to have libdvdcss2 installed.  Just apt-get install it.  Otherwise you might find that some modern DVD's will not be able to be copied.

---

