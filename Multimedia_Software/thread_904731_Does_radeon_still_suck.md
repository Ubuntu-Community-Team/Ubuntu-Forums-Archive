---
title: "Does radeon still suck?"
date: 2008-08-29
forum: Multimedia Software
---

### Post by logophobia on 2008-08-29
I am going to buy a new video card. I am looking for a good price/quality card which ATI has at this moment. I really like the HD 4850. Do ATI cards, specifically the one I am going to buy, still suck on linux? I want to run it with 2 monitors, is that possible at this time? Any experiences you guys can share? I know they have this whole "open source drivers" thing going on, but I am looking for working stuff now. Gaming on windows and duo monitors+compiz on linux.

---

### Post by djRobbieF on 2008-08-29
IMO I'd never use an ATI card in Linux, when nVidia are so much better at OpenGL and easier to setup.

---

### Post by Crafty Kisses on 2008-08-29
If you're going to get a new video card and you're going to run Linux, go with nVidia.

---

### Post by markbuntu on 2008-08-29
The ati 4850 is defintely good to go on Ubuntu and linux and you will have very little problem with that card. They released their restricted linux drivers the same day as the card. ATI is also now fully supporting and providing funding for the open source Radeon effort so the open source drivers are catching up rapidly. Nvidia will be left in the dust.

There are a lot of sour grapes around here about ATI due to past disasterous missteps but there has been a wholesale turnaround in their attitude towards linux since they were aquired by AMD last year which has always supported open source. 

The current goal at ATI is to have linux drivers that are the equivalent of their windows drivers. They expect to accomplish this within the next six months. 

There are some issues with proprietary software from outside sources for older cards that cannot be released by ATI due to IP issues but the new cards have moved away from that problem and so the open source driver writers are getting everything. 

So, if you are expecting to use your new video card for a while, ATI may be the way to go. Nvidia is still stuck in proprietary mode and they have never fixed their 2D issues.

---

### Post by Crafty Kisses on 2008-08-29
Yeah, that's not to say ATI completely sucks in Linux, just a little bit more support with nVidia.

---

### Post by paulg on 2008-08-29
The real truth is likely something in between. NVidia still has the best driver performance for most cards when compared to the equivalent ATI. I believe this is still true.

Per Markbuntu's post ATI/AMD support is improving rapidly and the community is starting to see the payoff of their monthly release cycle. I have an X800PRO and lucky me this is one of the older cards that does have decent support in the binary driver. For me though, it's not quite as good performing as my 7600GT on another machine (Debian). From what I've read for those running the ATI X1### series cards it's been a struggle and Markbuntu's post covers the IP problems still existing here.

It will take some more time for 3D acceleration of the open source driver to match the binary ATI/AMD driver (if it ever happens but it's going to get better for sure) but just the fact that ATI/AMD releasing documentation on their products to the community does give a warm fuzzy feeling to this open source user. There is something to be said about supporting the companies that support open source.

Bottom line, if you don't mind using the binary driver, the open source community now has two choices. NVidia may be better performing for now but the future is bright for ATI/AMD. I think you'd be happy with either.

---

### Post by djRobbieF on 2008-08-29
> **Codename said:**
> Yeah, that's not to say ATI completely sucks in Linux, just a little bit more support with nVidia.

Agreed; I'm not saying "if you have ATI, you're stuck" - but what I would say is based on the first comment in this thread:  "I am going to buy a new video card."

If I were to recommend any new card, it would NEVER be an ATI.  Period.

If you HAVE ATI, sure, you can get it to work.  If you're buying a new card, however, don't get ATI; get an nVidia card.

Anyone concur?

---

### Post by circusmonkey on 2008-08-30
well I can safely say Nvidia geforce 9600 gt cards also suck , and wont work well....forget hardy

---

### Post by djRobbieF on 2008-08-30
> **circusmonkey said:**
> well I can safely say Nvidia geforce 9600 gt cards also suck , and wont work well....
Well, a 9600 is a very "entry level", low-end card.  So what do you expect?

In _extreme lay-terms_, nVidia's numbers represent:
a) First one-digit number = the version of the card
b) Last three numbers = how good the card is

