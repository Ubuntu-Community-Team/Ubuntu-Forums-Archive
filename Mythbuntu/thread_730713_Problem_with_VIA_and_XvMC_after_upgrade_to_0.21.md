---
title: "Problem with VIA and XvMC after upgrade to 0.21"
date: 2008-03-21
forum: Mythbuntu
---

### Post by mekis on 2008-03-21
After upgrade to 0.21 on one combined back-front and two frontends I have problem watching TV, both live and recorded. 

On the combined back-front the quality is very good so the reception works OK and on one of the frontends I have good quality after adjusting Video Playback Profile to Lean

But on the other frontend both Video and Audio freeze 3-5 times per minute   and sometimes I see shadows from the OSD. I use a VIA EPIA ML6000EAG and using Google found a possible explanation that there is a problem with VIA XvMC on this place: [http://svn.mythtv.org/trac/ticket/4930]("http://svn.mythtv.org/trac/ticket/4930")

Pleas help me with a solution to this problem.

---

### Post by superm1 on 2008-03-21
Yeah that bug was found after the backport.  It's fixed in hardy, but not likely to come back to gutsy.

---

### Post by mekis on 2008-03-21
Thanks for the answer Superm1!

I'll try the Hardy beta release on this frontend.

---

### Post by jstembridge on 2008-03-22
If you don't want to upgrade to Hardy I've set up some suitably patched packages for Gutsy:

[https://launchpad.net/~jstembridge/+archive](https://launchpad.net/~jstembridge/+archive)

---

### Post by mekis on 2008-03-24
I did an upgrade to Hardy beta but I’m still not happy with the quality. Watching live TV works normally OK but if I activate an OSD, for example using the M key, the video and audio still freeze regularly several times every minute.

My hardware settings:
VIA EPIA ML6000EAG motherboard, Hauppauge Nova-T-500 and LifeView FlyDVB-S.

I appreciate any suggestions for changed settings or error detection.

---

### Post by mekis on 2008-04-14
I have upgraded MythTV to the latest sub-version and now the quality is much better. It seems like live TV works best because when watching recordings or Video the playback freezes in between.

When using the OSD the situation is still very bad with almost complete freeze as long as the OSD is up.

Looking forward to see improvements in future releases.

Thanks for a good program!

---

