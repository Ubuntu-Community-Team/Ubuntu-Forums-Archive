---
title: "Sound not being detected anymore"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by feardotcom on 2010-09-10
Sorry for the double post, wasn't sure if i had the right category for this problem.

Ok, im having a problem with my sound card. Here's what happened. I just got a new monitor/tv for my computer (widescreen) and i was trying to get Quake 4's video setting just right and i launched and exited the game about 2 or 3 times. The last time after i get the video settings i noticed quake 4 wasn't playing sound any more and i i figured it was the infamous idtech 4 linux sound issue again. After i exited i noticed the sound icon had the "--" and usually means its been muted. So i click on it and find out i have no sound controls so i go to the sound preferences to find out that my sound card doesn't even show up. I rebooted about 2 or 3 times to see if it would start working, no go. 

I booted into 10.4.1 live cd and my sound works just fine in there. So i look at the logs see if i can find anything useful and find a 3 posts around the same time i rebooted that says "ubuntu pulseaudio[1604]: pid.c: Daemon already running."

I found something in another thread, someone else posted, that suggests un-installing pulseaudio and reinstalling it. So i did and still no audio but the sound control icon on the top bar is missing now.

Im trying to avoid reinstalling cause i just got everything setup on 10.10 the way i like it.

side note: for the most part, i know my way around linux, but im completly lost when it comes to sound issues.

---

### Post by ranch hand on 2010-09-11
```

apt-get install indicator-sound

```
should get the indicator back.

What is your sound card of controller?

---

### Post by feardotcom on 2010-09-11
Im not at the house right now, but i think its Realtek ALC888? Its a gigabyte MA770T-UP3P mother board. I know the audio works, it was working before. I just dont know what i did to make it not work anymore. :-/

---

### Post by VastOne on 2010-09-11
Since you have posted it here I am assuming you are using Maverick.  Since Alpha 3 and now into Beta, in 9 of 10 boots I have to go into sound settings and re setup my surround sound settings and turn the sound back up as it will be all the way down.  This may be what you are seeing.  It is annoying but I am sure a fix is in the making.

And I have the same motherboard...

---

### Post by feardotcom on 2010-09-11
> Since you have posted it here I am assuming you are using Maverick.
Yes, sorry, i thought it was clear with my signature and labaled under my beans counter also. Sorry, I will point that first next time. :-/


There's no sound driver at all. If you go into sound preferences and hardware... Theres nothing listed. If you goto output it says for the output device as Dummy Sound, or Dummy Out, or Dummy something (sorry, again im not at home to see it or take a screenshot). So im not sure what the problem is.

---

### Post by feardotcom on 2010-09-11
I found out theres been several bugs reported about this issue for 10.10. No fix yet, so im reinstalling 10.04.

---

