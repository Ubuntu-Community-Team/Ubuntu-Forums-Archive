---
title: "Mythfrontend on EeePC 901 and TV settings"
date: 2008-10-01
forum: Mythbuntu
---

### Post by ederopaa on 2008-10-01
Hi,

I installed a mythfrontend on an Atom-based EeePC 901. I have a slight issue watching recordings on it. Side to side movement can be seen in the picture as there is a kind of line in the middle separating the top and bottom of the screen and they don’t seem to be sync. Any ideas on the tv setting that will get rid of this?

Ede

---

### Post by rhpot1991 on 2008-10-01
> **ederopaa said:**
> Hi,

I installed a mythfrontend on an Atom-based EeePC 901. I have a slight issue watching recordings on it. Side to side movement can be seen in the picture as there is a kind of line in the middle separating the top and bottom of the screen and they don’t seem to be sync. Any ideas on the tv setting that will get rid of this?

Ede

Are you looking at HD or SD recordings?  My eee 1000 was able to play SD recordings just fine but HD recordings not so much.  To be honest I never looked into if it was a network issue or a lack of cpu, but the atom is a little underpowered for HD.

---

### Post by ederopaa on 2008-10-01
I am playing 720p recordings. rhpot1991 what are your video playback settings?

Ede

---

### Post by rhpot1991 on 2008-10-01
> **ederopaa said:**
> I am playing 720p recordings. rhpot1991 what are your video playback settings?

Ede

I think I was using the slim playback profile, I also messed around with the totem mythtv plugin.  Either way 1.6ghz is kinda weak for 720p I believe.

---

### Post by rhpot1991 on 2008-10-02
I revisited this last night and it seems that the 1.6ghz atom is powerful enough to actually play back HD.  My playback profile was cpu+.  Oddly though my eee seemed to stream the recording better over wifi than the wired connection, I had quite a few breakups both ways.

---

### Post by netslacker on 2008-10-02
What you described (horizontal line with the top/bottom slightly out of sync) is known as video tearing.  Try changing playback profiles in myth or probably your best bet is a newer/different video driver.

Does the eee have ATI vid or Intel or ... ? (I know nothing about them).  If it's ATI then you may be SOL as this is a common problem with the ATI video driver.  I believe tho it is resolvable with Intel...  Search for video tearing and you should find some good hints.  

I resolved this myself by ditching an ATI video card for nVidia... though I'm assuming in an eee you are stuck w/ what you got so hopefully you can resolve it through different drivers.

---

### Post by rhpot1991 on 2008-10-02
I'd recommend using the kernel from here as well:
[http://www.array.org/ubuntu/](http://www.array.org/ubuntu/)
Should have most of the drivers built in.

For the record, I tested with the mythbuntu weekly builds.

---

### Post by ederopaa on 2008-10-03
I was playing around with the the playback settings and I got a fairly good result with xvmc, xvmc-blit and bobx2. The only little thing is a thin blue line on top and bottom of the screen. However this does not occur when I use single field deinterlacing, but the deinterlacer is not sufficient. What are thin blue lines and any idea of how to get rid of them?

Ede

---

### Post by ederopaa on 2008-10-03
> **netslacker said:**
> 
Does the eee have ATI vid or Intel or ... ? 

Its an Intel GMA 950.

---

### Post by ederopaa on 2008-10-04
> **rhpot1991 said:**
> I'd recommend using the kernel from here as well:
[http://www.array.org/ubuntu/](http://www.array.org/ubuntu/)
Should have most of the drivers built in.

For the record, I tested with the mythbuntu weekly builds.

Thanks rhpot1991! Adams kernel works really well, even with cpu++. 

Ede

---

