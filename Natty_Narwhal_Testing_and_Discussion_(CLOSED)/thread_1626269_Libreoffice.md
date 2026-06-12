---
title: "Libreoffice"
date: 2010-11-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nperry on 2010-11-20
Since Libreoffice is now in debian repos, reckon we can get a merge? 

Whats the best way to do it? Open a bug report?

---

### Post by tghe-retford on 2010-11-20
Looks as if someone has already requested Libreoffice be packaged in Ubuntu since September:

[https://bugs.launchpad.net/df-libreoffice/+bug/651124](https://bugs.launchpad.net/df-libreoffice/+bug/651124)

---

### Post by dext on 2010-11-20
its already packaged in Fedora for F15

---

### Post by coffeecat on 2010-11-20
> **dext said:**
> its already packaged in Fedora for F15

Interesting. Here's a multiple-choice question. Will the Fedora devs ruin the autocorrect utility by removing the Replace tab just as they have done in Open Office since the year dot?

1 - Yes

2 - Almost certainly

3 - Of course

---

### Post by kaldor on 2010-11-20
LibreOffice will have a stable release soon. I see no reason to include OpenOffice.org in Ubuntu 11.04 anymore.

---

### Post by dext on 2010-11-20
> **coffeecat said:**
> Interesting. Here's a multiple-choice question. Will the Fedora devs ruin the autocorrect utility by removing the Replace tab just as they have done in Open Office since the year dot?

1 - Yes

2 - Almost certainly

3 - Of course

IMO there are far better office suites out there than just Openoffice which was a resource hog anyway. like OxygenOffice there's one. if you dont like hat Redhat/Fedora Devs do to a office app your not forced to use it. but will they do that to LibreOffice? who knows time will tell i guess, but if you dont like it, download the tarball an extract it

---

### Post by cariboo on 2010-11-20
> **kaldor said:**
> LibreOffice will have a stable release soon. I see no reason to include OpenOffice.org in Ubuntu 10.10 anymore.

You won't see Libreoffice packages for Maverick, development is over and done with. We should see it in Natty though.

---

### Post by dext on 2010-11-20
> **kaldor said:**
> LibreOffice will have a stable release soon. I see no reason to include OpenOffice.org in Ubuntu 10.10 anymore.

no one is stopping you from downloading an compiling it yourself in Mav. or you could enable the Natty repo Temporarily and install it there ( thats assuming its in natty repo ) or just get it from the ppa repo

---

### Post by kaldor on 2010-11-20
Whoops, I meant 11.04 :)

---

### Post by dext on 2010-11-22
> **coffeecat said:**
> Interesting. Here's a multiple-choice question. Will the Fedora devs ruin the autocorrect utility by removing the Replace tab just as they have done in Open Office since the year dot?

1 - Yes

2 - Almost certainly

3 - Of course

here is an answer to your question. [http://forums.fedoraforum.org/showthread.php?p=1419237&posted=1#post1419237](http://forums.fedoraforum.org/showthread.php?p=1419237&posted=1#post1419237)  Ubuntu is a Debain based Distro which has different and or allows patented stuff in its distro. Fedora is a USA based Distro again different Laws. maybe you should and others here should brush up on those laws. look at Mono for starters, Ubuntu is Ridden with Momo. Fedora doesnt install Mono by default and hasnt since fedora10 and or 9.

---

### Post by coffeecat on 2010-11-22
> **dext said:**
> IMO there are far better office suites out there than just Openoffice which was a resource hog anyway. like OxygenOffice there's one. if you dont like hat Redhat/Fedora Devs do to a office app your not forced to use it. but will they do that to LibreOffice? who knows time will tell i guess, but if you dont like it, download the tarball an extract it

> **dext said:**
> here is an answer to your question. [http://forums.fedoraforum.org/showthread.php?p=1419237&posted=1#post1419237](http://forums.fedoraforum.org/showthread.php?p=1419237&posted=1#post1419237)  Ubuntu is a Debain based Distro which has different and or allows patented stuff in its distro. Fedora is a USA based Distro again different Laws. maybe you should and others here should brush up on those laws. look at Mono for starters, Ubuntu is Ridden with Momo. Fedora doesnt install Mono by default and hasnt since fedora10 and or 9.

@dext, I'm sorry that I seem to have inadvertently touched a raw nerve. I was being only half-serious and forgot to add a winking smiley to my post to make my intent clear. Apologies. My question was, in fact, rhetorical but thanks for the link. So the crippling of the autocorrect utility is down to mono is it? Are you sure? This lack of the replace tab goes way back in Fedora, as long as I remember, way before 9. Whatever, my own solution to this was to download and install the RPMs for Go-OO in Fedora.

However, I think we're OT, so I'll keep my peace for now. I wish LibreOffice well.

---

### Post by Slug71 on 2010-11-22
I would imagine that until LibreOffice becomes the official name, it wont be packaged by default.

---

### Post by seeker5528 on 2010-11-22
> **dext said:**
> here is an answer to your question. [http://forums.fedoraforum.org/showthread.php?p=1419237&posted=1#post1419237](http://forums.fedoraforum.org/showthread.php?p=1419237&posted=1#post1419237)  Ubuntu is a Debain based Distro which has different and or allows patented stuff in its distro. Fedora is a USA based Distro again different Laws. maybe you should and others here should brush up on those laws. look at Mono for starters, Ubuntu is Ridden with Momo. Fedora doesnt install Mono by default and hasnt since fedora10 and or 9.

Following that link I can't see anything indicating the replace tab was removed in the Fedora builds of OOo because of patent/legal issues.

And what does Mono have to do with anything?

Later, Seeker

---

### Post by cariboo on 2010-11-22
> And what does Mono have to do with anything?

I'm not sure why mono was brought up either, OOorg relies on java to get things done. Although it is my understanding that future versions will have less reliance on java.

---

### Post by dext on 2010-11-22
> **seeker5528 said:**
> Following that link I can't see anything indicating the replace tab was removed in the Fedora builds of OOo because of patent/legal issues.

And what does Mono have to do with anything?

Later, Seeker

well why dont you email Oracle and ask them yourself why it may have been removed in Fedora's OpenOffice. im not gonna do your homework for you 

what does Mono have to do with anything? 

1) Novel Owned 
2) Novel shook hands with the Devil if im right.
3) Mono has Microsoft Code in it am i right? which would make it patented.

