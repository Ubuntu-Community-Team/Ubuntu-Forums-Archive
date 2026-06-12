---
title: "Is it really possible to set up VLC to stream TV from TV tuner card ENCORE “ENLTV-FM3"
date: 2014-09-23
forum: Multimedia Software
---

### Post by Carolina_Lu on 2014-09-23
After 2 weeks of searching for any solution, I could say that I didnt  find any way to make this work. I'm on Xubuntu 12.04 from Work, and I  saw that with VLC was possible to capture TV and then stream it. So, I  decided to install my TV tuner, and then VLC. All those tutorials seemed  to be so easy to configure and all that, but... no one helped me. First  of all: 
  
1 - VLC detects my TV tuner perfectly, and it seems to take signal,  but it only shows that famous gray screen when no one channel could be  tuned.


2 - I can't change channels, to see if TV tuner syntonizes some of them, at least one!!!.
  
3 - Of course I can't test streaming till I can't set up previous  points. But, there's a problem... I couldnt find just only one tutorial  to explain me the correct way to stream in VLC. There're a lot of them  but referred to windows... those are very different than in Ubuntu, and  it can't apply. Many people told me that they couldnt make VLC work,  so... I dont know any other option in Ubuntu to do this what I need,  so... I hope you can help me with this!

  
My idea was to capture TV from TV tuner, and then stream it; no in  another software, but on a WEB page. Many tutorials say that it's  possible! and they do it, but... or it's about windows, or VLC version  they use is very old against the newest you find in Ubuntu Repositories  and it's almost impossible to adapt it (of course when I try, it doesnt  work anyway).

  

Any help would be very appreciated!

---

### Post by TheFu on 2014-09-23
Where are you physically located?  Country/city and what are the tuner standards there?  That tuner appears to be analog, so it will not work with many current digital broadcast or cable systems.  I know it will not work where I live.

So - please confirm that local TV is analog before doing anything else.  
Also are you using cable, satellite or an antenna? The standards for each are different.

---

### Post by deadflowr on 2014-09-23
Thread Moved to Multimedia

I don't know about VLC, but you can hook up a digital converter box through mythtv
[http://www.mythtv.org/wiki/Digital_Television](http://www.mythtv.org/wiki/Digital_Television)

---

### Post by Carolina_Lu on 2014-09-24
> **TheFu said:**
> Where are you physically located?  Country/city and what are the tuner standards there?  That tuner appears to be analog, so it will not work with many current digital broadcast or cable systems.  I know it will not work where I live.

So - please confirm that local TV is analog before doing anything else.  
Also are you using cable, satellite or an antenna? The standards for each are different.

I'm actually in Argentina, here we use PAL-N. This TV card is analog and I'm using cable to syntonize it... any idea?.

---

### Post by Carolina_Lu on 2014-09-24
> **deadflowr said:**
> Thread Moved to Multimedia

I don't know about VLC, but you can hook up a digital converter box through mythtv
[http://www.mythtv.org/wiki/Digital_Television](http://www.mythtv.org/wiki/Digital_Television)

I'm gonna check it out too, thanks!

---

### Post by TheFu on 2014-09-24
El Cuartito pizza forever!  THE best pizza in the world, IMHO. I've only checked 5 continents so far.
Just had to say that.

I haven't been back to BsAs since 2008, so this may be out of date. The apartment we rented had a cable box and about 100 channels. Didn't really look at it too closely. Sorry.

Before the digital conversion here, watching CATV happened in 2 ways:

1) if there is a cable box converter, it output on Channel 3 or channel 4 and the tuning of cable channels happened only on the cable box, not the tuner in the PC.  VCRs would be setup this way too - only on ch3/4.

or

2) the computer tuner card "knew" the CATV frequencies and would be told to scan those for specific channels. These were called "cable ready" cards.  TVs were also called "cable ready" and no cable-box was needed.

I'm not sure what "syntonize" means, but if you have a cable box between the computer and the wall, then I suspect only the cable box can tune stations and it will output on ch3 or ch4 only.

In both cases, some channels might be encrypted - usually the paid channels like HBO or SPACE, but local channels or "basic cable" would not have any encryption. Those will only be tuned though the cable box with a special code.

You probably know all this. Anyway, I hope the description helps someone with more MythTV experience than I to help you towards a solution.

---

