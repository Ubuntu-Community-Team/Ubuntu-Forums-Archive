---
title: "Any successful use of M-Audio 2496?"
date: 2010-06-14
forum: Multimedia Software
---

### Post by jbarjoy on 2010-06-14
I have been looking for a sound card for stereo classical music.  The search has been frustrating.  The best-known maker is well known for games and DVDs -- special effects in other words.  One card works only on 32-bit distros, not 64-bit.  Other cards used to work well with Linux, but stopped several years ago, and all interested parties consider it low priority.  Others are priced outside my budget.
	
	From specs and price, the best card for me would be the M-Audio Audiophile 2496, a stereo-only card with reportedly great musical performance.  But it is one of those cards that stopped working around 2007, in Ubuntu and several other distros.  In the forums it appears to be caused by an incompatibility between ALSA and Pulse Audio, and involves the initialization for the ICE1712 sound chip. So several other M-Audio cards, and cards from other makers, are affected as well.  Comments in the Ubuntu forum trail off inconclusively.  Some partial solutions have been found that work for some people, but not for all.  Some reports say that a return to ALSA or even OSS works.  This is discouraging, and I will not spend $100 knowing that a failure is likely.
	
	But the best discussion appears in the Red Hat - Fedora forum for bug 499435.  The authors of the ALSA and Pulse systems get into the discussion, and in the resulting ferment, one correspondent develops a workaround consisting of a large change to a conf file, and a couple of little changes elsewhere.  The description of the change is followed by several messages reporting success with the card, finally.  But please note that this was NOT for Ubuntu.  You may find this discussion and the fix via Google by searching "m-audio 2496 red hat".  It's right at the top.
	
	The file requiring the big change is 
	/usr/share/alsa/cards/ICE1712.conf
	
	Looking into the same file in Ubuntu, I found that it contains most (not all) of the revision in Fedora.  Perhaps the differences between the distros require the modification to be different.  The change log for libasound2 (the package containing this file) has no discernable reference to this change, so I am left wondering about its source and validity.
	
	Still, I am not about to spend $100 without some assurance that the money is not thrown away.  So now, the question for which this entry was written:
	Is anyone out there successfully using an M-Audio Audiophile 2496 sound card with the current release of Ubuntu (10.04 or 9.10), using Pulse, ALSA, or OSS?   Everybody posts tales of woe.  I'm hoping to hear a few tales of success.
	
	Thanks a bunch!

---

### Post by cchhrriiss121212 on 2010-06-14
I have a card with the ice1712 chipset that suffers from the same issues as the 24/96 and it is running fine as long as I remove pulse. The problems only show up with distros using pulse audio, and my card works out of the box with distros that use pure ALSA (crunchbang in my case). I use this card regularly with 9.10 but have tried 10.04 successfully as well. 

[Here]("http://ubuntuforums.org/showthread.php?t=1507014") is someone here who is using the card successfully, and have heard reports of many others in the studio forums. You should be able to get one cheaper than $100 BTW, they go for about £30 used in the UK.

---

### Post by Breambutt on 2010-06-14
Worked out of the box in Hardy as far as I recall and requires the removal of PulseAudio or a **simple** copy/paste configuration file fix if you insist on using PA. There's a couple of different versions of M2496 but the same method works for most people, myself and my real life sidekick included. It's well supported by ALSA.

Personally I don't really see any reason to use PA with proper hardware, it'll just get in the way and JACK will be your tool of the trade anyway when in need of anything out of the ordinary.

What have you been reading anyway? I've heard nothing but positive feedback about this popular card.

---

### Post by jbarjoy on 2010-06-15
Thanks to you both for your replies.  You confirm my discovery from other queries that the problem results from conflicts between Pulse Audio and ALSA.  Some people have not been helped by removing Pulse, but then I have no way to know if the removal was well done. I think I will invest in a M-audio 2496.

Thanks again for your help.

---

