---
title: "64 bit vs 32 bit"
date: 2008-12-05
forum: Mythbuntu
---

### Post by NautiusMaximus on 2008-12-05
Hi All

I'm in the process of building an HTPC to run Ubuntu + MythTV, which is based on an AMD Phenom processor, so I could use the 64 bit version of Ubuntu. The question is, should I? Could anyone point me to the advantages and disadvantages of 64 bit vs 32 bit?

I'll be using the PC mainly for watching DVD movies and recording and playing back TV, but also for listening to music and looking at photos. Not planning to do much if any gaming.

Thanks
NM

---

### Post by squaregoldfish on 2008-12-05
Try the x64 forum - there's endless discussions of this topic in there.

Steve.

---

### Post by ian dobson on 2008-12-05
Hi,

I have a feeling that transcoding from MPEG2 to MPEG4/NUV is quicker on my 64bit backend than my 32bit frontend/temp slave backend even though the frontend is 200MHz quickeror core.

These days 64bit is no problem apart from afew programs (Flash for example). For a pure Myth box I'd say go 64bit.

Regards
Ian Dobson

---

### Post by Perfect Storm on 2008-12-05
Flash is not a problem anymore. There's a 64-bit version now (still beta but works great).

---

### Post by 4dognight on 2008-12-05
> **NautiusMaximus said:**
> Hi All

 Could anyone point me to the advantages and disadvantages of 64 bit vs 32 bit?



I don't think the question was, can mythtv run in 64 bit, but rather , why would you want to run it on 64 bit. I have asking myself this question lately. And the only reason I can think of going 64bit, is to have more memory in your server. But since myth isn't memory intensive, I cant see a  reason to go 64bit , myself. Unless someone, knows of a reason, I dont see any reason that its better.

---

### Post by tgm4883 on 2008-12-05
> **4dognight said:**
> I don't think the question was, can mythtv run in 64 bit, but rather , why would you want to run it on 64 bit. I have asking myself this question lately. And the only reason I can think of going 64bit, is to have more memory in your server. But since myth isn't memory intensive, I cant see a  reason to go 64bit , myself. Unless someone, knows of a reason, I dont see any reason that its better.

Some people have seen a 30% faster transcoding time.

---

### Post by 4dognight on 2008-12-05
> **tgm4883 said:**
> Some people have seen a 30% faster transcoding time.

Is that because they throw more memory at it? I'm curious cause it would still be the same code wouldn't it? I wasn't aware that 64 bit means something runs faster just because its 64 bit. Especially since most apps are still 32 bit. Its the kernel that would be 64 bit in this case, not mythtranscode.

---

### Post by meho_r on 2008-12-05
The real question is: If you have 64bit processor why would you go 32bit at all? It's completely natural that you choose 64bit Ubuntu, so, again, why would you go 32? I don't know of myth, but every app I ever needed has 64bit version.

---

### Post by Therion on 2008-12-05
> **meho_r said:**
> The real question is: If you have 64bit processor why would you go 32bit at all? 
Indeed.  Once you've gone 64-bit you'll never want to go back to 32.

---

### Post by tgm4883 on 2008-12-05
> **4dognight said:**
> Is that because they throw more memory at it? I'm curious cause it would still be the same code wouldn't it? I wasn't aware that 64 bit means something runs faster just because its 64 bit. Especially since most apps are still 32 bit. Its the kernel that would be 64 bit in this case, not mythtranscode.

No.  I'll refer you to wikipedia for a more in depth answer.  [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

But to sum it up.  ""64-bit" computer architecture generally has integer registers that are 64 bits wide, which allows it to support (both internally and externally) 64-bit "chunks" of integer data."

So basically, it can process more data than a 32-bit processor can in a set amount of time.  IE, you should see an increase on any number crunching app.

---

### Post by 4dognight on 2008-12-05
> **tgm4883 said:**
> No.  I'll refer you to wikipedia for a more in depth answer.  [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

But to sum it up.  ""64-bit" computer architecture generally has integer registers that are 64 bits wide, which allows it to support (both internally and externally) 64-bit "chunks" of integer data."

So basically, it can process more data than a 32-bit processor can in a set amount of time.  IE, you should see an increase on any number crunching app.

But mythtv and or mythtranscode is not written in 64 bit. They are both 32 bit applications, are they not? A 32bit application will still only use 32 bit registers. To get any performance improvement, I would expect the app to be compiled for 64 bit. And even then, depending on the app, it still may not benefit from the 64 bit archecture. This is even stated in that artical.

"Not all such applications require a large address space nor manipulate 64-bit data items, so they wouldn't benefit from the larger address space or wider registers and data paths. The main advantage to 64-bit versions of such applications is the ability to access more registers in the x86-64 architecture."

My 2cents on this topic, would be that there is no compelling reason to go to 64bit. I doubt it would be a night and day difference between 32bit and 64 bit.

I'm not saying don't go 64bit, but rather dont get your hopes up on a huge benefit from it.

---

### Post by meho_r on 2008-12-06
Even if myth* is 32bit, it won't work faster on 32bit. In fact, it'll work same or better (not worse) on 64bit. And you'll still have "64bit" for any other app. But, at the end, it's your call, if you for some reason like more 32bit, then go 32 ;)

EDIT: BTW, you sure myth* is 32bit only?

---

### Post by Perfect Storm on 2008-12-06
The source are there to compile it for 64-bit.

---

### Post by meho_r on 2008-12-06
I guess OP meant compiled package. But still, I noticed myth* in repos (and I use 64bit system, so I assume those are 64bit packages too).

---

### Post by majoridiot on 2008-12-07
without getting into a never-ending debate over "is mythtv 64 bit or not?"...

i will say that the 64 bit distros have matured greatly and are terrific packages.  i have been installing
and using mythbuntu 64 bit for the past few releases and find it very stable and considerably
faster in many applications- including transcoding and muiltitasking while playing back and 
streaming h.264 encoded HD movies.

i would not consider installing the 32 bit distro on any new dual or quadcore builds, unless requested.

my only caveat is to stick with 8.04.1 for now.  8.10 64 bit has been less than stable on 2 different
boxes and i have had to downgrade until things are sussed.

---