---

### Post by sanderd17 on 2010-11-22
mono doesn't have ms code in it, but mono implements the same features as some ms progs do. Those features are patented. I'm happy we don't have software patents in Belgium (I believe in entire Europe) so I could always use mono.

btw, Novell is not bought by ms, novell is bought by an other firm and because novell was too expensive, they sold a lot of patents to ms (or ms daughter firms)

---

### Post by Merk42 on 2010-11-22
> **dext said:**
> what does Mono have to do with anything? 

1) Novel Owned 
2) Novel shook hands with the Devil if im right.
3) Mono has Microsoft Code in it am i right? which would make it patented.
Well OpenOffice is **Oracle** not **Novell**, so really rather irrelevant to this particular thread.

---

### Post by cariboo on 2010-11-22
The mono question was cleared up here several releases ago. It has no place in this discussion about Libreoffice.

---

### Post by seeker5528 on 2010-11-24
> **dext said:**
> well why dont you email Oracle and ask them yourself why it may have been removed in Fedora's OpenOffice. im not gonna do your homework for you 

So should I take it that you included the link to the Fedora policy on patent/legal issues because you assume that is the reason the feature in question was "broken"/ommited in Fedora and you don't have pointers to anything that back that assumption so an irrelevant blurb about Mono was mentioned instead?

And why should I do the research? I'm not the one that linked to the Fedora policy as if it was an explanation to the why of the earlier question.

> well why dont you email Oracle and ask them yourself why it may have been removed in Fedora's OpenOffice.

Why would I ask Oracle about something that was done in Fedora?

Later, Seeker

---

### Post by cariboo on 2010-11-24
Again, what does mono have to do with OpenOffice.org?

---

### Post by seeker5528 on 2010-11-24
> **cariboo907 said:**
> Again, what does mono have to do with OpenOffice.org?

Exactly. ;)

Later, Seeker

---

### Post by amano on 2010-11-26
> **dext said:**
> 
what does Mono have to do with anything? 

1) Novel Owned 
2) Novel shook hands with the Devil if im right.
3) Mono has Microsoft Code in it am i right? which would make it patented.

Crazed and confused?

1) OpenOffice was built by Sun which is now ORACLE. And LibreOffice is now driven by the independent Document Foundation. 

2) There is no Microsoft code in Mono except for some pieces of code open sourced by Microsoft themselves.

3) Mono isn't known to violate any Microsoft patents. There are just suspections. Most of the C# spec is covered by Microsoft's community promise anyway. Thus they cannot sue even if you infringed on a Microsoft patent related to the spec. And remember: Any code in existence might infringe on a Microsoft patent currently unknown to the world.

4) There is no single piece of Mono code in OpenOffice. Just educate yourself before starting a flamefest.

---

### Post by directhex on 2010-11-26
> **amano said:**
> 4) There is no single piece of Mono code in OpenOffice. Just educate yourself before starting a flamefest.

There are bindings, allowing you to write macros etc in C#, in Go-OO (the patchset applied to upstream OOo in pretty much every distro) and LibreOffice.

---

### Post by MacUntu on 2010-11-26
Don't want to be a party-pooper, but what has all of this to do with Ubuntu 11.04 and the inclusion of LibreOffice?

---

### Post by amano on 2010-11-26
That's what we are trying to say: NOTHING

(and NO, even if there are bindings FOR Mono in the code, there isn't any part OF Mono within it)

---

### Post by cariboo on 2010-11-26
This thread has fallen way off topic. I suggest someone start a new thread, as this one is closed.

---

