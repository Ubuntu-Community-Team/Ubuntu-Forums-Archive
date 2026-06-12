---
title: "MythStream Stopped Working"
date: 2009-02-26
forum: Mythbuntu
---

### Post by jdeslip on 2009-02-26
The mythstream plugin has stopped working for me in the last couple of days. 

It fails to havest any data from podcasts feeds (stays at harvesting forever).  I click a direct feed (like a live radio feed) it starts playing, but pressing ESC now hangs mythfrontend.  

It was working fine on the weekend.  I have no idea how I managed to break it.  I have tried uninstalling and reinstalling the mythstream packages and creating new storages for the streams.  But, nothing solves the problem.  

I can't figure out how to get meaningful debugging information (is there a way to tell mythstream to be verbose?  By running the frontend from the command line did have this message:

2009-02-26 09:29:04.688 XMLParse::LoadTheme using /usr/share/mythtv/themes/default-wide/stream-ui.xml
Wide character in print at /usr/share/mythtv/mythstream/parsers/podcast.pl line 110.

I am using the 0.21-fixes with vdpau backports - but I don't think myth packages have changed since it was working last.

---

### Post by jdeslip on 2009-02-26
Ok, I downgraded back the regular myth 0.21-fixes packages in mythbuntu from the vdpau patched ones, and this problem still exists.  My laptop which is just a mythfrotend has the exact same problem as well.  So, it is probably a problem for all mythbuntu users now.  Can someone else confirm this?

I cannot for the life of me think of what has changed since the weekend on my system that would have broken mythstream...

---

### Post by jdeslip on 2009-02-26
OK, I have no idea how this is the case - but the problem occurs after the update of the nvidia driver from 180.29 to 180.35 in the vdpau repo.  Every other package stays the same, and I have reverted multiple times to prove this is the source the problem.

---

### Post by agamotto on 2009-02-26
I have noticed the same this week.  I don't think it has anything to do with the video drivers, as going directly to wwitv.com shows that many of the links don't work for me in Firefox either...

---

### Post by jdeslip on 2009-02-26
I don't use any wwwitv streams.  For me, every stream in mythstream was broken.  It is definitely do to the 180.35 video driver in my case.  I confirmed it on two different machines only changing the driver.

---

