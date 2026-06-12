---
title: "Movie DVDs spin and then get ejected"
date: 2014-05-26
forum: Multimedia Software
---

### Post by PartisanEntity on 2014-05-26
Hi all,

I am not much of a DVD user, so not sure what the issue is here.

I am having a strange problem that affects movie DVDs only (some new type of DRM??).

I have a 2010 model iMac, and the only OS is Ubuntu 14.04 LTS.

When I pop in a movie DVD, it will spin up a couple times, then get ejected.

Data DVDs are beign read fine.

I tried various new and old movie DVDs with the same effect. The DVD discs themselves appear to be find as they are being played normally in our stand-alone DVD player.

They also worked fine on my ancient Macbook from 2008 running OSX.

Here is the output of lshw:

```
cdrom
             description: DVD writer
             product: DVD RW AD-5680H
             vendor: OPTIARC
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 3AHB
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=open
```

I have Ubuntu restricted extras installed as well as libdvdcss.

Anyone familiar with this type of behavior?

---

