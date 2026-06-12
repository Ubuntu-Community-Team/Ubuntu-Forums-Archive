---
title: "[SOLVED] Exporting mp3 from Audacity"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by FuturePilot on 2007-10-24
I can't seem to figure out how to do it with the new version of Audacity that is in Gutsy. I go to File>Export Selected. Then I click on the Options button, but there's no option for mp3. I do have lame installed and Audacity knows where it is. I must be missing something really simple.:confused:

---

### Post by squaregoldfish on 2007-10-24
Just above the Options button is a drop-down list of file types - MP3 is in there.

---

### Post by aysiu on 2007-10-24
Try this:
[http://www.psychocats.net/ubuntu/audacity](http://www.psychocats.net/ubuntu/audacity)

---

### Post by rsambuca on 2007-10-24
Mine has mp3 in the "Options" section.  I think the first time I tried it when exporting a file, I had to physically type in the "name.mp3" with the mp3 file extension.  It then gave me a warning that I was about to save a .wav file with mp3 as an extension.  After I cancelled that, the next time I tried something, mp3 was in the "options" section.  Very weird.

---

### Post by FuturePilot on 2007-10-24
> **rsambuca said:**
> Mine has mp3 in the "Options" section.  I think the first time I tried it when exporting a file, I had to physically type in the "name.mp3" with the mp3 file extension.  It then gave me a warning that I was about to save a .wav file with mp3 as an extension.  After I cancelled that, the next time I tried something, mp3 was in the "options" section.  Very weird.

Yeah, I'm not seeing mp3 in there. I tried what you did but it didn't work.

---

### Post by aysiu on 2007-10-24
> **FuturePilot said:**
> Yeah, I'm not seeing mp3 in there. I tried what you did but it didn't work.
Try the link I gave before.

---

### Post by FuturePilot on 2007-10-24
> **aysiu said:**
> Try the link I gave before.

Yes, I also did that. Well, actually I didn't have to do much. Audacity already knew where it was:o But it knows where libmp3lame.so.0 is

---

### Post by FuturePilot on 2007-10-24
Ah, found it. This is a very odd way that this is implemented. You need to expand the  Browse for Other Folders and Select MP3 Files from the drop down menu there. Then you can click on the Options button for options on how you want it encoded. Thank you all for helping :D

---

### Post by Palmyra on 2007-10-28
> **aysiu said:**
> Try this:
[http://www.psychocats.net/ubuntu/audacity](http://www.psychocats.net/ubuntu/audacity)

Thanks.  This worked.

---

### Post by waxedwing on 2007-11-16
AHA! futurepilot was correct. It wasn't an lib problem for me either.
Just the weird export menu.
This should really be mentioned to the developers, it drove me crazy for awhile.

---

