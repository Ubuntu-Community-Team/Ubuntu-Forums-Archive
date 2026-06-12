---
title: "Ceton InfiniTV 4 support status?"
date: 2012-01-28
forum: Mythbuntu
---

### Post by SPW06 on 2012-01-28
According to [http://www.mythtv.org/wiki/Talk:Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Talk:Ceton_InfiniTV_4), the Ceton InfiniTV 4 works well with Mythbuntu. Can anyone confirm this, and/or provide more details on how well it works? Should thr external USB version (which apparently does not get as hot as its internal card counterpart) also work? A quick Google search on CableCARD support only brings up that April Fool's joke.

I'm looking into switching cable cos from Insight to WOW! because I can get double the internet bandwidth and TV channels for about the same price a month if I use 1 M-Card rather than their terrible, clunky DVRs. I miss my old Myth setup, which I stopped using once everything started going digital/HD.

---

### Post by nickrout on 2012-01-28
> **SPW06 said:**
> According to [http://www.mythtv.org/wiki/Talk:Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Talk:Ceton_InfiniTV_4), the Ceton InfiniTV 4 works well with Mythbuntu. Can anyone confirm this, and/or provide more details on how well it works? Should thr external USB version (which apparently does not get as hot as its internal card counterpart) also work? A quick Google search on CableCARD support only brings up that April Fool's joke.

I'm looking into switching cable cos from Insight to WOW! because I can get double the internet bandwidth and TV channels for about the same price a month if I use 1 M-Card rather than their terrible, clunky DVRs. I miss my old Myth setup, which I stopped using once everything started going digital/HD.

[http://www.gossamer-threads.com/lists/mythtv/users/497094#497094](http://www.gossamer-threads.com/lists/mythtv/users/497094#497094)

---

### Post by uteck on 2012-01-28
It should work fine, a few people have posted on the forum at BraodbandReports, [http://www.dslreports.com/forum/wow](http://www.dslreports.com/forum/wow) that they were able to install it fine.  Alothough WOW does offer a self install option, it is recommended to have an installer do it since getting the cable card to get authorized to work can be problimatic

---

### Post by nickrout on 2012-01-28
> **uteck said:**
> It should work fine, a few people have posted on the forum at BraodbandReports, [http://www.dslreports.com/forum/wow](http://www.dslreports.com/forum/wow) that they were able to install it fine.  Alothough WOW does offer a self install option, it is recommended to have an installer do it since getting the cable card to get authorized to work can be problimatic

Yes but mythtv does not support this card unless you either patch your 0.24-fixes source code and compile it yourself, or run master, which code is experimantal and prone to breakages.

If you want to run master (called 0.25 in mythbuntu-repos) you MUST subscribe to the mythtv-dev and mythtv-commits mailing lists, and read them, and be prepared for breakages.

The developers DO need people to run master to test it out, but you HAVE to know what you are doing and be prepared for the fact that your system will not be as reliable as a release+fixes version

---

### Post by SPW06 on 2012-01-28
I may not be a mythtv developer, but I am a very experenced user. I remember having to compile the PVR 150 drivers each kernel release before they made it into the kernel :) That said, I think I'll stick with the PPA.I would be happy to provide feedback.

---

### Post by jaakan on 2012-10-18
Does anyone have it fully working on Mythbuntu 12.04 without recompiling any code?

---

### Post by nickrout on 2012-10-19
This thread is ancient, but I believe this card works fine with mythtv 0.25. ).25 is the release shipped with 12.04, so it should work fine.

Curious why you ask though, do you know something we (or the release notes) don't?

---

### Post by jaakan on 2012-10-19
My question is related to [FCC Allows Cablecos to Eliminate Clear QAM.......]("http://ubuntuforums.org/showthread.php?t=2071538")

I'm thinking about going Cablecard or just putting an antenna in my attic.

> **nickrout said:**
> This thread is ancient, but I believe this card works fine with mythtv 0.25. ).25 is the release shipped with 12.04, so it should work fine.

Curious why you ask though, do you know something we (or the release notes) don't?

---

### Post by nickrout on 2012-10-19
> **jaakan said:**
> My question is related to [FCC Allows Cablecos to Eliminate Clear QAM.......]("http://ubuntuforums.org/showthread.php?t=2071538")

I'm thinking about going Cablecard or just putting an antenna in my attic.

I was wondering what made you think it doesn't work with mtthtv 0.25 when the release notes are clear.

Cablecard will NOT automatically fix your problem. It depends how the broadcasts are flagged - copy freely, copy once etc. You need local input from others on your service. The best place to get that is mythtv-users mailing list.

---

