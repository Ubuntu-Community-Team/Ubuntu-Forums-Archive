---
title: "Karmic: Sound playing through subwoofer, not speakers"
date: 2010-02-03
forum: Multimedia Software
---

### Post by opethfan89 on 2010-02-03
Hey guys,

I had posted previously [here]("http://ubuntuforums.org/showthread.php?t=1384850") regarding the problem I'm having with my laptop. The sound doesn't play through the main speakers, but instead plays through the subwoofer on the bottom of the laptop. The headphone/mic jacks don't work either. I've listed the relevant lspci -v code in my other thread, but I'm not sure what other information is needed (like I'm trying to find the exact sound card I have so I can google around for a solution but since everything in laptops is so specialized I don't really know what to look for).

I do apologize if this question has somehow been answered elsewhere but I've waited 2+ weeks for a response and have gotten nothing. Also, I tried following [this sticky thread]("http://ubuntuforums.org/showthread.php?t=205449") but the link it refers to in step (3) under general help does not work, so I cannot proceed with any of the directions.

I am anxious to resolve this problem as I just discovered compiz-fusion and it just makes it even more fun to be loaded into my Ubuntu install, and I'm anxious to make the full-time transition to Ubuntu but I won't be able to do that if I can't play music.

Thanks for any and all suggestions or help, and I do apologize for having to double thread for the same problem!

Thanks,

OpethFan89


***EDIT***: After some lucky googling, I found [this thread]("http://ubuntuforums.org/showthread.php?t=1073090&page=7"), followed the steps, and now I can listen to my favorite music in Ubuntu. Thanks again to the OP of that thread, saved me alot of time/frustration.

---

### Post by sleepee on 2010-02-04
i had the same problem with my hp dv7 3080..  i was about to point you to my solution, but i'm glad you got it fixed already.

but just out of curiosity, did your solution fix the sound from both the speakers and the headphones as well??


never mind...  my jack sensing issue was fixed by upgrading alsa to the latest version, 1.0.22.1
i just followed the simple instructions from here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
simple!

---

### Post by opethfan89 on 2010-02-06
Hey sleepe,

Actually the headphone jacks DONT work for me, but I'm going to follow your link and see if that works. For now, the sound works out of both speakers + the subwoofer. The only other thing is that when i shut down, there's this weird loud static noise that plays. Other than that, everything works perfect.

---

### Post by sleepee on 2010-02-11
well, seeing as we have similar models, i'm guessing your jack sensing issue should be fixed with the new alsa version...

BUT beware..
ever since i upgraded alsa, i've had a sound issue with flash..
it seems that if i put a flash video in firefox, no other system sounds will play..
and if i do it the other way around... if i play, rhythmbox or movieplayer, then there's no audio from flash videos...
but then again, i had also upgraded flash and the kernel at right around the same time, so it might not be alsa's fault.  it might work out fine for you, so you might want to give it a try.

but it's funny that we've had the same exact sound issues, because i also get that loud popping noise at reboot.  i'm actually about to start a thread on that to see if i can get any help with that..
since we have similar laptops, i'll give you the link to my thread so you can see if i can get a solution so you can follow it too and see if it works for you..

EDIT:
[http://ubuntuforums.org/showthread.php?p=8813312#post8813312](http://ubuntuforums.org/showthread.php?p=8813312#post8813312)
there's the link.. that way, if somebody helps me out with that loud speaker popping problem, you'll know how to fix it too..

---

