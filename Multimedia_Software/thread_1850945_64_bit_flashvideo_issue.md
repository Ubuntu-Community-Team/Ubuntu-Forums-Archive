---
title: "64 bit flash/video issue"
date: 2011-09-27
forum: Multimedia Software
---

### Post by sks24 on 2011-09-27
I'm getting ready to go to a friend's house and help him with his "my youtube says I need flash" issue.  I installed his 10.04 LTS, and I could have sworn I found a plug-in which got his flash going.

His computer is a fairly high-end quad core AMD Gateway tower.

I think it was called "easy flash" or something like that.  I also think it may have been a browser extension.

In any case, the purpose of this post is to ask after whether there's a single best solution to the Ubuntu 64 bit flash issue, and, if so, whether I might get a link to a page which would get me going once I sit down in front of his computer.

I did find [this]("http://www.ubuntugeek.com/flash-doctor-%E2%80%93-an-easy-way-of-fixing-flash-problems.html") this morning.  I'll try it, of course.  Perhaps one of you knows of something better, though.

In any event, thanks in advance,
Scott

---

### Post by wolfen69 on 2011-09-27
Try the flash-aid extension for firefox. It will remove the flash you have, and install the proper one.

---

### Post by sks24 on 2011-09-27
Oh, my, but did that ever work well.  Thank you Mister Wolfen!

---

### Post by SpindizZzy on 2011-10-08
Well, I've been pulling out my hair ever since I installed Backtrack 5 release 1... Flash-Plugin just won't work.  I was kinda happy when i found this thread and installed the 'Flashaid'-app, but none of the both options (install Adobe Beta or flash from repositories) works ... :-(  I'm on a 64-bit system with Firefox 7.0.1. Backtrack 5 R1 uses Ubuntu Lucid

---

### Post by lovinglinux on 2011-10-10
> **SpindizZzy said:**
> Well, I've been pulling out my hair ever since I installed Backtrack 5 release 1... Flash-Plugin just won't work.  I was kinda happy when i found this thread and installed the 'Flashaid'-app, but none of the both options (install Adobe Beta or flash from repositories) works ... :-(  I'm on a 64-bit system with Firefox 7.0.1. Backtrack 5 R1 uses Ubuntu Lucid

Please click Flash-Aid menu, select "Help >> Generate Report" and post the report here.

---

### Post by SpindizZzy on 2011-10-10
Well, here's the report:

---

### Post by jocko on 2011-10-10
Adobe Flash 11 (both 64 and 32 bit) is available in the Canonical-partners repo, so there is no big point in using flash-aid any more. Last I checked (a couple of days ago) flash-aid installed the flash 11 release candidate, while the final version 11 was in the partners repo...

---

### Post by lovinglinux on 2011-10-10
> **jocko said:**
> Adobe Flash 11 (both 64 and 32 bit) is available in the Canonical-partners repo, so there is no big point in using flash-aid any more. Last I checked (a couple of days ago) flash-aid installed the flash 11 release candidate, while the final version 11 was in the partners repo...

Flash-Aid is more than an installer. It removes conflicting plugins from various sources and also apply performance tweaks. It is currently installing the final flash version. 

About the repos, is the 64bit really 64bit? Last time I checked it was the 32bit with the 64bit wrapper. It would be great if they start providing the real 64bit in the repos.

---

### Post by lovinglinux on 2011-10-10
> **SpindizZzy said:**
> Well, here's the report:

The main problem is that you are using a 32bit version of Firefox on a 64bit system. 

Get Firefox 64bit from [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/7.0.1/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/7.0.1/linux-x86_64/)

---

### Post by jocko on 2011-10-11
> **lovinglinux said:**
> It would be great if they start providing the real 64bit in the repos.
Flash 11 final in the partners repo really is 64 bit. No ugly 32 bit wrapper anymore.

---

### Post by lovinglinux on 2011-10-11
> **jocko said:**
> Flash 11 final in the partners repo really is 64 bit. No ugly 32 bit wrapper anymore.

That's really nice.

---

