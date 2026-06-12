---
title: "streaming video sites don't work"
date: 2009-12-22
forum: Multimedia Software
---

### Post by LesFromWaldenVT on 2009-12-22
I have tried to stream video from NBC, Fox and NetFlix but none of these work with Linux. Any chance there is a fix coming soon?

---

### Post by lewisforlife on 2009-12-22
> **LesFromWaldenVT said:**
> I have tried to stream video from NBC, Fox and NetFlix but none of these work with Linux. Any chance there is a fix coming soon?

I am not sure about NBC and Fox, but Netflix uses a Microsoft Product, Silverlight Digital Rights Management which is only supported on Windows operating systems.  One of a couple of things will have to happen to get Netflix to work


[LIST]
[*]Netflix move to an open, standard, more cross-platform streaming format
[*]Microsoft make Silverlight cross platform (hopefully remove DRM stuff), I think there is something called Moonlight, but it doesn't work for Netflix.
[/LIST]

I don't see this happening anytime soon, but maybe if enough people complain to Netflix, and possibly cancel their account because of there lack of support for non Monopolistic operating systems, Netflix will move to an open standard.

---

### Post by SawyerLX on 2010-01-06
Yeah i have been using Amazon.com, Movies, and Video on demand.  I think Apple encompasses Netflix with Microsoft's liscence.

Chrome OS may bring about a new Movie service ,  toooo......:popcorn:

---

### Post by efflandt on 2010-01-07
I use a BluRay player for streaming Netflix, since I don't think you can get streaming HD Netflix on a PC anyway.

Fox video is flash, but some pages have too many flash ads.  If you are using 64-bit ubuntu, the flash-plugin-installer in Synaptic is actually 32-bit flash with a wrapper, but true 64-bit flash is available from Adobe [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

However, 64-bit flash relies on lahf_lm instruction that some older 64-bit cpus do not have.  So if your browser vaporizes on some flash, you may need the lahf-fix per [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)

The initial page at Hulu may bog down with previews scrolling across when you initially try to login, but it should work for actual videos once you get past that.

---

### Post by pyrofreak99 on 2010-01-07
[http://ubuntuforums.org/showthread.php?p=8623341#post8623341](http://ubuntuforums.org/showthread.php?p=8623341#post8623341)


ok maybe u could help me out with my question also its similar to this one but ya kno 


but i didnt think netflix even ran on linux  that it was only for like microsoft products and stuff like that

---

### Post by FalloutMan on 2010-01-07
> **lewisforlife said:**
> I am not sure about NBC and Fox, but Netflix uses a Microsoft Product, Silverlight Digital Rights Management which is only supported on Windows operating systems.  One of a couple of things will have to happen to get Netflix to work


[LIST]
[*]Netflix move to an open, standard, more cross-platform streaming format
[*]Microsoft make Silverlight cross platform (hopefully remove DRM stuff), I think there is something called Moonlight, but it doesn't work for Netflix.
[/LIST]

I don't see this happening anytime soon, but maybe if enough people complain to Netflix, and possibly cancel their account because of there lack of support for non Monopolistic operating systems, Netflix will move to an open standard.

I think that the only reason moonlight doesnt work with netflix is because the netflix server is checking the OS/browser info and not seeing microsoft or OSX in it and instantly denying it.  I wonder if you changed that data that Netflix might just work with linux.

---

