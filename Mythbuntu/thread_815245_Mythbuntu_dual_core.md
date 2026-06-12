---
title: "Mythbuntu dual core"
date: 2008-06-01
forum: Mythbuntu
---

### Post by blairm on 2008-06-01
Hi,

With the approach of winter (living in NZ) it's time to get my long-delayed plans for myth going. 
Have spent hours reading stuff on the net, but I still have a few questions...

1) The cpu recommendations for mythbuntu don't seem to cover dual-core. Would an Athlon 64x2 4600+ (2.4ghz) be okay?

2) Have seen a bunch of postings on the web about the nvidia 8xxx series not having XvMC support, but have also seen postings that people are using them. Are they now supported? And how important is that XvMC support with the above cpu?

3) How difficult is it it to configure myth? Have heard horror stories! I've used linux for about four years and I'm happy to edit files and play with the command line, but I'm by no means an expert.

I'm viewing this as a bit of project- not expecting to have it all done in a weekend. Would want a combined front/backend box that's HD capable.

Any advice would be much appreciated,

Cheers,

Blair

---

### Post by superm1 on 2008-06-01
> **blairm said:**
> Hi,

With the approach of winter (living in NZ) it's time to get my long-delayed plans for myth going. 
Have spent hours reading stuff on the net, but I still have a few questions...

1) The cpu recommendations for mythbuntu don't seem to cover dual-core. Would an Athlon 64x2 4600+ (2.4ghz) be okay?

Sounds good to me

> 
2) Have seen a bunch of postings on the web about the nvidia 8xxx series not having XvMC support, but have also seen postings that people are using them. Are they now supported? And how important is that XvMC support with the above cpu?

Moot point when you've got a decent CPU like that.

> 
3) How difficult is it it to configure myth? Have heard horror stories! I've used linux for about four years and I'm happy to edit files and play with the command line, but I'm by no means an expert.

Much improved over the years.  The goal is to try to make mythbuntu as easy to use as we can.  Lots of GUI tools provided.  You shouldn't have to touch the command line for installation unless you run into hiccups with some of your hardware and need to debug it.

An entire install can be done via the GUI.

> 
I'm viewing this as a bit of project- not expecting to have it all done in a weekend. Would want a combined front/backend box that's HD capable.

Any advice would be much appreciated,

Cheers,

Blair
I can do an install in ~30 minutes for a FE/BE, so provided you don't run into trouble, i would say budget a  few hours and that's enough :)

---

### Post by blairm on 2008-06-01
Thanks for your help... that's cleared things up for me. 

Cheers,

Blair

---

### Post by zoiks on 2008-06-01
> **blairm said:**
> Hi,

With the approach of winter (living in NZ) it's time to get my long-delayed plans for myth going. 
Have spent hours reading stuff on the net, but I still have a few questions...

1) The cpu recommendations for mythbuntu don't seem to cover dual-core. Would an Athlon 64x2 4600+ (2.4ghz) be okay?

2) Have seen a bunch of postings on the web about the nvidia 8xxx series not having XvMC support, but have also seen postings that people are using them. Are they now supported? And how important is that XvMC support with the above cpu?

3) How difficult is it it to configure myth? Have heard horror stories! I've used linux for about four years and I'm happy to edit files and play with the command line, but I'm by no means an expert.

I'm viewing this as a bit of project- not expecting to have it all done in a weekend. Would want a combined front/backend box that's HD capable.

Any advice would be much appreciated,

Cheers,

Blair

1) Presumably you are talking about HD playback. I'm pretty sure those recommendations are getting a little dated. I think your processor has plenty of power. As an example, I'm using a dual core E8400 Intel, which is 3.0 GHz. During 1080i playback, my mythfrontend process is running about 35% on one CPU and xorg is running about 35% on the other CPU. This is with deinterlacing and whatnot. The 3.0GHz rule of thumb was for P4 type machines, IIRC, and your machine is both dual core and 64 bit, both of which are significant improvements in performance over a P4.

2) I doubt XvMC will be that useful to you. I'm sure you don't need it so it's better not to mess with it. I'm not even messing with it myself, since it makes your OSD black and white, adn other such stuff. But I'd still use the nvidia driver since it provides OpenGL sync'ing, correct resizing, and stuff like that.

3) It's not that hard. There are foobars involved, like if you are going to use QAM (over HDHR, for example), you have to do this process of entering the XMLTV IDs and other such stuff. For some reason, when I installed mythbuntu, the "mythconverg" database wasn't created so I had to do that (with the help of the mythbuntu forum). Also, if you choose new locations for your storage, other than the default locations in /var, you'll need to deal with the permissions stuff, like making mythtv's directories group-writable and such like that.

But I would say it's not that hard. I've been doing hand-rolled myth (compiled, system setup, everything) for 4 years on a SuSE system, and I can say using mythbuntu is a breeze relatively speaking.

---

### Post by tgm4883 on 2008-06-02
> **zoiks said:**
> 1) Presumably you are talking about HD playback. **I'm pretty sure those recommendations are getting a little dated.** I think your processor has plenty of power. As an example, I'm using a dual core E8400 Intel, which is 3.0 GHz. During 1080i playback, my mythfrontend process is running about 35% on one CPU and xorg is running about 35% on the other CPU. This is with deinterlacing and whatnot. The 3.0GHz rule of thumb was for P4 type machines, IIRC, and your machine is both dual core and 64 bit, both of which are significant improvements in performance over a P4.

Hardware recommendations can't become dated in the sense of we are talking about what we feel comfortable building an HD system with.  Anything more is obviously better.

---

### Post by zoiks on 2008-06-02
> **tgm4883 said:**
> Hardware recommendations can't become dated in the sense of we are talking about what we feel comfortable building an HD system with.  Anything more is obviously better.

I should have been more explicit. The old rule of thumb was "at least 3GHz processor to handle high-def". 3GHz P4 would barely handle 1080i, IIRC. I think with core 2 duos and the athlon equivalents and such, 3GHz is more than needed, and it won't be "barely" anymore.

---

