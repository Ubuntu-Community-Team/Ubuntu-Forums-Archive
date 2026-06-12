---
title: "discontinuous motion in video"
date: 2013-02-23
forum: Multimedia Software
---

### Post by zhanfei on 2013-02-23
I had this problem when I was watching youtube videos. The video stream became discontinuous even it's playing video which has been loaded.  Meanwhile both of the cpu cores usages were up to 90%. I can hardly believe a web video can make cpus so exhausted. Can you guys give me some generic testing steps, which I can do and find the possible reason for the high cpu usage problem?

---

### Post by AngJinhang on 2013-02-24
Flash players do really put up a lot of CPU and ram. And that's why I hate flash videos. Your problem about CPU high usages is maybe caused by the high swappiness. When your ubuntu run out of ram, and also swap, you are doomed. The pc starts to clean up the ram and also swap. And the CPU, disk usages, ram go crazy. But if compared to windows, this situation is better. Windows uses page file more than ram, and your hard disk is hot...
Try to disable flash. You should know that YouTube works without flash in Firefox.

---

### Post by zhanfei on 2013-03-25
Now I find not only for online videos but also for playing videos files, the performance is really bad. My ubuntu is 12. 04 LTS, freshed installed. I have ATI radeon graphic card on my laptop. I have had ATI/AMD proprietary graphic driver installed. So why I still suffer these problems? How to fix these problems? Is this related to the new version of ubuntu? I don't think I had these problem before with 10. 04 LTS. How about I switch back to 10. 04?

---

### Post by bipinvish on 2013-03-25
Hey buddies,
I too faced same problem but with high res videos like 1080.
can any one suggest me any player that plays videos smoothly.

thanx
Bipin Vishwakarma
[EMAIL="b.vish@live.com"]b.vish@live.com[/EMAIL]

---

