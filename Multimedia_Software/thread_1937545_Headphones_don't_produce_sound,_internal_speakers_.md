---
title: "Headphones don't produce sound, internal speakers keep playing"
date: 2012-03-08
forum: Multimedia Software
---

### Post by bakere01 on 2012-03-08
Hi there. I'm sure this is a pretty common question on the forum, but, unfortunately I've looked all over the net and I haven't been able to find a solution that worked for me. 

I'm running Ubuntu on my 2007 24" iMac. The soundcard is a Realtek ACL889A. I'm having trouble with my headphones in Ubuntu 11.10. What happens is whenever I plug in my headphones, the internal speakers continue to play, but I can't hear anything on the headphones. Anyone know of a way to fix this? Thanks in advance.

---

### Post by jerome1232 on 2012-03-08
Click on the speaker icon in the top right, click sound settings, click output and toggle between the outputs, toggle between the different connectors (drop down box at the bottom)

---

### Post by sikander3786 on 2012-03-08
> **jerome1232 said:**
> Click on the speaker icon in the top right, click sound settings, click output and toggle between the outputs, toggle between the different connectors (drop down box at the bottom)
Yeah, I had this problem too on one of my old AMD PCs. I call it problem because sound should automatically be switched to Headphones/Speakers when the jack is inserted. However I never got time to investigate it further and find a workaround but I strongly believe that it can be 'fixed'.

---

### Post by jerome1232 on 2012-03-08
> **sikander3786 said:**
> Yeah, I had this problem too on one of my old AMD PCs. I call it problem because sound should automatically be switched to Headphones/Speakers when the jack is inserted. However I never got time to investigate it further and find a workaround but I strongly believe that it can be 'fixed'.

If I recall correctly the alsa drivers for some cards just aren't up to par and don't support automatically switching the outputs when it detects the headphones being plugged in. This was a long time ago when I had this issue and looked into it for a laptop. That's my recollection of my research though.

I also remember switching to OSS4 solved the issue, but it was a pain and I ended up liking pulseaudio better because it worked better with mumble, the primary reason I was messing with my sound anyways.

---

### Post by bakere01 on 2012-03-08
Hmm. Unfortunately, the connectors menu only has one option, Analog Output. And I've been through all the choices for the hardware profile and I haven't had any luck. Any other ideas? It would be really great to get this solved. It's really the only major problem I'm having with my Ubuntu install. Thanks.

---

### Post by Yellow Pasque on 2012-03-09
Try adding this line to /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=imac24
```
Hopefully, it works on next boot.

---

### Post by bakere01 on 2012-03-09
That's one of the solutions I've tried but so far it hasn't done anything.  Anyway, I'm still hoping I can find a way to get this solved. I'm gonna look around on the net some more. If anyone knows of anything else I could try, that would be great. Thanks again.

EDIT: Well I was trying some possible solutions I found online and I've ended up in an even worse situation. I uninstalled pulse audio to see if that would help. But after that I lost ALL my sound. In my system settings the only hardware I have is Dummy Output. I tried reinstalling PA but no dice. Nothing is seeming to work. I've also tried to reinstall alsa but, again, no dice. Now, I can't even open alsamixer. I'm completely lost and a bit angry at myself. If any of you could help me solve this you have no idea how awesome you would be. 

Signed,
    Officially Desperate

---

### Post by bakere01 on 2012-03-10
Got it all fixed. HOORAY! Haha.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

That's the thread that helped me sort it out. I just need to reinstall gdm and ubuntu desktop. I can now access alsa mixer with the proper configuration. Sound works perfectly.

---

### Post by jerome1232 on 2012-03-10
:cool:Glad you got it worked out! Sorry we couldn't be of more help

---

