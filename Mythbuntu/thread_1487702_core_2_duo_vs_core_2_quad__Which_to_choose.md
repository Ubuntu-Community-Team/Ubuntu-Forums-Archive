---
title: "core 2 duo vs core 2 quad?  Which to choose?"
date: 2010-05-19
forum: Mythbuntu
---

### Post by Sternfan on 2010-05-19
Hi all,

I am planning on building a Mythbuntu box.  Looking at motherboards in my price range, for roughly the same cost - which is better?  A core 2 duo at 3+ ghz?  Or a core 2 quad at a slower speed (2.5ghz)? 

I am planning on putting this together within the month, any info greatly appreciated. 

Thanks,
Rob

---

### Post by cascade9 on 2010-05-19
Core 2 Duo would be more than enough. If your looking to save a bit of money, or get a more powerfully system than you need (for desktop/mythbuntu use) then maybe AMD is worth looking at. 4 core CPUs for very good prices.

---

### Post by Grenage on 2010-05-19
It's not going to make a lot of difference, but considering the application, I would recommend the higher-clocked duo.  If the machine was being used for anything else, I'd go quad.

---

### Post by LowSky on 2010-05-19
> **Grenage said:**
> It's not going to make a lot of difference, but considering the application, I would recommend the higher-clocked duo.  If the machine was being used for anything else, I'd go quad.

If you need to transcode. then go quad, as you can multithread and save time. If you are just using it for basic recording and watching and not worrying about transcoding, then you really don't need much power.

Realistically you can get a $60 dual-core processor that will be more than enough for MythTV. Spend your money on a better TV tuner card and storage space. I'm amazed that an hour show is about 6GB in 1080i. If you think about it that way, 1TB of space wont last very long.

---

### Post by williammanda on 2010-05-19
> **Sternfan said:**
> Hi all,

I am planning on building a Mythbuntu box.  Looking at motherboards in my price range, for roughly the same cost - which is better?  A core 2 duo at 3+ ghz?  Or a core 2 quad at a slower speed (2.5ghz)? 

I am planning on putting this together within the month, any info greatly appreciated. 

Thanks,
Rob

Based on my setup I use a core 2 quad 9300. I have my masterbackend / frontend with 3 tunner cards. I also have four other frontends that could be playing at any given moment. The unit is also used as a desktop computer for ripping dvd's, spreadsheets, browser, etc... So it just depends on what your use will be.

---

### Post by ian dobson on 2010-05-19
Hi,

If your not transcoding videos, cpu performance doesn't make any difference, a dual core is more than enough.

It's better to invest the money in more harddisk space and please,please buy a NVidia graphic card. MythTV supports hardware acceleration (VDPAU) on NVidia cards so you don't need much CPU for playback. 

My frontend is an underclocked C2D e5200 running at 800MHz and it's enough to playback 1080p with VDPAU. My graphic card is a passive cooled 9600GT (also underclocked).

In my backend I currently have 6Tb recording space (RAID5) and another 4Tb for backups. Since starting with MythTV 2 years ago my disk requirements have grown about by almost 300%

Regards
Ian Dobson

---

