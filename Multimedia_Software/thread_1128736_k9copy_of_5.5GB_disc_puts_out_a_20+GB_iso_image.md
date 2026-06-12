---
title: "k9copy of 5.5GB disc puts out a 20+GB iso image"
date: 2009-04-17
forum: Multimedia Software
---

### Post by jjv on 2009-04-17
A couple of recently released movies are showing some strange behavior in k9copy v 1.2.3

The movie shows about 5.5 GB and will play under totem.  When I open it up with k9copy it shows the main movie in several titlesets each with the approximate size of the movie (4.3 GB).

Even if I configure k9copy for dual layer output (8.8 GB) it runs over 12 hours compressing it but I still get an ISO image on hard drive that is over 20 GB.

Is this some new type of layout that k9copy cannot read correctly or a new form of copy protection?

The two movies that I've seen this with are "Bolt" and "Bedtime Stories"

Any suggestions on getting k9copy to behave as it does the majority of the time?

Thanks

---

### Post by Rev.Willie.Crow on 2009-08-30
I'm having the same problem and cannot seem to find a fix.

---

### Post by servicetech on 2009-09-10
Same here

---

### Post by unckybob on 2009-10-25
I'm having the exact same problem with "Transformers Revenge of the Fallen" another recent DVD release. Please let me know if you find out anything on this. 

Thanks, 
Bob

---

### Post by jjv on 2009-10-26
The issues seems to be with the Sony ArccOS protection.  (Advanced Regional Copy Control Operating Solution).  It is designed as an additional layer to be used in conjunction with Content Scramble System (CSS), the system deliberately creates corrupted sectors on the DVD, which cause copying software to produce errors.

I have tried using ddrescue in conjunction with decss but I have gotten no traction.

I'll keep working through this and post if I run across a solution.

---

### Post by unckybob on 2009-10-29
Thanks jjv. I'll be waiting for you.

---

### Post by mc4man on 2009-10-30
> .....with "Transformers Revenge of the Fallen" 

Titleset 8, title 47

Your best bet with k9 is to do movie only, no orig. menus

Note that with 1 audio stream the orig. movie only size is around 6.5Gb which is a bit of a stretch for a transcoder like k9 to shrink to dvd5. (I guess if your display size isn't too large it would be acceptable

(this isn't ArccOS. just a run of the mill ripquard protection

---

### Post by bhoth on 2009-11-30
any new news on this?

Thanks!

---

### Post by shadetree1 on 2009-12-01
> **bhoth said:**
> any new news on this?

Thanks!

I have been watching and working on this too!  Had to use my wife's puter with DVDfab :(.

But it will backup any of the new DVD's until this has a fix ;).

shadetree

---

### Post by Das Goat on 2010-03-17
Here is sort of an answer. Some of them I have gotten to copy by picking only one title set. It is a crap shoot. some like UP, it was the first title set that looked like the whole move. Bolt looked like it copied, but the disk will only play the menu. I suspect that if I try each title set one at a time I will find the right one.

There is a new twist. Princess & Frog and Ponyo both have a new encription method. When K9 goes to open the disk, it shuts down K9 automatically.

:popcorn:

---

### Post by jjv on 2010-03-18
In doing some testing and looking at trace output I have run into another interesting failure mode.

When you attempt to simply open the movie in k9copy the memory usage ramps up to use all available memory (8GB on this machine) in about 15 seconds. Then is begins to use swap (logical) until it is all used (about 2GB) in about 10 seconds and then the system freezes.

I have had this happen with a couple movies, the latest is "Old Dogs". When you put it in and run k9copy, have a command ready in a window to kill the k9copy process or you will end up rebooting.

Movies that exhibit this behavior will play correctly in the system but just attempting to open the movie in k9copy in order to select which tracks you want to use will cause this memory/swap failure.

If I manage to make any headway I will post it here.

---

