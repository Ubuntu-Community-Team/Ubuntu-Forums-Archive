---
title: "ATSC-110 &quot;no tables&quot; issue"
date: 2007-12-20
forum: Mythbuntu
---

### Post by Rhiadon on 2007-12-20
I appear to have the ATSC 110 firmware loaded as I get no errors in dmesg. 

But when I scan in myth for channels all I get are "no tables" after each channel when it doesn't have "no signal". I obviously expect to get "no signal".

What woudl be causing this "no tables" issue? I've dug around ont he net and in this forum quite a bit and can;t seem to find any information. 

Also, what information woudl be helpful in solving this issue?

I'm using mythbuntu 7.10. Anythign else that woudl be useful, please let me know.

Thanks,

Kris

---

### Post by Lester_Burnham on 2007-12-20
Hi,

I'm guessing, but I'd say it would be related to EIT guide data. The lack of it on those channels.

Lester

---

### Post by Rhiadon on 2007-12-21
A little more information: My TV with a QAM tuner has no problem scanning these channels at all. Also a few months ago I was using Mythdora and I was able to find those channels then. So I woudl find it odd that it's an EIT data related issue. I'm going to try to take all of my splitters out of the equation to see if it's a signal strength related issue.

---

### Post by Rhiadon on 2007-12-28
OK, I figured out what my deal was just in case anybody ever runs into the same problem. It turned out that I was not loading the firmware. I thought I had downloaded it and placed in the proper directory but I had not. One I placed the .fw file in the proper location, the driver loaded correctly and I was able to scan all of my local channels.

---

