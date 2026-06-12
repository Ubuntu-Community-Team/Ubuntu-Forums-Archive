---
title: "HVR 1600 Digital/Analog/Svideo no Sound"
date: 2010-01-26
forum: Mythbuntu
---

### Post by srmcatee on 2010-01-26
Hello,

I have a Myth .22 system setup using Mythbuntu.  I have a HVR 1600 capture card.  

I have setup Digital TV and get video and sound just fine.  I have my DISH cable box connecting using Svideo and RCA jacks for sound.  The Svideo has video but I am not getting any sound.

My video is going out through HDMI from myth.  My audi is going out through digital audio (spif).

When I am on the Digital TV source I can also adjust the volume.  When I switch the input over to SVideo volume says 0% and I am unable to adjust it.

Any ideas?

Thanks in advance for any assistance you can provide.

---

### Post by SiHa on 2010-01-27
Is one of the 'Line In' options muted in alsamixer?

---

### Post by srmcatee on 2010-01-27
Yes.  Inline is on.  This is a new system.  I took a look at my old system which works and noticed PCM was in alsamixer.  But PCM is not showing in my new system in alsamixer.  Should it be there?

---

### Post by srmcatee on 2010-01-30
Okay,

I went into Alsamixer and turned on everything.  all playback and all capture.

I know have sound on live tv for both digital and analog.  However, when I schedule a show I get sound on digital but no sound on analog.  I however do get picture for both.

I am at my wits end.  So what could I possibly be missing.

---

### Post by epi 1:10,000 on 2010-02-05
I have the same issue for playback of analog capture on my HVR-1600.

---

### Post by srmcatee on 2010-02-05
I got it working!!!

I flipped everything on in Alsamixer.   I think it was a combination of factors.  But sound generally means it is an alsamixer problem.

---

