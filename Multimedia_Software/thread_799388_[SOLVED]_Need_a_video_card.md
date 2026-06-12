---
title: "[SOLVED] Need a video card"
date: 2008-05-19
forum: Multimedia Software
---

### Post by finlost on 2008-05-19
I have poked around with various Linux distros during the past six months or so.  The PC I was using seemed to have several hardware shortcomings IMO.  Of all the distros I sampled, I have to say Ubuntu's was the friendliest and the best dressed.

I have decided to put together a modest PC build on NewEgg.  (If anyone wants to see the components of my build, LMK)  I am having problems selecting an appropriate video card.  It seems as though there are horror stories after horror stories for many video cards.  Since I am a Linux newbie, I don't feel as though I have the ability to troubleshoot a video card that doesn't want to play nicely.

A little about my computer habits....I am not a gamer.  Nor am I a movie or TV watcher.  I do want a video card that is up to par and will keep me up to speed with graphics for several years. _[This card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130085") _is my current selection for my build.  After researching this forum, it seems that video cards with Nvidia chipsets can cause this ](*,) during install.

Should I steer clear of the video card I am eyeballing at the moment?   Any suggestions on a comparable video card?  With respect to price of a video card, it is important to keep it in check.

---

### Post by cor2y on 2008-05-19
That card will work with linux however its important to note nvidia is falling behind in terms of video driver support lately when you compare the advances ati is making.
So a few things to be aware of.
1) Do a clean install of ubuntu, if you are upgrading from a previous version this is where the problems with nvidia cards usually occur.
2) Stick with the default ubuntu closed source/restricted driver, unless your video card is a newer model like the 8800 and above stick with the closed source restricted driver from the repos, since there hasn't been a big update to the drivers nvidia has released.
3) After you nstall the closed source driver be prepared for weird colors in video playback (they reversed the hue settings in the video driver) in order to fix this adjust hue setting of your media player of choice either to the maximum or minimum settings, then the color will look like its supposed to.

On the Ati side of things just make sure its not too new a video card sometimes the closed source drivers don't yet support it if it is and you'll have to make do with the open source ones which are not bad but you will not have 3d enabled since its the open source drivers, the samething is true for nvidia as well.

---

### Post by finlost on 2008-05-19
....this is a free invitation to get me to spend money and no one else wants it?

---

### Post by tamoneya on 2008-05-19
That card should be fine.  I have used similar cards with 8.04 and had no problems.

---

### Post by cor2y on 2008-05-19
The video card you have picked out is a good one.

---

### Post by finlost on 2008-07-14
The card I linked in the original post installed without issue.  I did it under 8.04 and it was a new install.

---

### Post by kapatp on 2008-08-01
Nice to hear that it worked for you finlost. I am looking for one myself. 

One question here - that card, 8600GT, has two DVI ports with a max resolution of 2560x1600 - is that for the two ports combined or for each one? 

Pardon me for being dumb, the reason why I ask this: I have two monitors: 1680x1050 and 1280x1024, so that would make a total of 2960x1050 in horizontal arrangement. This is what I have been using till my old card burnt out :(

---

### Post by finlost on 2008-08-06
I am far from a hardware expert.  My best guess is the 2560x1600 is for each monitor.  I have never heard of it being combined.

---

