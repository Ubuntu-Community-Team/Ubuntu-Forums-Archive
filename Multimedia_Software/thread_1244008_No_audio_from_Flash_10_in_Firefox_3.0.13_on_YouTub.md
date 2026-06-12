---
title: "No audio from Flash 10 in Firefox 3.0.13 on YouTube"
date: 2009-08-19
forum: Multimedia Software
---

### Post by figneutron on 2009-08-19
After hours and hours of struggle, I finally managed to install Flash 10 in Firefox 3.0.13 running Ubuntu 9.04. The reason I installed Flash 10 was to play videos on YouTube and other sites. When I had surfed to YouTube with Flash 9 installed, YouTube directed me to install Flash 10. Now, I am sure Flash 10 is operating on YouTube, because I right-clicked on the YouTube video screen and the message "About Flash 10" popped up. Furthermore, the Flash 10 player is listed on the Firefox/Tools/ Add-ons screen. However, even with Flash 10 installed, I still don't have audio on YouTube! Yet, I have audio when I play a music cd or listen to internet radio and also when I play the video in the /home/username/Examples directory, the one with the guy talking about the Ubuntu Forum. I hear him just fine. So, why don't I have sound when Flash 10 is playing on YouTube? By the way, I can't get any system sounds or effects to play even though my system sound files are in the right directory.

---

### Post by Lunatik-X on 2009-09-04
I'm having exactly the same problem, can someone please help? :???:

---

### Post by Holeposts on 2009-09-08
Someone keeps ignoring the fact this is a REAL problem.  Same issue.  Audio works everywhere but Youtube or other embedded videos.  I've tried upgrading browsers, reinstalling plug-ins, checking permissions, but I am rusty enough on Linux that I haven't found the solution to the problem that IS a problem.  I keep searching....

---

### Post by johanbove on 2009-10-06
Hi, i have the same issue on FireFox 3.5.3 with Flash player version 10,0,32,18.

No audio is audible or playing from any embedded flash video in either Youtube, Vimeo, etc.

It's not a rights problem since the ~/.mozilla folder has my ownership and group ownership.

Nor did it fix anything to remove cookies and reinstall the plugins.

---

### Post by VertexPusher on 2009-10-06
Try removing PulseAudio.

---

### Post by johanbove on 2009-10-07
Thanks! That seems to have fixed the issue.

---

### Post by Dirtpile on 2009-10-09
Thanks +1

Worked for me too, until I rebooted again in the morning that is. 

Anybody have a permanent solution?

Nevermind, it's working again.  Tried everything i could find with no success so i tried reinstalling pulseaudio and re-uninstalling it with complete removal.  Three restarts later and it still works.

---

### Post by juntjoo on 2009-11-28
> **VertexPusher said:**
> Try removing PulseAudio.
 okay, looks like we have a solution, but how do you go about removing pulseaudio?  i'm new to ubuntu so forgive me.

---

### Post by juntjoo on 2009-11-28
oh okay, i found it in some "synaptic" thing

---

