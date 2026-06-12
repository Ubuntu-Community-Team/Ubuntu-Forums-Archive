---
title: "This is to Inform those using SB Live! 24bit"
date: 2006-01-27
forum: Multimedia &amp; Video
---

### Post by TechSonic on 2006-01-27
I've done a lot of homework on figuring out the problem with Sound Blaster Live! 24bit sound cards and why you cannot get full duplex sound.  If you're computer has an AC97 Type sound card built in, try using that one.  You will get full duplex, reguardless of how many programs are demanding to make noise.

Far as the Sound Blaster Live! 24bit goes, there aren't any type of OSS mixerhandling that works.  Right now only ALSA is able to run it and buggy at that.  OSS isn't going to work, sorry.  I've talked it out for 2 hours with Creative Labs, they say there wont be any driver releases for Linux for the 24bit.  They did release to driver developers, information on other cards, such as Audigy and Live! (Other versions) on how to handle it.  But apparently the 24bit gets cut out.  The 24bit does have some similar chips that make some detections think it's the Audigy LS.  That driver under CA0106 is the closest match for it at this moment.

Sorry for those of you wanting to get their 24bits running at full throttle.  I'll post new info when I get any on this.

I have an SB Live! 24 bit myself, I'd love to get it fully working.  Right now my onboard card, AC 97 is working at full throttle.

It's a shame that my AC 97 was buggy in Windows XP with bad mixer control.. I guess theres a shot at Windows.  They can't handle AC 97 and Linux can, but then again, they can handle 24bit and Linux can't...


>.>


PS, not sure about all types of AC97 though.
I'm currently using
C-Media Electronics CMI9761 (For OSS)
VIA 8235 (for Alsa)

---

