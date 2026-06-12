---
title: "Any compelling reason to install the Mythbuntu 10.04 RC"
date: 2010-04-24
forum: Mythbuntu
---

### Post by GuiGuy on 2010-04-24
I've managed to install the MythTV 0.23 upgrade despite some of the objections it threw up (corrupted mythvideo data records). 

I'm running 9.10 at the moment so was wondering if there's a point to upgrading to Mythbuntu 10.04 RC?

Thanks

---

### Post by tgm4883 on 2010-04-24
No. Really the only reason you would upgrade distros would be for either A) newer version of MythTV, or B) Better hardware support.

As you are already on 0.23, if your hardware is working I would leave it. If it ain't broke, don't fix it.

---

### Post by GuiGuy on 2010-04-24
> **tgm4883 said:**
> 
As you are already on 0.23, if your hardware is working I would leave it. If it ain't broke, don't fix it.

Thanks.

However, I note that I can no longer use nuvexport in 0.23/ Karmic. I think this has to do with  libmyth-perl now  being referenced as  libmythtv-perl. 

I can't quite get my head around around the obfuscated description so favoured by those posting in linux technical forums :confused:

Does anyone know if the 10.4 RC addresses this issue?


Thanks

---

### Post by tgm4883 on 2010-04-24
> **GuiGuy said:**
> Thanks.

However, I note that I can no longer use nuvexport in 0.23/ Karmic. I think this has to do with  libmyth-perl now  being referenced as  libmythtv-perl. 

I can't quite get my head around around the obfuscated description so favoured by those posting in linux technical forums :confused:

Does anyone know if the 10.4 RC addresses this issue?


Thanks

I don't think nuvexport is supported anymore. Have you seen mythexport?

---

### Post by GuiGuy on 2010-04-24
> **tgm4883 said:**
> I don't think nuvexport is supported anymore. Have you seen mythexport?

I cannot get that thing to do what I want. In fact, I cannot get it to work at all. Although I wouldn't mind just 1 cent for every  minute I've spent on it. Seriously, I reckon it was stitched together and documented by the same team that gave us C.


**UPDATE: Thought I try it again; same dependency problem as nuvexport - it wants libmyth-perl which AFAIK is now libmythtv-perl**

Cheers

---

### Post by tgm4883 on 2010-04-24
> **GuiGuy said:**
> I cannot get that thing to do what I want. In fact, I cannot get it to work at all. Although I wouldn't mind just 1 cent for every  minute I've spent on it. Seriously, I reckon it was stitched together and documented by the same team that gave us C.


**UPDATE: Thought I try it again; same dependency problem as nuvexport - it wants libmyth-perl which AFAIK is now libmythtv-perl**

Cheers

Hmm, have you installed all updates?

---

### Post by GuiGuy on 2010-04-25
> **tgm4883 said:**
> Hmm, have you installed all updates?

Yes, I think so. As best I can work out  the 0.23 update introduced the libmythtv-perl package and uninstalled libmyth-perl, thereby creating the dependency problems.

UPDATE: I started a[ new topic thread here ]("http://ubuntuforums.org/showthread.php?t=1461956")so the issue the separated...

---

