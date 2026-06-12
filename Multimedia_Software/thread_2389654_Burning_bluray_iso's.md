---
title: "Burning bluray iso's"
date: 2018-04-19
forum: Multimedia Software
---

### Post by Joe_Linux on 2018-04-19
I am running Ubuntu 16.04 and would like to burn some bluray iso files. From 
[https://www.startrekcontinues.com/downloads.html](https://www.startrekcontinues.com/downloads.html)
I have the hardware is there any software under Ubuntu 16.04 that will do this gui preferred.

                                                Thanks

---

### Post by 1clue on 2018-04-19
I also have the equipment. I've never tried to burn a blu-ray movie due to the copyright issues. However it looks like you're in the clear with respect to these files.

Have you tried Brasero?

---

### Post by Joe_Linux on 2018-04-19
If you look at the link I posted there are no issues with copyright [https://www.youtube.com/watch?v=D6VL1OQrebg](https://www.youtube.com/watch?v=D6VL1OQrebg)
Brasero & K3B do not seem to work.

---

### Post by SeijiSensei on 2018-04-19
Looking at Settings > Programs in my K3b (on 18.04) I see wodim is used for burning, but apparently it doesn't support Blu-rays.  

According to [https://help.ubuntu.com/community/CdDvd/Burning#Blu-Ray_Burning](https://help.ubuntu.com/community/CdDvd/Burning#Blu-Ray_Burning), you need to install cdrecord and make it the default burning program in K3b. At the bottom of that article, it talks about using growisofs from the command prompt to burn BDs as well.

I don't use optical media much any more.  Big hard drives, memory cards, and USB thumbdrives are all a lot more convenient.

---

### Post by 1clue on 2018-04-19
I thought that the lack of blu-ray support was due to DRM. I suspect these isos are not recorded in a DRM mode. In which case it would just be like a really high quality home video, I would think it would work.

---

