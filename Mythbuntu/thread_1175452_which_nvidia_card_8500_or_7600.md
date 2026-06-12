---
title: "which nvidia card 8500 or 7600?"
date: 2009-06-01
forum: Mythbuntu
---

### Post by zaprat on 2009-06-01
I have a 7600GT and 8500GT. Of these 2 cards, which is better suited for use in HTPC application. 
 
I have herd that 8500GT has better h/w decode & other feature support that the 7600GT. Is this correct? If so, does the additional features support offer advantages over the faster 7600GT card. Is the 8500 fast enough to handle the HD decode.
 
I also have a 8600GT (but the fan is a litte noisy) and it uses more power as is evident by the additional power connection required for the card. I think it is also a overkill. Hence I am no considering this to be good HTPC option. Do you agree?
 
PS. I use TV with PAL 720x576 50Hz:popcorn: for HD and SD.
 
PPS. Note, the card not being used will remain in the draw till I consider it useful for something else.

---

### Post by madverb on 2009-06-01
[http://lmgtfy.com/?q=7600GT+8500GT](http://lmgtfy.com/?q=7600GT+8500GT)

---

### Post by Slate8 on 2009-06-01
I would use the 8500 as it looks to support VDPAU: [http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

Hope this helps.

---

### Post by ian dobson on 2009-06-01
Hi zaprat,

As the 8500 supports VDPAU, I'd use it. VDPAU is hardware acceleration for NVIDIA cards under linux.

madverb - really helpful, maybe you can do better next time.

Regards
Ian Dobson

---

### Post by madverb on 2009-06-01
It never hurts for them to actually do the research themselves.

---

### Post by zaprat on 2009-06-02
thanks guys it is the 8500 then!
 
out with the screwdriver!

---

### Post by zaprat on 2009-06-05
Guys, just wondering how I go about enabling **VDPAU**. Is it in mythbuntu 9.04 and which version of nvidia driver do I need. 
 
I read some posts from sites indicating that it was only in development versions, but the were in relation to earlier versions of mythbuntu.
 
Links would be helpful, rather than crawling through go.........(not yet)......(not yet)....(nearly there).......ogle.

---

### Post by LorenzoS on 2009-06-05
This thread [http://ubuntuforums.org/showthread.php?t=1063102](http://ubuntuforums.org/showthread.php?t=1063102) gave me the info I needed to get it working, and I have only basic Linux skills.  Reduced my CPU from 99% to under 10% so it was well worth it.

---

### Post by ian dobson on 2009-06-05
Hi,

VDPAU will be available in MythTV 0.22, whenever that comes out. But a guy over at [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) has produced a "backport" where the VDPAU code is included in version 0.21.

I'm using the backport on my frontend and it works really well. With the backend running the standard mythbuntu weekly builds.

Regards
Ian Dobson

---

