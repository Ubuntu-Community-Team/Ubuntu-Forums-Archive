---
title: "No LiveTV nor record"
date: 2008-05-09
forum: Mythbuntu
---

### Post by NarsilAnduril on 2008-05-09
Hi all,

I've done a fresh install of mythbuntu 8.04, front and backend on same box, PVR-500, GeFoce 6800.

I can tune channels with the backend (find all channels, signal level 95%), watch tv (/dev/video0 and /dev/video1) in MPlayer, watch movies (xvid) in my frontend.

When I select LiveTV in the frontend, I get a black screen for 2-3 seconds and back to GUI. When I record a show, I don't get anything.

I thought about a right access problem, so I chmoded both video0 and 1 to 777, but nothing better.

I can't go further alone ... help needed !

Thanks

Diego

---

### Post by rtrevor on 2008-05-09
Have you checked the permissions on the directory you have configured for TV recordings in the backend setup? The 'mythtv' user needs read/write access to this directory.

---

### Post by NarsilAnduril on 2008-05-09
No I didn't, good suggestion. I'll do it as soon I'll back on my machine.

Question : how could that impact LiveTV ?

---

### Post by Nikas on 2008-05-09
> **NarsilAnduril said:**
> No I didn't, good suggestion. I'll do it as soon I'll back on my machine.

Question : how could that impact LiveTV ?

Live TV records what you see all the time. You are watching the recorded file in Live TV-mode. :)

Check your /var/log/mythfrontend.log and mythbackend.log

---

### Post by rtrevor on 2008-05-09
There's a decent overview of how / why it records the LiveTV here:

[http://www.mythtv.org/wiki/index.php/LiveTV#How_It_Works](http://www.mythtv.org/wiki/index.php/LiveTV#How_It_Works)

Let us know how you get on!

---

### Post by NarsilAnduril on 2008-05-09
> **rtrevor said:**
> 
Let us know how you get on!

Of course I'll do, just let me go back home (I'm currently at work ...)

---

### Post by NarsilAnduril on 2008-05-09
That's it : chmoded ~/records to 777 and it works. I'll look for a fine tuning of rights later.

Thanks for your help.

Diego

---

