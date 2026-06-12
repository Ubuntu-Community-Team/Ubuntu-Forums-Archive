---
title: "Would Samba hinder gigabit speeds?"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-03-04
Just a question here... Using Samba on my network, it took me approximately 34 minutes to transfer 18 gigabytes of data from my desktop to my laptop. Both computers were wired to a 10/100 switch.

10/100 = 100Mbps / 8 = 12.5MB/second it's capable of transferring.

34 minutes @ 12.5MB/second = 8.8MB/second it's transferring at. I guess 12.5, along with some headroom, longer/low quality cable, etc brought it to 8.8MB/s, which I GUESS is average. Right?

If I were to get a gigabit switch, would Samba up the speeds too? I wasn't sure if Samba by design was limited to a certain transfer speed or if Samba was strickly network dependent.

---

### Post by Huufarted on 2009-03-04
I'm in a similar situation.  2 PCs, one is WinXp, other os Ubuntu.  Moving files over file and print sharing (Samba) on 100 mbit connection maxed out at about 10 MB/sec.  Moving the same files over gigabit maxed out at about 41 MB/sec.  The limiting factor wasn't the bandwidth, but instead the read/write of the hard drives.  Samba DOES add some overhead, but your performance increase compared to 100 mbit will still be fantastic.

To answer your question, Samba does not limit any kind of speeds with a cap or anything like that.  It will move as fast as the hardware will let it move.

---

### Post by Roasted on 2009-03-05
So what you're saying is basically this...

100Mbps = 12.5MB/second (highest in theory)
1000Mbps = 125MB/second (highest in theory)

On a 10/100 network transferring @ 8MB/second is a typical 100Mbps connection + overhead.

However, on a 10/100/1000 network transferring @ 41MB/second is a different story, because the 41MB/second isn't being restricted due to severe overhead from it's potential theoretical output, but the drives themselves are limiting the possible 125MB/second to 41MB/second... whereas the reason I'm slinging 8Mb/second instead of 10+MB/second on a 100Mbps network is due to the overhead, not necessarily hardware limitation.

Is my train of thought correct?

---

### Post by strife242 on 2009-03-05
You are on the right track.

But there is loads of things that one can count into the equation when it comes to measuring transmission speeds.

You have the data you want to transfer, on top of this is the network protocols, possible encryption and similar which you could say is overhead.

Then you have the hardware issues, like drive speed, bus speed, cpu load and all that crap. 

Then the type of networking equipment, obviously a $10 consumer switch / router won't perform as good as a $1000 industry equivalent.

All in all, transfering files at 10MB/s on a 100Mb/s network is perfectly fine performancewise.

---

### Post by Yashiro on 2009-03-05
Samba is slower than NFS and FTP but it's not limited by design or anything like that.

---

### Post by Roasted on 2009-03-05
> **Yashiro said:**
> Samba is slower than NFS and FTP but it's not limited by design or anything like that.

I always heard some people say Samba is slower, but I've never seen a speed difference in my case. And when I have talked to people who have slow Samba speeds, they're saying they're running like 2MB/second, much lower than what I transfer at.

I mean, if Samba is "slower" it can't be hindering connections overall too much! I don't think 10 (or in my case, even 8.5-9.8 that I fluxuate between) is all that far off from 12.5 potential in theory.

---

### Post by Yashiro on 2009-03-05
Give NFS a test on your network if you can. If it's about the same as Samba then you have confirmation that's it's not some goofy setup issue.

Not that I am saying it is! :) but it doesn't hurt to test stuff out.

---

### Post by Roasted on 2009-03-06
True, but I need to stick with Samba regardless due to the fact I'm a Linux user living in a Windows family. :P My brothers are bigtime gamers and my mom needs certain MS applications for work, so those 3 have stayed with Windows while I migrated. So regardless, Samba is here to stay, I'm just trying to obtain more info about it, cause, well... I'm curious. :D

---

### Post by Huufarted on 2009-04-02
Better late than never, right?

Did you upgrade to gigabit?  If so, what kind of performance did you see?

---

### Post by Roasted on 2009-04-02
I never did upgrade to a gig switch. I went broke buying tires and fixing my gargantuan sized hole in my exhaust that I haven't had the opportunity to upgrade to anything else.

---

