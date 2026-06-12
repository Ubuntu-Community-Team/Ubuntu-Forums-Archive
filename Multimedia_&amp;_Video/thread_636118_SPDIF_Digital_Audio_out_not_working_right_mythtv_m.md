---
title: "SPDIF Digital Audio out not working right mythtv mythbuntu"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by sonic6567 on 2007-12-09
Hello,

I have Mythbuntu (7.10) and am running it as a media pc.  I have most everything working great except my spdif digital audio out.

I have searched for days on this topic and found a lot of nothing.  There are tons of posts and web sites but none with a good explanation or solution.  They are all windows mentality: click around until it starts working :(

Right now I can get two channel pcm audio out of the spdif connection.  How can I get digital out? (Dolby 5.1, DTS)

thanks

---

### Post by aaltieri on 2008-01-01
Any word on this?  

I have a similar issue with Mythbuntu.  I previously had Edgy installed on my former server (RIP) and it also converted everything to PCM 2-channel sound.  No surround, even with surround source.

Of course, I also have an issue where my spdif goes mute on each reboot.  Still searching to forums for that issue.

Thanks!

Anthony

---

### Post by wiseweasel on 2008-01-04
I am having a similar problem.  I can't get digital audio output at all.  Not HDMI (Which is a known problem) or through my SPDIF output.

---

### Post by sonic6567 on 2008-01-24
I have had no real update on this.

I have found though that it appears to be working in a round about way.

Something with a non-standard digital signal being output by ubuntu perhaps? just a guess.

My receiver does not recognize the digital input as valid (it does not identify it as dolby or dts on the receiver screen) however, it does play it in what seems to be beautiful 5.1 surround.

Anyone have thoughts on this?

(no, it is not a problem with the motherboard or receiver.  If I run windows on the computer the receiver identifies the digital stream just fine.  Only linux has this issue)

---

### Post by JonCage on 2008-05-30
Has anyone had any luck with this? I'm just attempting to install Hardy Heron and not having much luck with the digital audio :(

---

### Post by prule on 2008-06-30
I have SPDIF output over optical cable running okay, with Mythbuntu 8.04.

I needed to go into the mythtv settings, and switch on AC3 passthru and DTS passthru.

Also, I ran alsamixer and unmuted iec958.

I've come across quite a few forum posts that discuss this, don't have references at the moment, maybe try googling 'mythbuntu spdif unmute'

Hope this helps.

---

