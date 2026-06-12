---
title: "Unity Panel Service crashing?"
date: 2011-02-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-02-07
I am using one of my alpha1 installs at the moment until the nvidia problems are sorted out.
I was surfing away and looked up at my system clock. It said the time was 1-24am, but the actual time was 6-21am. So I tried to click on it and nothing happened. Nothing else on the top panel showed any response when clicked on either. 
So I minimized the FF window and looked at my conky display. It showed that one processor was pegged at 100% and the other was at about 20%.
The offending program was unity panel service. I then opened system monitor and it showed that unity panel service (UPS, I like that :-) ) was using 98% of one core. I right-clicked on it and chose "end process". Everything went back to normal then.
Within a few seconds UPS returned as a running process in system monitor but it was "sleeping".
This problem has occurred before, usually after the laptop has been left unused for a couple of hours, but still logged in to Ubuntu.
Has anybody noticed anything similar?
Thanks.

---

### Post by MacUntu on 2011-02-07
Yes.

---

### Post by Quackers on 2011-02-07
Aha! :-)  Thanks for the confirmation! I'm not alone!

---

### Post by mc4man on 2011-02-07
A couple of times here - it did take a series of events to get it off and racing
(I believe here it was only w/ the current compiz and unity 3.4 which are quite easy to break

---

### Post by Quackers on 2011-02-07
> **mc4man said:**
> A couple of times here - it did take a series of events to get it off and racing
(I believe here it was only w/ the current compiz and unity 3.4 which are quite easy to break

I'd agree with that! The current unity breaks if I look at the sidebar :-)

---

### Post by mc4man on 2011-02-07
Just had it happen again here - still not sure what brings it on though having an app open w/ an 'untracked' (unseen), window and then restarting compiz to 'fix' is a good start to this, but by itself doesn't cause.

Unfortunately here it also starts the desktop 'refreshing' every 25 sec.'s or so, pretty hard to produce any useful info in that time frame

(this install is A2+, using nouveau 3d and unity, it can handle the increased heat levels I find nouveau produces though am considering dumping natty till nvidia-current comes back and the unity 3.4 variation of window issues is resolved.

---

### Post by Quackers on 2011-02-07
I've given up on A2 until the nvidia thing is sorted out - it's virtually unusable. Even in classic I'm having problems. 
So I'm back in A1 nowadays.
If I click on the 2 new items in the sidebar (Applications or Files/Folders) Unity crashes and wipes out everything but the desktop background. I just do Alt Gr+Sys Rq + K and log in again. That gets me up and running again.

---

### Post by mc4man on 2011-02-07
I set my laptop, which is about the same 'era' hardware as yours, (in sig?),  to A2+, using nouveau 3d > classic.
It's somewhat stable but because it has a pitiful cooling system (thanks dell), am not using much except to ck. on updates and see if I 'fixed' the random kernel panic it had been having since mid December on  any fresh install inc. A2 itself
(2 days, 50 - 60 restarts, no KP's

---

### Post by Quackers on 2011-02-07
I too had a couple of random keyboard light flashing kp's early on, but have had none for some time now.

---

### Post by mc4man on 2011-02-07
getting a little closer to being able to produce the race at will - screen in 'action'

---

### Post by Quackers on 2011-02-07
Aha! What did you do to get that at will? :-)

---

### Post by mc4man on 2011-02-07
I got to  go to a job for a bit, will try to narrow down when I get back.
Do you ever run apps from a terminal?, like for instance mplayer

---

### Post by Quackers on 2011-02-07
Sorry, I went out for a minute.
No I don't, or very rarely anyway.

---

### Post by mc4man on 2011-02-07
Well after coming back and a restart it is again proving hard to get this to happen 
I think that once it happens, if I only killed the process it was fairly easy to set UPS off again.

Anyway fairly sure it's related to the 'unseen' window issue in compiz, that's how I was getting it to come back  - by forcing some unseen windows.
Once compiz gets in better shape don't think this will be happening.

Actually find that the current unity/compiz/nux can work quite well as long as I stay away from certain things like leaving the places icons alone, not letting some windows get maximized and a few other...

(I've also disabled the 'grid' plugin, which when moving windows about I'd sometimes inadvertently maximize them and for certain windows that's a problem causer here.

As far a KP's - on one machine I had previously 'fixed' by using older udev libs, There may have been a kernel patch for this, whether in natty don't know but the issue has subsided here also on my A2+ install.

---

### Post by Quackers on 2011-02-07
Yes, I've had the odd "unseen window" problem too, which may have been connected to the UPS thing, but not certain.
Still good here on kp's - or more accurately the lack of them :wink:
Thanks for the feedback!

---

### Post by webme on 2011-02-07
> **mc4man said:**
> 

Actually find that the current unity/compiz/nux can work quite well as long as I stay away from certain things like leaving the places icons alone


Same thing with me!

---

### Post by mc4man on 2011-02-07
> Yes, I've had the odd "unseen window" problem too, which may have been connected to the UPS thing, but not certain

Well - did a restart, doing nothing too much out of the ordinary and it started up, this time w/ no unseen windows ect.
(maybe I shouldn't have used dconf-editor to add a date to the time area, but that seems fine.

Anyway there clearly seems to be different ways for this to occur.

---

### Post by mc4man on 2011-02-08
Quackers - 
there is a new update to compiz (0ubuntu10) that reports to deal w/ the 'unseen' windows
Will give it a good test here, hopefully in the near future nvidia will return and you can get from behind the xserver upgrade.

---

### Post by Quackers on 2011-02-08
> **mc4man said:**
> Quackers - 
there is a new update to compiz (0ubuntu10) that reports to deal w/ the 'unseen' windows
Will give it a good test here, hopefully in the near future nvidia will return and you can get from behind the xserver upgrade.

I've just run the updates so I'll be looking for the missing window :wink:  and I hope I don't find it :-)
Roll on nvidia-current update :-)

---

### Post by mc4man on 2011-02-08
It's looking very good, though ultimately was still able to create 1 unseen "unknown' window, though thru  a fairly atypical use involving synaptic and update manager

(probably best not to use synaptic in a maximized window though that alone isn't a big problem.

Now to see if USP goes off, so far so good there, though still have no clue what brings it on

---

### Post by Quackers on 2011-02-08
Nothing untoward here yet :-)
For me, the only thing that seems to set UPS off is to leave the pc logged in, but not use it for a couple of hours. In those circumstances UPS will sometimes go mental a few minutes after I start using the pc again. That's the only circumstances that seems to set it off here.

---

### Post by mc4man on 2011-02-09
So far so good concerning UPS - though the window issue isn't quite 'finished' yet, hopefully soon. (opera has been added to my small list of possible problem creating apps

---

### Post by Quackers on 2011-02-09
I left mine unattended for about 6 hours last night, but no UPS problem when I started using it again! That's good :-)

---

### Post by mc4man on 2011-02-10
Some nice updates to unity today, more to come
(this was a mention to a ups bug fixed, may or may not be related to what we were seeing. I'd think it's gone for good

Also expect a compiz update shortly that should finally put an end to to inadvertent untracked windows, tested the patch and can no longer create any. (though atm with compiz  you never quite know

---

### Post by ELD on 2011-02-11
Updated today doing a partial upgrade as kernel kept back, unity no longer hard crashes after a minute, now i can properly test :D

You can scroll on the applications window now too, although you have to pull the scroll bar, no mouse wheel yet.

---

### Post by Quackers on 2011-02-11
> **mc4man said:**
> Some nice updates to unity today, more to come
(this was a mention to a ups bug fixed, may or may not be related to what we were seeing. I'd think it's gone for good

Also expect a compiz update shortly that should finally put an end to to inadvertent untracked windows, tested the patch and can no longer create any. (though atm with compiz  you never quite know

New thread on that subject
[http://ubuntuforums.org/showthread.php?p=10448717#post10448717](http://ubuntuforums.org/showthread.php?p=10448717#post10448717)

---

