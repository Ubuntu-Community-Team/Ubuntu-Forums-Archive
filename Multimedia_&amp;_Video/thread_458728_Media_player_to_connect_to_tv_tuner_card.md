---
title: "Media player to connect to tv tuner card?"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by cooldudeny on 2007-05-29
Hi i just bought a tv tuner card for my laptop and i am looking for the media player to play the tv using the tv tuner card on my ubuntu right now i am using windvr application using windows xp 

please suggest me which is a good media player for this purpose and how can i download it into ubuntu 

and one more question how i will be able to install the drivers on ubuntu for my tv tuner card  coz the cd that came with it is for windows xp

thanks

---

### Post by tgm4883 on 2007-05-29
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by rsambuca on 2007-05-29
MythTV is a pretty complicated installation.  What do you want to do with your tuner card - use it as a PVR, or just to watch TV live?  If you want to use it as a PVR, then yes, mythtv is your best bet.  If you just want to view TV, there are a few different applications that you can use, depending on your card.

The driver you require will depend on the card.  What is the exact make and model of your tuner card?

---

### Post by tgm4883 on 2007-05-30
> **rsambuca said:**
> MythTV is a pretty complicated installation.  What do you want to do with your tuner card - use it as a PVR, or just to watch TV live?  If you want to use it as a PVR, then yes, mythtv is your best bet.  If you just want to view TV, there are a few different applications that you can use, depending on your card.

The driver you require will depend on the card.  What is the exact make and model of your tuner card?

I tend to disagree, it use to be a bugger to install, but not so much anymore, and much less when mythbuntu is released.  The guide I linked to is very good.  What capture card do you have.

---

### Post by rsambuca on 2007-05-30
> **tgm4883 said:**
> I tend to disagree, it use to be a bugger to install, but not so much anymore, and much less when mythbuntu is released.  The guide I linked to is very good.  What capture card do you have.

Wow, that looks a lot easier than when I installed it on Dapper!  I think it is still excessive if you are just viewing though (which I assume it is if using a laptop).

---

### Post by cooldudeny on 2007-05-30
> **tgm4883 said:**
> [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

to be honest i am really new to ubuntu to be able to install that complicated installtion all i want it to watch tv and to be able to record the show if i like so is there any other options for that or no ?

---

### Post by tgm4883 on 2007-05-30
If you just viewing tv, you can use other software to do that (or if your just recording an occasional show you can use mplayer).  But if you want a full PVR then I suggest mythtv (there are also plugins to expand functionality which is great)

There are a bunch of different guides in that link i posted that range from a single machine that is a stand alone machine, or also something with a desktop.  Mythbuntu should be released around October and shouldt have Mythtv .21 included (if it's out by then) which should also have some autodetection of hardware

---

### Post by cooldudeny on 2007-05-30
> **tgm4883 said:**
> If you just viewing tv, you can use other software to do that (or if your just recording an occasional show you can use mplayer).  But if you want a full PVR then I suggest mythtv (there are also plugins to expand functionality which is great)

There are a bunch of different guides in that link i posted that range from a single machine that is a stand alone machine, or also something with a desktop.  Mythbuntu should be released around October and shouldt have Mythtv .21 included (if it's out by then) which should also have some autodetection of hardware

what other media player will u suggest me ?

and the tv tuner i m using is super tv tuner which is like a data card and goes inside the laptop i think this is made in china or something  but not a name brand that alot of people might be fimilar with

---

### Post by rsambuca on 2007-05-30
We kinda need to know the exact make and model of the tuner to tell you what media player will work best.  Do you know the chipset by chance?  If you are in ubuntu, open a terminal (Applications -> Accessories -> Terminal) and enter```
lspci
```It should spit out a bunch of stuff, including your tuner card info.  Paste it all here if you don't know what you are looking for.

---

### Post by reclusivemonkey on 2007-05-30
TVTime is a good simple TV viewing application. Its in the repos, and has no dependencies I am aware of. If your card is recognised as a v4l device, it will "just work" in TVTime. Simply scan for channels and you are good to go.

---