9600 = abbb

A 7950 is better than an 8600, for example, even though if you were looking at the number in units of 1000, it seems it should be the other way around.  That's not the case.

A 9600 is a low-end 9xxx series card.  An economy card, most likely.  You can't expect too much from a x600-level card.


> **circusmonkey said:**
> forget hardy
Now, that's just nonsense talk.

---

### Post by lavinog on 2008-08-30
I have been a nVidia user for over 10 years. I recently started switching to ATI because of their linux and open source support. I just built a new machine and decided to go with ATI and have been happy with my decision. Now I am hearing that nVidia is having high failure rate issues: [http://www.bit-tech.net/news/2008/07/07/nvidia-warns-of-high-failure-rates/1](http://www.bit-tech.net/news/2008/07/07/nvidia-warns-of-high-failure-rates/1)

I am using a 3200 IGP (on board) and I am using the proprietary drivers which are very easy to install now, compared to the past.

The frame rates of the 3200 are high enough for compiz effects, but not enough for any major gaming. I can play ut2004 just fine, but with some reduced settings. I expect getting a dedicated card will make a drastic improvement.

There are two issues regarding desktop effects that are not bugs, but limitations of dri: opengl flicker and video flicker when compiz is enabled. This doesn't occur with the nvidia driver because nvidia has some sort of hack in place, while ati is focusing on dri2 to fix the issue. (dri2 got dropped from intrepid ibex)

Open source drivers are picking up very quickly, but currently 3d support is still limited on many cards.

---

### Post by ikhsan on 2008-09-06
> **lavinog said:**
> I have been a nVidia user for over 10 years. I recently started switching to ATI because of their linux and open source support. I just built a new machine and decided to go with ATI and have been happy with my decision. Now I am hearing that nVidia is having high failure rate issues: [http://www.bit-tech.net/news/2008/07/07/nvidia-warns-of-high-failure-rates/1](http://www.bit-tech.net/news/2008/07/07/nvidia-warns-of-high-failure-rates/1)

I am using a 3200 IGP (on board) and I am using the proprietary drivers which are very easy to install now, compared to the past.

The frame rates of the 3200 are high enough for compiz effects, but not enough for any major gaming. I can play ut2004 just fine, but with some reduced settings. I expect getting a dedicated card will make a drastic improvement.

There are two issues regarding desktop effects that are not bugs, but limitations of dri: opengl flicker and video flicker when compiz is enabled. This doesn't occur with the nvidia driver because nvidia has some sort of hack in place, while ati is focusing on dri2 to fix the issue. (dri2 got dropped from intrepid ibex)

Open source drivers are picking up very quickly, but currently 3d support is still limited on many cards.

I'm having a very hard time making a difficult decision whether to choose ATI or NVIDIA IGP for my next notebook. Since it's on a notebook, swapping graphic cards means swapping the entire machine hehe.

My ideal machine will be the Benq S41, with Nvidia 8600M graphic chip onboard. Unfortunately, with the recent development in the [Nvidia bad part story]("http://gizmodo.com/5023963/inquirer-every-nvidia-graphics-card-with-g84-or-g86-chipset-is-ready-to-die"), I can't really see myself buying notebook with Nvidia IGP.

On the other hand, my experience with ATI is not something to write home about. My current notebook uses ATI Mobility X300. I'm running Gutsy, with older binary driver and XGL to run compiz. It's not the greatest setup, but Compiz works,and xvideo runs fine while compiz is on. To run 3d Application, all I have to do is to make a new profile with XGL and Compiz off. My experience with newer binary driver is not smooth at all, with video and 3D games flickers like hell with compiz running or not. 
And since Hardy includes newer ATI driver and scrap XGL, I'm stuck with Gutsy..

I haven't tried ATI newest binary driver yet, but I really do hope that the recent development on ATI camp means that their graphic card is a viable choice for me.

---

