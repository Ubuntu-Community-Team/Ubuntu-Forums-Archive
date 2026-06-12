---
title: "Very laggy flash games"
date: 2010-08-14
forum: Multimedia Software
---

### Post by TrieBr on 2010-08-14
I'm trying to play a flash game that runs perfectly smooth on Windows 7, but it seems to be getting huge lag spikes here on Ubuntu. I've installed the latest Nvidia drivers and I used the Flash Aid Firefox plugin to make sure I had the right version and flash compatibility.

If anyone has any suggestions on why it would lag so bad, or if you need any more information from me please let me know!:)

---

### Post by slooksterpsv on 2010-08-14
> **TrieBr said:**
> I'm trying to play a flash game that runs perfectly smooth on Windows 7, but it seems to be getting huge lag spikes here on Ubuntu. I've installed the latest Nvidia drivers and I used the Flash Aid Firefox plugin to make sure I had the right version and flash compatibility.

If anyone has any suggestions on why it would lag so bad, or if you need any more information from me please let me know!:)

There isn't any hardware acceleration for flash in Ubuntu (or any variant of Linux that I know for that matter) so the only way you really could speed it up or see if helps is disable composition. Go to System -> preferences -> appearance -> effects -> change it to None. Now if you use any programs that use transparency (such as Docky) you'll see black lines where it should be transparent.

I've been able to watch full-screen movies on hulu with little stuttering doing that, but then again its different for each person.

Other than that I'd try installing AdBlock (removing ads can speed up sites/flash); trying a different browser (Chrome is the only one that flash videos work in to where I can click the buttons).

That's all the suggestions I have.

---

### Post by lovinglinux on 2010-08-14
> **TrieBr said:**
> If anyone has any suggestions on why it would lag so bad, or if you need any more information from me please let me know!:)

See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

> **slooksterpsv said:**
> (Chrome is the only one that flash videos work in to where I can click the buttons).

The clicking issue usually happens when you are running a 32bit plugin on a 64bit system and can be easily fixed. See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

