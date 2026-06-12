---
title: "Poor sound quality"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by midlandman on 2007-04-22
I hope someone here can help me with this.
I'm new to Linux...very new. I just installed the new Ubuntu and so far, I love it. Except for the sound. I have an onboard sound card and Sound Blaster Audigy Z2, and when I go to "Accessories>sound" the Sound Blaster shows up as the default. And everythng else is set to "ALSA".  But the problem is, it sounds terrible. There's very little volume and the overall sound quality stinks. 
I'm using the drivers that came with Ubuntu and the Sound Blaster website doesn't offer any new drivers for Linux. 
Can someone think of a fix for this? I did a search here and couldn't find anything related to this problem.
Thanks.

---

### Post by deadgobby on 2007-04-22
Disable the on board sound card in your BIOS.  After you boot up your system after changing your BIOS settings. You can double click on the sound icon. Once the box open up. Go to settings>preferences. Go ahead and click all the boxes on. Then play with the volume controls. On the switches tab key. Check if IEC958 is not checked mark. 
Enjoy.
Gobby

---

### Post by Spr0k3t on 2007-04-22
From a terminal (console), check to see what the master volume is when you run "alsamixer".

---

### Post by midlandman on 2007-04-22
Thanks guys. I did what you said and it sounds much better. It still isn't the way it was when I was using XP, but it is 100% improved.
And for "alsamixer", it's at the max. And there was no "IEC958". to check.
Thanks again.

---

