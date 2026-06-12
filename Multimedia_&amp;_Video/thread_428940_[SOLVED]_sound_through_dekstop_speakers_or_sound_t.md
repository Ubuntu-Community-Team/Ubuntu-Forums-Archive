---
title: "[SOLVED] sound through dekstop speakers or sound through headphones"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by theonlykman on 2007-04-30
Ok, I suppose Im a moron and this is more of a science question than anything but...
why is it that when I plug in my (crappy and old) desktop speakers into my laptop headphone jack, audio comes out crystal clear but when I plug in my (crappy but new) pair of headphones the sound is terrible? Same jack, same volume settings, everything.

Heres the kicker... with everything else equal, I can even plug my headphones into the jack on my desktop speakers and the sound is beautiful, but when I switch out the desktop speakers and plug  in my headphones directly into the laptop its crap...why???? I have tested this with other pairs of headphones, and with another pair of speakers and this is consistent through multiple reinstallations of 7.04, its no fluke.

Also, needless to say, everything works normally in windows and I can listen to substantially higher volumes in windows with the headphones than in ubuntu before it starts to go bad. But again, with external speakers, theres no problem.

Thanks for any ideas

---

### Post by theonlykman on 2007-05-04
No ideas, does this mean this problem is unique to me, cause that makes me feel special :s

---

### Post by theonlykman on 2007-05-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112260](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112260) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok Im attaching screens of alsamixer to illustrate my problem. With the first one, the volume is maxed out and it is all garbled through headphones. The second one is not much better. The third one is clearer but still a little fuzzy and finally the fourth one is clear but the volume is so low that its not worth using headphones in the places that I would feel the need to use headphones. Ive tried fiddling with the master volume and with "pcm" and with both together, but the result is the same as above. As far as I can tell "pcm-2" directly affects the speaker volume and nothing else, which is nice because thats a feature I dont get in windows. I just checked the headphones using xp and they work "like they should". Please please help! this is my last major hurdle with using ubuntu. As such, its really annoying that I cant fix it.

---

### Post by theonlykman on 2007-05-17
????? help

---

### Post by borris.morris on 2007-05-17
strange.

---

### Post by theonlykman on 2007-05-17
Tell me about it, Im starting to feel like Captain Ahab, with this problem becoming my whale...

---

### Post by theonlykman on 2007-05-18
Impedance mismatch...after getting some help and doing some research, this explains it.

So, does anyone know how to change (if its possible) the output impedance of my sound card so that it matches my headphones? I could get a different pair, but I was hoping that this would do it...

---

### Post by theonlykman on 2007-06-09
upgraded alsa driver to 1.0.14 and everything is fixed!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Chappy7777 on 2007-06-10
WTG! And I bet you know a whole lot more now than you did when you 1st started this thread. This was the 1st I saw it, or I would likely have steered you to alsa driver since it seems to be the main fix for unexplainable sound probs. Anyhow, enjoy the feeling of having learned some Linux. I'm glad you posted this, because I have a similar situation. I finally got some of my mp3s installed into Dapper today, and playing thru XMMS. But the speakers are old and have been totured by years of abuse. IOW, they sound like crud. And I do have a fairly decent set of headphones. The headphones will allow me to get away w/playing music anytime I want, as well.

---

### Post by theonlykman on 2007-06-10
Thanks. It really is a euphoric feeling and (I think) I learned a lot. I actually would have tried the new version earlier if it werent for a bad experience with Edgy. Back then I was having similar (yet worse) problems and so I installed 1.0.14 (still in rc at the time) and it made things worse. It was only yesterday that I checked back and, seeing that it was stable, said to myself "why not". Now I get channels labeled "Headphones" and "Speaker". The irony is that the Headphone channel does absolutely nothing, yet I still get the same functionality with the master channel so it doesnt bother me at all. Just as long as I can finally plug my headphones into my laptop and hear crystal clear!! hooray!

---

