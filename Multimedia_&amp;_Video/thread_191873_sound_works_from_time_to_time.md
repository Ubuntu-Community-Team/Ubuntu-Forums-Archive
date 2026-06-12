---
title: "sound works from time to time"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by PTR on 2006-06-08
At the beginning I want to say hello everyone. My English isn't perfect but i'll try to write as well as I can.

    I have a problem with sound. Not only me, I read about other people with the same thing. Sound sometimes is working and sometimes isn't. I have all needed codecs, two  sound cards (1: "VIA" on board, and second "C-Media" which I use). System is set to use C-Media with ALSA. Sometimes it's working but only to reboot. After reboot it's a lottery.
    However, when I installed game (Heroes 3 for linux) I have sound every time when I turn computer on, but only in this game. In movies,  music and everything else I have to reboot, reboot, reboot until sound will work.


Could someone help me with this?

ps. I have this problem with Dapper only. With Breezy everything was ok.

---

### Post by jonjpeterson on 2006-06-08
I have a very similar problem - I never know whether I will have sound at each reboot. I put alsamixer-gnome form synaptic and had sound two or three reboots in a row and thought I had it fixed, but no - every time is a crap shoot. If there is anyone that knows how to fix this please help. Breezy worked great and Dapper has this little problem.

---

### Post by PTR on 2006-06-10
Finally I have sound working every time. 
I killed esd and it helped. But is esd needed? Am I losing something in exchange?

---

### Post by jonjpeterson on 2006-06-10
How did you kill ESD and how many times consecutively has the sound worked for you. I had five consecutive and then one lost sound and now it's back again.

---

### Post by PTR on 2006-06-11
As i said it was more like lottery. Sometimes I had sound after 1 reboot (rarely), sometimes after 5.
I killed esd in gnome using "System Monitor".

---

### Post by Jason_25 on 2006-06-11
[QUOTE=PTR]As i said it was more like lottery. Sometimes a had sound after 1 reboot (rarely), sometimes after 5.
I killed esd in gnome using "System Monitor".[/QUOTE]
You can stop it from starting every time in the sound control panel.

---

### Post by PTR on 2006-06-11
[QUOTE=Jason_25]You can stop it from starting every time in the sound control panel.[/QUOTE]

Thanks but I don't have to. I did it only once and it's enough.

---

### Post by jonjpeterson on 2006-06-11
I killed ESD and got it working again for about five consecutive and its gone again. Has anyone else run into the problem popping up again after they thought it was fixed.

---

### Post by Jason_25 on 2006-06-11
[QUOTE=jonjpeterson]I killed ESD and got it working again for about five consecutive and its gone again. Has anyone else run into the problem popping up again after they thought it was fixed.[/QUOTE]
If you don't want it running, why don't you disable it in the control panel?

---

### Post by jonjpeterson on 2006-06-11
How would I know weather I want it running or not. I'm new to Ubuntu and had everything working in breezy, but now with dapper I have all sorts of glitches. I just want my sound to work everytime all the time. I can follow the flow of someones script or whatever you call it, but I don't know how to create my own to get everything working. I'd love a howto on getting my sound to work - if I needed to take all the sound stuff off first I'd need to know how to do that first. If you can help I'd appreciate it a ton.

---

### Post by Jason_25 on 2006-06-11
Well esd works with alsa to combine multiple sounds at once as I understand it.  But it causes alot of problems too with microphones and sound cutting out.  It's just a check box in the sound control panel.  You could experiment with it off, and then check it again to turn it back on.

You shouldn't need any "scripts" to get your sound to work.  Tweaking what you have a little should get you what you want eventually.

---

### Post by PTR on 2006-06-12
[QUOTE=jonjpeterson]Has anyone else run into the problem popping up again after they thought it was fixed.[/QUOTE]
In my case it's fixed. 
As  you said you have very similar problem. Maybe you need very similar solution.

---

