---
title: "epia openchrome xorg.conf"
date: 2009-10-27
forum: Mythbuntu
---

### Post by TomGar on 2009-10-27
Hi
I'm struggling with mythbuntu Jaunty running on an epia cn1000eg which allows hardware handling of mpg2 files. It used to be great under hardy but now jitters along at best.

I've tried mucking about with xorg.conf to little or no avail. Has anyone an xorg.conf that will get the most out of this board. I use it as a mythtv in the campervan and the kids are fed up!

It's running the openchrome driver,

---

### Post by TomGar on 2009-10-29
fixed it! Picked up the Via driver by sort of following 
[https://help.ubuntu.com/community/OpenChrome#VIA%20proprietary%20graphics%20driver](https://help.ubuntu.com/community/OpenChrome#VIA%20proprietary%20graphics%20driver)

cn1000eg needs a cn700 driver

 and eventually worked out to untar the right one after downloading it (bunzip2) as the tar command wouldn't work at first.

mythtv now runs ok. if anyone has an optimised xorg.conf for the via driver on an epia board I'd appreciate sharing it.

---

