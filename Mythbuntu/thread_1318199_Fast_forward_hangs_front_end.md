---
title: "Fast forward hangs front end"
date: 2009-11-07
forum: Mythbuntu
---

### Post by gwagchunks on 2009-11-07
Hi Everyone

Another little issue I have is when I fast forward (usually anything faster than 30x definitely at 100x+) or chapter skip a few times, the frontend will hang and Esc does not work. I have to alt-tab and close the frontend. If I start a terminal session and check processes when this happens mythfrontend is taking 101% CPU! I thought it was because myth was having trouble with my usb hard drive on which I have my videos, but I tried using the SATA instead and get the same results. Can anything be done? Between this issue and the no recordings scheduled problem I have, the Wife does not want the box "in production" and I really don't want to give up the project after all the work that has gone into it.  :-(

---

### Post by SiHa on 2009-11-07
Sorry, I don't know the answer, but I sympathize with the WAF issue. I did get a text at work a few weeks back that said "It's that box or me!"

---

### Post by gwagchunks on 2009-11-07
> **SiHa said:**
> Sorry, I don't know the answer, but I sympathize with the WAF issue. I did get a text at work a few weeks back that said "It's that box or me!"

:lolflag: Computers... you gotta love um (cause the missus doesn't!) Saying that she saw the windows 7 advert on TV that wirelessly sends media to the TV from a laptop etc. and she says "Why can't we do that?" and I said "Thats what I've been trying to do with the myth box for months, but you won't let me set it up in the lounge" and she says "Well, test it upstairs for a week and if it works OK and I can use it without phoning you up for a week, you can". Now the gaunlets down I've just love to get these last couple of issues cleared! (My credibility as a computer guy is at stake!!!)

---

### Post by LorenzoS on 2009-11-07
I had this same behavior and fixed it by switching to vdpau to offload video processing to my nvidia card. Reduced cpu from around 100% to 10%. I did this with the avenard patch to 9.04 but I believe vdpau is now a standard part of 9.10 and mythtv 0.22.

---

### Post by gwagchunks on 2009-11-07
> **LorenzoS said:**
> I had this same behavior and fixed it by switching to vdpau to offload video processing to my nvidia card. Reduced cpu from around 100% to 10%. I did this with the avenard patch to 9.04 but I believe vdpau is now a standard part of 9.10 and mythtv 0.22.

I need to check to see what cpu is used normally, before using fast-forwarding or skipping. I'm not using HD so I'm surprised that a core 2 duo would run at 100% cpu, but using my 8800GT card could bring cpu down to 10%? That's interesting. I'll have to give it a go. I've not considered VDPAU yet (as I didn't know really what it was all about). Thanks for the pointer. Something to try tomorrow.

---

### Post by gwagchunks on 2009-11-11
Well my CPU is only around 4-10% on mythfrontend.re. I found this link by googling around, but I don't know how to implement it?

[http://svn.mythtv.org/trac/changeset?old_path=%2Ftrunk%2Fmythtv%2Flibs%2Flibmythtv%2FDVDRingBuffer.cpp&old=20654&new_path=%2Ftrunk%2Fmythtv%2Flibs%2Flibmythtv%2FDVDRingBuffer.cpp&new=20654](http://svn.mythtv.org/trac/changeset?old_path=%2Ftrunk%2Fmythtv%2Flibs%2Flibmythtv%2FDVDRingBuffer.cpp&old=20654&new_path=%2Ftrunk%2Fmythtv%2Flibs%2Flibmythtv%2FDVDRingBuffer.cpp&new=20654)

---

