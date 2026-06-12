---
title: "Full Screen OpenOffice Presentation"
date: 2010-05-16
forum: Multimedia Software
---

### Post by whalogreg on 2010-05-16
After upgrading to Lucid, I've found that when using the OpenOffice Presentation in a full screen slide show, that the presentation itself does not maximize over the gnome panel anymore (I have a slideshow with my panel showing on top). Quite annoying. I am able to work around this by auto-hiding the panel, but would rather be able to simply run the presentation without having to do so. I can't find anything in OO's settings to resolve this. Any help?

---

### Post by NTHQ on 2010-05-16
I am having the same issue and would like some assistance as well.

---

### Post by whalogreg on 2010-05-17
> **NTHQ said:**
> I am having the same issue and would like some assistance as well.

Have you had any other problems with OpenOffice products since upgrading to Lucid? I'm wondering if this problem has anything to do with Oracle's purchase of Sun....

---

### Post by optimusmedia on 2010-05-17
I also can repeat the problem.

---

### Post by michaelhoward78 on 2010-05-17
same issue. but there dont be anything else wrong with it.

---

### Post by NTHQ on 2010-05-17
> **whalogreg said:**
> Have you had any other problems with OpenOffice products since upgrading to Lucid? I'm wondering if this problem has anything to do with Oracle's purchase of Sun....
Everything else seems fine.

---

### Post by whalogreg on 2010-05-20
bump

---

### Post by Hagar Delest on 2010-05-21
Can you try with the Sun version? See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

No problem for me but using xubuntu (with Sun version). Not sure if the problem is in the OOo main code or in the Novell build (used by Ubuntu by default).

---

### Post by oyvinst on 2010-05-26
Has a bug been filed ? I'm seeing this as well. Quite stupid.

[I]Edit: Yes, several bugs have been filed of course. Looks like it was just fixed upstream.
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807)[/I]

---

### Post by whalogreg on 2010-05-28
I found turning off compiz cured my problem. This kind of makes me sad. I tried using the deb packages from openoffice's website and it took care of it. Thanks.

---

### Post by belfi117 on 2010-06-18
I have the same problem. Actually I don't know how you SOLVED it. Would you please let me know how to fix it?

---

### Post by Hagar Delest on 2010-06-18
Have you tried to turn Compiz effects off as stated in the last post?

---

### Post by soro2005 on 2010-06-19
> **Hagar de l'Est said:**
> Have you tried to turn Compiz effects off as stated in the last post?

Turning off Compiz is hardly a solution. It should work with compiz. I also have this problem.
In any case, the relevant bug report is [here](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807)

---

### Post by Hagar Delest on 2010-06-19
Try the Sun/Oracle version, it should fix it: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by cafonso on 2010-07-16
This is a serious bug for a long-term (LTS) release, being discussed in the OO, Compiz and Ubuntu developer communities. This thread should not have been marked as "solved" at this point. Disabling features is not a solution.

---

### Post by teuvotohvelo on 2010-11-25
Hi!

I found a nice little trick to get OpenOffice Impress (or virtually any Window) to get fullscreen with CompizFusion. I just activated module called "Additional window management functions" (or something like that, I use Finnish version of Ubuntu, so I'm not sure about the actual translation) and there is an option to configure keyboard shortcut for "toggle window fullscreen". Now I can switch any window I want to fullscreen!

I also found that there is an update for Open Office that fixes this bug: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807/comments/86](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807/comments/86)

And yes, I know there is other (and newer) topics about this problem, but I wanted to make the current situation clear also for anyone who reads this thread. And furthermore, now we can say this thread can be set to [SOLVED]: there is buxfix for 10.04 and also a workaround i descripted, that requires only one additional keystroke at the start of the presentation ;)

---

