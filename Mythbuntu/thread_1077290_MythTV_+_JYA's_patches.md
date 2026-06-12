---
title: "MythTV + JYA's patches"
date: 2009-02-22
forum: Mythbuntu
---

### Post by TMcC on 2009-02-22
I'm now on my 3rd attempt at building a Home Theatre PC...

First was a few years ago; build in a large Silverstone LC16m, Nvidia Geforce 6800 I think...

Second was 5 months ago, got an IGP ATI HD3200 mini-itx board; this time in a much more WAF friendly (smaller) Silverstone LC19-S... great, I thought: AMD are now very open source friendly, it'll not be long before I can play HD videos at 1080p...

Third was about a week ago, got an IGP NVidia 8200 mini-itx board to replace the HD3200. 

Thanks to Mr Avernard's patches from the testing repository (fixes20018) I'm now able to play HD 1080p videos at 2% CPU, and fan noise is now almost inaudible :)

However, I'm having a few problems:

1. When starting Mythfrontend, xorg sits at 99% CPU for 60 seconds...

2. When moving around in Myth menus entering, for example, Setup->Media Settings->Video Settings, results in an Xorg at %98 CPU for around 90 seconds.

3. The High CPU also happens when entering the Media Library ->Play Online Streams functionality.

4. When leaving the Online streams -> apple movie trailers, I get a segmentation fault (without playing anything).

Anybody able to reproduce, or give me some hints? 

Nothing exciting in /var/log/mythtv, as far as I can tell.

---

### Post by TMcC on 2009-02-22
Problem was my fault; had just used the testing repository. Added the release one and did "aptitude safe-upgrade". Seems to have fixed everything.

---

### Post by blackoper on 2009-02-22
glad to hear you got it fixed. So how does your wife like it now that it is working correctly?

---

### Post by TMcC on 2009-02-23
> **blackoper said:**
> glad to hear you got it fixed. So how does your wife like it now that it is working correctly?

Well, the techo-fear is still there... but at least it doesn't crash when she uses it! Of course, there's a standing complaint about the number of remote controls there are. Tried added them into one, but then she complained that it was too complicated...

---

