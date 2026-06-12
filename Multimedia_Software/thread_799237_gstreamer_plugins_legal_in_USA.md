---
title: "gstreamer plugins legal in USA?"
date: 2008-05-18
forum: Multimedia Software
---

### Post by Jackelope on 2008-05-18
Are the "gstreamer extra plugins" and "ffmpeg video plugins" legal to use for U.S. residents? I realize no one cares that much, but after a bit of reading I'm still unclear on the subject and it'd be nice to know one way or the other. Thanks ahead of time.

---

### Post by cor2y on 2008-05-18
Like i said in a previous thread as far as i know they are legal they are decoders and not encoders plus reversed engineered i believed which is why sometimes there are pixels/video artifacts when you attempt to playback propriatary codecs in some gstreamer players.

---

### Post by wdaniels on 2008-05-18
The US patent system is such that it is impossible to say. Basically, the whole system makes no sense when applied to software and it would take a legal challenge to determine one way or another on any particular issue. If you were to assume that all granted patents are valid, probably most software is in violation of some patent or another (unbeknown to the authors or anybody else) because there are some absurdly broad-ranging patents out there, and far too many for anybody to read them all.

The attitude that seems to be taken by the [ffmpeg project]("http://ffmpeg.mplayerhq.hu/legal.html") is that they don't know and don't really care, they just say that if they violated some patent it is accidental since they never read any. This, in my opinion, is the only sensible approach to take in the matter.

---

### Post by Roasted on 2008-08-09
Are there seriously no right or wrong answers? I know the US copyright system is laughable at best, and unusually difficult to understand, but I would think there'd be some sort of yes/no answers that can apply to these questions.

Ex -

Ubuntu Restricted Extras. Legal?
GStreamer Plugins. Legal?
w32codecs. Legal?
libdvdcss. Legal?
Medibuntu Repostiory. Legal?

If I said, yes, I live in the United States of America, you're telling me that the legality issue is just a blur and it would take going to court and finding out what happens to place an actual y/n answer on this circumstance?

---

### Post by Melcar on 2008-08-09
Well, as they say back home: "golpe avisa" (hit lets you know)

---

### Post by wdaniels on 2008-08-09
> **Roasted said:**
> If I said, yes, I live in the United States of America, you're telling me that the legality issue is just a blur and it would take going to court and finding out what happens to place an actual y/n answer on this circumstance?

Yes, that is the situation. One of the main reasons is that it is beyond the responsibility (and ability) of the US Patent Office (or any other organisation) to determine whether a patent is actually valid, they only assess the application for sanity in accordance with the various criteria (e.g. non-obvious, inventive step and so on). For example, it is often possible to turn up examples of "prior art" that would invalidate a patent, but the USPTO does not actively look for such examples before granting a patent (since such a process could not possibly be exhaustive). Also, the USPTO does not have an army of programmers to debate whether the patent is non-obvious. These things are left to a court of law to decide, and a great many patents are declared invalid when that happens.

The problem of course is that you typically need a few million dollars to fight such a case, so it is far too easy for large software companies to go around patenting all and sundry so that they can use the threat of such litigation to damage smaller competitors. For example, a new start-up would find it next to impossible to secure new investment with the threat of an IP lawsuit hanging over them.

The reverse often happens too - large software companies invariably manage to accidentally violate numerous patents (as we all do) naturally through the act of writing software, and these companies are rich pickings for a much smaller company with a patent grant.

Beyond the basic issues of validity it gets even more complicated, and above that there are higher-level questions about the legality of software patents at all.

The biggest problem with the system overall is that it is simply impossible for any person to read all the granted and applied for software patents and fathom out exactly what code we are actually allowed to write. As a quick example, there may or may not be a patent for the visual aid of using "tabs" in dialogs. Who would know? Such a patent could be phrased in all manner of different ways so searching the patent database for keywords will not yield even a convincing, let alone definitive, answer. I pick this example because I heard mention once that there is actually such a patent on tabbed dialogs.

However, it is often possible to make fair probabilistic judgements in many cases. For example, in the case of compression algorithms, it is clear enough that there are indeed granted patents covering the use of certain algorithms, and perhaps more importantly there are organisations that might pursue those questions against offending software, so that software is considered "tainted" and sidelined in favour of free alternatives for which fewer IP questions exist (e.g. MP3 vs OGG). This is not intended to imply that the relevant patents are valid (i.e. that it definitely is or is not legal to use the others), only to remove open source organisations and projects from the firing line in such matters. As such, we cannot say that project X is "legal" or "illegal" for use in country Y, we can only characterise project X as being tainted or not.

---

### Post by wdaniels on 2008-08-09
It's worth pointing out that as an end user you are not necessarily required to determine whether the programs you use violate any patents, it is primarily the authors/distributors of the software who can be held to account, especially if they claim otherwise.

