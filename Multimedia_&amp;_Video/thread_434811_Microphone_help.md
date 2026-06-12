---
title: "Microphone help"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by dustin0 on 2007-05-06
I saw a few threads but none really helped. Well im running Ubuntu 7.04  My Microphone is made by Hama there wasnt a model number. Its plugged in and its like a microphone u can hear the voice in the speakers but it doesnt recoard anything. 

I got this output

dustin0@dustin0-desktop:~$ lspci | grep -i audio
**00:10.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)**
dustin0@dustin0-desktop:~$ 


Im trying to get this setup so I can call my girlfriend on Skype. The microphone does work on Windows XP


  - Dustin

P.S. I got this error when i try to pick my card

[IMG]http://i13.tinypic.com/67hbw28.png[/IMG]

---

### Post by dustin0 on 2007-05-06
bump

---

### Post by slugkilla on 2007-05-06
I have the same sound card that you have and my microphone does not record. This sucks! Every thing worked before I upgraded.

---

### Post by dustin0 on 2007-05-07
bump

---

### Post by slugkilla on 2007-05-07
Do you have on board sound? I do so I might try to plug my mic into that and see to see if it's the card.

---

### Post by dustin0 on 2007-05-07
No i only have a pci card.

---

### Post by Cappy on 2007-05-07
Use this: [http://ubuntuforums.org/showthread.php?p=2306168](http://ubuntuforums.org/showthread.php?p=2306168)

If the top section doesn't fix the error you'll need to use alsamixer in your console to fix it. I've read that this error is caused mainly by the "capture" not being selected in alsamixer.

Also see:

[http://ubuntuforums.org/showthread.php?p=2210477](http://ubuntuforums.org/showthread.php?p=2210477)

---

### Post by slugkilla on 2007-05-07
Here is my (still not able to record with) configuration. I figured that since we have the same, or at least similar, soundcard, Having pictures would help people to help us.
[[IMG]http://img250.imageshack.us/img250/9947/mixerah6.th.png[/IMG]](http://img250.imageshack.us/my.php?image=mixerah6.png)
[[IMG]http://img266.imageshack.us/img266/7632/mixer2on8.th.png[/IMG]](http://img266.imageshack.us/my.php?image=mixer2on8.png)
[[IMG]http://img266.imageshack.us/img266/4001/mixer3mw3.th.png[/IMG]](http://img266.imageshack.us/my.php?image=mixer3mw3.png)
[[IMG]http://img374.imageshack.us/img374/5786/mixer4oq1.th.png[/IMG]](http://img374.imageshack.us/my.php?image=mixer4oq1.png)

---

### Post by slugkilla on 2007-05-07
And here are some pics of alsamixer. 
[[IMG]http://img363.imageshack.us/img363/8445/mixer5yg7.th.png[/IMG]](http://img363.imageshack.us/my.php?image=mixer5yg7.png)
[[IMG]http://img119.imageshack.us/img119/4486/mixer6rt1.th.png[/IMG]](http://img119.imageshack.us/my.php?image=mixer6rt1.png)
[[IMG]http://img363.imageshack.us/img363/5850/mixer7jv2.th.png[/IMG]](http://img363.imageshack.us/my.php?image=mixer7jv2.png)

---

### Post by Cappy on 2007-05-07
I don't see anything especially wrong with your soundcard, slugkilla. You should try turning off the capture from Mic Boost (with the space bar). If that doesn't do anything, try turning it off on the mic and only turning it on on the "mic boost". 
It looks like it should already be working so you might end up having to try editing alsa's conf files to get it to work or upgrading your ALSA to the newest version which may have support for recording on your soundcard.

---

### Post by slugkilla on 2007-05-07
Well I got the mic to work on the motherboard's built in sound. The noise was so bad that I think I'm gonna need to just get a better card. I was only testing my system with a mic, I can't imagine what an instrument would sound like on such a system. Sorry I couldn't help out anymore with your sound problem.

---

### Post by Cappy on 2007-05-07
What fixed it?

---

### Post by slugkilla on 2007-05-07
Oh I just gave up on using the CMI sound card and enabled the on board chipset in my BIOS and plugged it in to the motherboard.

---

### Post by hanzomon4 on 2007-05-08
I have the same problem with an m-audio delta 66(ice1712-chipset)

---

