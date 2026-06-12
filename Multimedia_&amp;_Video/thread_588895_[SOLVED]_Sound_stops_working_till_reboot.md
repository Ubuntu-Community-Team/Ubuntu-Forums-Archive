---
title: "[SOLVED] Sound stops working till reboot?"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by SomethingUniqueHere on 2007-10-23
Hey Guys,
So i was running fiesty just fine and upgraded rather than doing the fresh install.  The problem i'm having is that i'll come home after class and my sound doesn't work - this isn't all the time, just once in awhile.  When i reboot, everything works just fine.  Is there a way to reboot ALSA without doing a full system reboot?  Are there any log files i could examin that might give me some insight into the problem? 

As always,
Thanks

---

### Post by SomethingUniqueHere on 2007-10-23
Quick Update

I did this in a term:

ryan@ryan-desktop:~$ sudo /etc/init.d/alsa-utils restart
[sudo] password for ryan:
 * Shutting down ALSA...                                                 [ OK ] 
 * Setting up ALSA...                                                    [ OK ] 
ryan@ryan-desktop:~$ 

to reboot ALSA, problem is still persisting: no audio from rythmbox/youtube/anywhere.

---

### Post by SomethingUniqueHere on 2007-10-23
Using:
sudo /etc/init.d/alsa-utils reset

worked...

Why restarting didn't work but reseting did, i have no idea.  Hope this helps anyone else who runs into the same issue.

---

### Post by nostradamnit on 2008-04-10
Neither reset nor restart worked for me?!? I'll report back what eventually works...

---

### Post by crc294 on 2008-04-27
I'm having the same problem, running Hardy. Neither reset nor restart is working for me. The command ```
lsof | grep pcm
``` returns no results. Has anyone found a fix for this yet?

---

### Post by giosico on 2008-05-28
Ok ... This helped me solve my problem a little.

I think the problem is that firefox is holding or locking the audio ... free the lock .. and things go back to normal ...

So running

lsof | grep pcm 

And killing the processes it shows ... which happened to be firefox snd 

After that my movie player and vlc worked normally again

So my guestimate is this is a fire fox bug

oh using hardy with the default ff 3b5

---

