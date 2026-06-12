---
title: "DVGrab file ending"
date: 2010-09-09
forum: Multimedia Software
---

### Post by serotta_rider on 2010-09-09
I am using a cannon HV20. No matter what format I pick in dvgrab the file ending is always m2t. 

I am trying to get a format that works on a mac and so I want a .dv or quicktime ending.

I am doing the following.


dvgrab -format raw -autosplit -showstatus laborday-
Found AV/C device with GUID 0x00008500014d3a5b
Waiting for HDV...
Capture Started
"laborday-008.m2t":    14.42 MiB 127 frames timecode 00:07:18.23 date 2010.07.04 19:19:3333^C

---

### Post by bodover on 2011-04-13
dvgrab has the smarts to recognise the format of the recording. In this case it is mpeg transport stream. You can then convert it to another codec / container with the appropriate tools.

---

