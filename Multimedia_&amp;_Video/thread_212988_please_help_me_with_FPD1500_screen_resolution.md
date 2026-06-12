---
title: "please help me with FPD1500 screen resolution"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by neilmac on 2006-07-10
Hi folks. I just installed the latest release on an old Gateway pc. It works brilliantly, I love it - except I can't get my monitor working properly. It's just running at 640x480.
Now I know a lot of people have had trouble with the FPD1500 and different flavors of Linux. I've searched Google and through forums and tried a dozen different suggestions and procedures. 
I think my card is an Nvidia Riva. (Sorry I've had a few machines since this one and lost the original spec).
Is there anyone out there who has had success making this monitor work with the latest version of Ubuntu?
Can anyone give me a sure-fire, can't-lose suggestion which I might have missed?
I notice a few people have given up trying Ubuntu when they haven't managed to sort out their video resolution. I'd really like to persevere and get this working.
Any help gratefully received.
Thanks

---

### Post by moore.bryan on 2006-07-10
usually, you can just use xvidtune to fix the issues.  type:

username@ubuntu:~$ sudo xvidtune

enter your password and follow the instructions.

---

### Post by neilmac on 2006-07-11
Thanks very much for the response
I tried that but it seems to control the position of the screen on the monitor and didn't let me change the actual resolution from 640x480. 
The more I research this the more problems I find people have had with this combination (by the way, the video card is the TnT2 Pro). 
I have tried all sorts of solutions found in forums and groups but nothing has worked so far. I really want to keep trying though; Ubuntu looks great, even in 640x480.
Anybody got any ideas or experience with the FPD1500 and Ubuntu?
Thanks again

---

### Post by orbish on 2006-07-11
what's the desired resolution?

---

### Post by neilmac on 2006-07-12
1024x768 would be perfect

I tried to edit xorg.conf by entering these details: 
[http://groups.google.co.uk/group/comp.os.linux.setup/browse_thread/thread/205342c8221c97/554a6194d9d112ee?lnk=st&q=gateway+fpd1500+linux+work&rnum=1&hl=en#554a6194d9d112ee](http://groups.google.co.uk/group/comp.os.linux.setup/browse_thread/thread/205342c8221c97/554a6194d9d112ee?lnk=st&q=gateway+fpd1500+linux+work&rnum=1&hl=en#554a6194d9d112ee)
but no success so far
I also tried following this tutorial (amongst others):
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
And then followed the instructions here:
[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)
No joy...

As always, any help gratefully received folks. There must be a way round this.
Many thanks 
Neil

---

### Post by moore.bryan on 2006-07-13
two things...
(1) try running xvidtune according to [www.xfree86.org/3.3.6/QuickStart6.html](www.xfree86.org/3.3.6/QuickStart6.html).

(2) edit xorg.conf to force it to include your resolution.

---

### Post by neilmac on 2006-07-18
Thanks for your suggestion.
Sadly no luck with the problem. 
I am going to try and shift this over to the nvidia drivers thread as that seems like a natural home for the problem.:)

---

### Post by moore.bryan on 2006-07-18
good luck with it...

---