The targets in any litigation will naturally be those who can be shown to have profited in some direct monetary form from writing/distributing the offending material, which may potentially also include an organisation that deploys such software and relies upon that functionality for operational purposes. This is why it is very important for Linux distributions to identify and properly segregate such potentially damaging software so that companies can use it confidently, regardless of any amount of inconvenience this might cause to users by having to install restricted components manually.

---

### Post by wdaniels on 2008-08-09
> **Roasted said:**
> I know the US copyright system is laughable at best, and unusually difficult to understand

I think I see your confusion now, I missed that you used the term "copyright" specifically before.

It's not (usually) an issue of copyright - that is relatively sane and reasonable and can be decided easily enough. No self-respecting Linux distribution would include any code that the copyright holder has not explicitly released under a suitable license. Stealing other people's work is just wrong in any country.

Also, copyright is mostly consistent between countries and covered by international laws and trade agreements.

The problem lies with (the absurdity of) patents as applied to software. Unlike copyright, the patent systems of each region differ greatly and there is mostly no jurisdiction of one in another (a US patent cannot be enforced in the UK for example, which is not true for copyright). These issues with software patents apply mostly to the US and Japan as far as I know.

---

### Post by Roasted on 2008-08-10
Thanks for all of your information. And yeah, that is a good point about authors and writers being the primary ones who have to watch that.

But, at the same time, why wouldn't that apply to us?

Say w32codecs are illegal in the US, yet not in Africa. Some writer in Africa comes up with w32codecs. Africa is happy. US gets a hold of w32codecs from Africa. Suddenly the US is using them.

Although we (you, myself, the end user) didn't write them, aren't we still violating the law by specifically using a piece of particular software that is... in essence... illegal?

---

### Post by wdaniels on 2008-08-10
> **Roasted said:**
> Although we (you, myself, the end user) didn't write them, aren't we still violating the law by specifically using a piece of particular software that is... in essence... illegal?

Technically, I *believe* the answer is yes. But in all practicality, no. That's not to say nobody would ever try, but it is almost unthinkable that a court would hold a person individually liable for patent violation by using a patented process (by means of a computer program) they didn't write and without knowing that they were doing so. It might be legally possible (I don't know, I'm not a lawyer) but it's unreasonable and impractical in any normal circumstances.

I say I'm not a lawyer, but to be honest I don't think it would help much if I were, since it's a very complicated and broken system.

---

### Post by Roasted on 2008-08-10
Yeah, but it's just humorous. Think about it... This system was created to punish those who violate the law. Yet, it's at the point where it's just a big conglomeration of ******** that it's like, meh, who cares... (to a degree).

It's as if law makers created so much work for themselves that at the end of the day, nobody wants to sift through the garbage in order to figure out what's right and wrong.

But, hey, at the end of the day I'm doing whatever is necessary (within reason) to get my Ubuntu system running. 

:guitar:

---

### Post by wdaniels on 2008-08-10
I think the fundamental problem with it is that the development of software is generally treated as an advanced engineering discipline, whereas it is more akin to writing (think "program writing" as opposed to "software engineering"). And as with writing, copyright is sufficient to protect software assets. When you apply the idea of patents to it, things start to break down fast. To continue the analogy, imagine if Shakespeare had been able to patent the general themes and outline of Romeo & Juliet...would that be reasonable? Or if some poet managed to get a patent on the haiku? Would the literary world be better off if such things had been possible (or if they were today)?

And how would we stand if the general method and apparatus for attaching two pieces of wood together using a nail had been patented? We would keep on inventing new metal devices for joining planks of wood until somebody came up with a decent one that they patented and offered royalty-free. This is not a good situation for an industry that is still trying to overcome the general problem of reuse in software, which has been at root the main driver for practically every new software "technology" and standardisation effort in the last 10 or more years. The actual solution to that problem, as with the wood, is open source, which has been proved extremely workable and effective, yet the patent system acts directly against such efforts.

It is not a good idea to strangle a young industry with patent systems at a point whereby the vast majority of code that is written (which the sponsors obviously regard as an investment in software technology), is done so purely for some specific purpose, to meet some particular set of requirements, and does not represent some new or advanced way of doing something as the product of investment in research. However, what happens is that each time some obvious, natural application of existing ideas gets implemented in a new area, that just happens to fulfil one of the criteria for patent grants (which do not require that no prior art exists, only that it does not exist as applied to the same problem) and affords the first one to do something a particular way the chance to patent it, even if the only reason nobody else had done the same thing before is simply that nobody else had so far had a need, opportunity or other reason to do so.

Sorry for the rant (I'll stop now) only this whole patent nonsense gets me mad like nothing else :D

---

