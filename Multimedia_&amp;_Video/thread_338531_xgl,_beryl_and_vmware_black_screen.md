---
title: "xgl, beryl and vmware black screen"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by lovenotes on 2007-01-14
I have an ubuntu 6.10 installation on my laptop with the firegl drivers. I installed vmware server and I'm running windows xp on it. I just installed xgl and beryl, and everything is looking fine, but if I start my virtual machine with windows xp now, the screen containing the vm is completely black. When i return to the gnome settings without beryl and xgl, I can see in the vm window how Windows is working and displayed well. Why is the screen getting black under beryl and xgl? If needed, I can post a screenshot for better understanding.

---

### Post by dabl on 2007-01-14
On the Beryl forum, it says "black window" is caused by insufficient video memory.  Don't know if that applies to VMware windows too.

---

### Post by crazydahveed on 2007-02-04
Did you ever figure out what the solution was to this?  It seems as though the problem is XGL, but not beryl.  If I am running xgl, but not , I have the same problem you described.  If I change into a gnome session, everything works just fine.  I moved to using the vmplayer because one of my apps requires I set the xorg.conf to use a 16-bit color rather than 24, and I was hoping the vmplayer would allow me to circumvent this and run beryl and xgl (which only run in 24-bit color).  So if you found a solution to this, it would be quite useful.

David

---

### Post by randreu on 2007-02-10
Hi, I had exactly the same problem. The only workaround i found is:

- Set Window Manager to Metacity (GNOME Window Manager) BEFORE running vmware
- Close session (logout)
- log in again in Xgl. Metacity is used as Window Manager
- Start VMware, and wait until the virtual machine is running and is correctly displayed
- Then, if you want, you can switch back Window Manager to Beryl

a little tricky, but at least that way i can use Beryl and vmware.

---

### Post by rjs82vette on 2007-02-27
or you could run your virtual machines in debugging mode, and they work with beryl. I think that the debugging mode slows them down but I have enough machine to make up for it.

---

### Post by crazydahveed on 2007-03-01
Ok, I will have to give that a try.  Debugging won't work for me, as I am using vmplayer to play games, but I will try using metacity.  I would not even mind using metacity while I am running vmplayer if that solves the problem.  I hope they fix this "white screen" problem with beryl soon - it is definitely annoying.  Thanks again.

---

### Post by ffxr on 2007-03-01
i had a similar problem.. try tweaking your beryl advanced options..

rendering path -> copy
disable GL yeild Setting... 

they cleared the 'black screen' with vmware for me.. which was really beginning to annoy me...

i use the standard version of beryl.

---

### Post by rjs82vette on 2007-03-07
I dont think it is a problem with beryl as I get the black screen when I use the xgl session without running beryl.

---

### Post by mfarley on 2007-03-18
> **rjs82vette said:**
> or you could run your virtual machines in debugging mode, and they work with beryl. I think that the debugging mode slows them down but I have enough machine to make up for it.

That's exactly what fixed it for me.. I wonder what the heck is going on there.

---

### Post by pablo13 on 2007-10-24
I was getting the black screen until I set the debugging flag ... now it works, but does anybody know why?


Thanks,
Pablo

---

### Post by ephman on 2008-04-08
oh my gosh!!! i've been trying to fix this blank screen issue for a while so long ago.  i'm so glad i found a fix.  yep debugging mode on full works for me too!  sweet.

thanks for the bandwidth,

ephman

---

