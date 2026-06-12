---
title: "New System - Hardware Feedback and Suggestions"
date: 2008-02-16
forum: Mythbuntu
---

### Post by poke4christ on 2008-02-16
I'm dreaming up a system right now that I'm thinking about building sometime soon.  I want it to be compact, quite, and powerful enough for two HD tuners.  I also might use it for some other basic network functions such as network storage.  So, here's the hardware I'm considering right now.

[Shuttle SG33G5B]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856101062")
[Core 2 Duo 2.66GHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115029")
[G.Skill 4(2x2GB) DDR2 800]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122")
[2x320GB HHD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152054")
[DVD Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827129018")
[2x pcHDTV HD tuner]("http://www.pchdtv.com/")

Uses
-HDTV watching
-DVD watching
-Network Storage (time machine backup if possible)
-Music listening
-emulation gaming (mostly old-skool)
-Hopefully blu-ray movie watching in the future
-5.1 audio

What where I'd like help:
-For this setup, I'd have to use the integrated HDMI video, will that be enough for 1080p?  I'm a little worried about this.  There are only two PCI slots and the tuners take up both.
-Is this more power than I need?  It seems like all the talk about necessary power is talking about older hardware.  Can I dumb it down and reduce the price yet still get the same performance?
-What tuner would you guys recommend?  Is pcHDTV the best for HD?
-I still need a remote for this and the tuners don't have one built in.

---

### Post by newlinux on 2008-02-16
I don't have much experience with Intel video and HD but really your processor will be doing all the work, so it should be powerful enough. I'd stick with nvidia wherever possible.

It is more power than you need. To display mpeg2 HD (even 1080p) really doesn't require much CPU speed by todays standards. Any dual core will do, and even less than dual cores can do it. However, it is useful to have more power for commercial skipping and transcoding if you will do a lot of that. It just makes it faster. That said, my X2 3800 is plenty powerful enough for my needs.

I think the pcHDTV is overpriced and doesn't really offer any quality gains over other digital tuners. I'd go with the kworld ATSC 110 or 115. 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815260005](http://www.newegg.com/Product/Product.aspx?Item=N82E16815260005)

I'd go with the MCE remote. Well supported and performs well.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851](http://www.newegg.com/Product/Product.aspx?Item=N82E16880100851)

---

### Post by poke4christ on 2008-02-16
Well, I feel a little stupid for not thinking about this before, but I have an old ATI remote wonder II from my first media PC (windows desktop and tv combo).  I think I might give that a try first.  Now I didn't see it mentioned on the LIRC, but I thought I had seen it mentioned before as working.  Anybody know?

As for the tuner, I guess I would still need two of those for dual HD.  With the dual tuner, One of them said digital and one analog.  I would assume that means only one for HD.  Could be wrong.

What do you think about the ram?  I'm sure I could probably get by on one stick of 2GB :D.  Could always add another if I want.  I might tone down the processor too now that you've mentioned I don't need all that.  If I can cut a couple hundred (even though it's already a sub grand system) I'd love that.

---

### Post by newlinux on 2008-02-16
2GB is plenty. That's the most I have in any of my HD Myth systems. 

Yep, they can only tune one stream at a time, so you'd still need two to do two HD streams at once. I have three Kworld ATSC 110s (almost identical to the 115s) and they work well for me. You could also look into the HDHomerun, which is popular (and is a dual digital tuner).

Yeah, I'd give that ATI remote wonder a try as your remote.  It seems to be supported:
[http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder](http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder)

My HD systems are P4 2.6 HT, X2 3800 and X2 4200. I used to have a AMD 64 3500+ that did HD as well. Now if you are going to be doing H.264 1080p, which is much more compressed, you might want more power. However I've done 720p h.264 in both of my dual core systems without any problems. Never tried 1080p h.264. I'd go with a dual core, of course, but probably just get the one that is the best deal.

---

### Post by poke4christ on 2008-02-16
> **newlinux said:**
> 2GB is plenty. That's the most I have in any of my HD Myth systems. 

Yep, they can only tune one stream at a time, so you'd still need two to do two HD streams at once. I have three Kworld ATSC 110s (almost identical to the 115s) and they work well for me. You could also look into the HDHomerun, which is popular (and is a dual digital tuner).

Yeah, I'd give that ATI remote wonder a try as your remote.  It seems to be supported:
[http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder](http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder)

My HD systems are P4 2.6 HT, X2 3800 and X2 4200. I used to have a AMD 64 3500+ that did HD as well. Now if you are going to be doing H.264 1080p, which is much more compressed, you might want more power. However I've done 720p h.264 in both of my dual core systems without any problems. Never tried 1080p h.264. I'd go with a dual core, of course, but probably just get the one that is the best deal.

I've noticed that the amd chips are a lot cheaper than the intel duos. I see you are using the x2s  what do you think about them?  How does speed compare with the duos?

---

### Post by newlinux on 2008-02-16
They are a bit slower than the duos from my perspective, but plenty fast enough for what I need and much less expensive. The faster AMD X2 are more than enough for HTPC needs.

---

### Post by poke4christ on 2008-02-16
Question on the integrated graphics.  Since it's using the processor I guess I can assume that it's not going to be XVideo compatible right?

---

### Post by poke4christ on 2008-02-16
Couple more questions (I'm loading you down I know)

-Is the shuttle box/barebones PC the way you would go?  It seems to be a good option for small PCs
-I'm wanting it pretty quite.  What would you suggest for helping this?  From my experience the heatsink is the biggest sound problem.

---

### Post by poke4christ on 2008-02-16
Okay, I've got a little bit of a new setup here.  If it will still give me plenty of performance, then I'm all for it.  Plus, I'm saving almost 400 dollars on this.  I was looking at around 940.  Now it's about 570.  Quite the improvement I would say.  Anyway, here's what I'm looking at.

[AMD Athlon 64 X@ 4000+ (might up it a little since it's cheap)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103774")
[ASUS Barebones Case and MB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856110061")
[2x320GB HHD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152054")
[DVD Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827129018")
[G.Skill 2GB (2x1GB) DDR2 800 Memory]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231098")
[2xKworld HDTV tuner]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815260005")

---

### Post by newlinux on 2008-02-16
Looks good to me. This is similar to one of my systems (AMD X2 4200, Asus P1-AH1 with nvidia 6150 onboard, 2GB). Looks good on my Plasma (runs at 720P). As far as quiet goes, just look for reviews on your case and fans. Also, watch out for vibrational noises, especially from the dVD drive and hard drive (and get a quiet hard drive too). They don't make the P1-Ah1 anymore, they make the AH2 now, but it is identical with an upgraded CPU socket (for AMD the ah1 is 939, Ah2 is AM2). My P1-Ah1 is pretty quiet. Going up a little on the CPU might be good - the CPU won't have to work as maybe stay cooler... But that is plenty powerful enough for what you've described...

---

### Post by poke4christ on 2008-02-16
> **newlinux said:**
> Looks good to me. This is similar to one of my systems (AMD X2 4200, Asus P1-AH1 with nvidia 6150 onboard, 2GB). Looks good on my Plasma (runs at 720P). As far as quiet goes, just look for reviews on your case and fans. Also, watch out for vibrational noises, especially from the dVD drive and hard drive (and get a quiet hard drive too). They don't make the P1-Ah1 anymore, they make the AH2 now, but it is identical with an upgraded CPU socket (for AMD the ah1 is 939, Ah2 is AM2). My P1-Ah1 is pretty quiet. Going up a little on the CPU might be good - the CPU won't have to work as maybe stay cooler... But that is plenty powerful enough for what you've described...

Do you have dual tuners on your AH1?  Are you using the integrated video?

also, I noticed that the case I've got has one PCIe and one PCI.  Is PCI compatible with PCIexpress.  If not then I might have to switch cases.

---

### Post by poke4christ on 2008-02-17
Well, I found out PCI isn't compatible with PCIe.  Looks like I either need a new Case or need to go with a HDHomeRun.  I think I'm liking the HDHomeRun though.  Also, I'll have room for a Graphics Card if I decide i need it.

---

### Post by Caps18 on 2008-02-17
Do you have the two hard drives already or are you planning to do RAID?

I bought a 750 GB SATA drive at Best Buy (it was in a Western Digital external USB drive), and I am using that right now.

The reason I went with the pcHDTV tuners is because I like supporting Linux hardware were I can.

---

### Post by poke4christ on 2008-02-17
> **Caps18 said:**
> Do you have the two hard drives already or are you planning to do RAID?

I bought a 750 GB SATA drive at Best Buy (it was in a Western Digital external USB drive), and I am using that right now.

The reason I went with the pcHDTV tuners is because I like supporting Linux hardware were I can.

I'm might do raid 1 till I fill it up. I haven't thought about it too much.  I think the big thing was just that I wanted two instead of one.  Why do you ask?  Do you have a deal you'd suggest?

---

### Post by newlinux on 2008-02-17
I'm using the integrated video. The Ah1 only has 2 PCI slots and I used to use it for dual tuners, but I have since moved them to another backend, but they worked fine while they were there. Keep in mind, that if your box only has PCI slots you will be forced to use the integrated video, since PCI can't support video cards that can do HD (need to be AGP or PCIe). PCIx is not backwards compatible. PCI cards won't work in PCIx slots and vice versa. Oooh.. looks like you already found that out.

---

