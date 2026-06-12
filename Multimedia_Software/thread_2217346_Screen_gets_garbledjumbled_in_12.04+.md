---
title: "Screen gets garbled/jumbled in 12.04+"
date: 2014-04-16
forum: Multimedia Software
---

### Post by Kamron on 2014-04-16
Hi, I upgraded (reluctantly) over a year now to 13.04, then 12.04 from 10.04 (my favourite Ubuntu) and since then I am having random episodes of my screen just getting jumbled/garbled. The computer freezes/doesn't respond and I have to do a hard restart. I can't seem to pin it down to any one event that triggers it, it seems to just happen out of the blue like that. It happened once on 12.04 while I was running it from the live USB. But hasn't happened since (though I am not using it long enough to tell). I've tried to repeat what I was doing at the time to see if I could trigger it but like I said it seems to just happen on its own. I am using an emachines with an Amd Athlon processor and Nvidia video card. All the times it happened I had the restricted drivers installed now, I do not and it hasn't seemed to happen as yet. I would like to know what is really causing it because it usually pops up when I am doing important stuff.

---

### Post by mörgæs on 2014-04-21
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

