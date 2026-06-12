---
title: "kdenlive rendering problem"
date: 2008-01-21
forum: Multimedia Production
---

### Post by actionist on 2008-01-21
i am using kubuntu gutsy/amd64/2Gb memory-- whenever i try to render video more than about ten minutes duration, the system crashes-- total shutdown of computer-- I am a filmmaker and I want to entirely shift to open source, but this last step is not working! :( 
I tried the render in cinelerra too, but the same thing is happening there too. Please help.

---

### Post by cotcot on 2008-01-21
I have (ubuntu) on amd64 /2GB as well. Rendering in kdenlive and cinelerra works fine. However the longest video i have rendered is 18 minutes. So basically it should be possible. Before i had 1 GB and that worked as well. It is using about 600 MB ram.

I had once crashes because i had not enough free space on the hdd. So maybe check free space in folder in use.

Maybe you get useful information when you start kdenlive or cinelerra in terminal. Make sure that you get the terminal window visible when the computer is going to crash (as far as you can estimate it of course).

---

### Post by actionist on 2008-01-23
Thanks for replying. i changed my tmp folder to a partition with a lot of free space-- but still the computer crashes. It may have to do with some hardware issue, but I have no way of figuring it out.

---

### Post by eye208 on 2008-01-24
These types of crashes may be caused by bad RAM. Run memtest.

---

### Post by redmansk8 on 2008-01-25
Hello It could be bad memory or not enough of memory.

---

### Post by cotcot on 2008-01-25
2 GB is more than enough ram. I see my ram consumption not going above 600 MB when i use kdenlive even with 64bit.
You are not working on a FAT filesystem (where there is a single file limit of 4GB) ?

---

### Post by eye208 on 2008-01-25
> **cotcot said:**
> You are not working on a FAT filesystem (where there is a single file limit of 4GB) ?
Even if he did, this would never cause a total computer shutdown.

This is most likely a severe hardware or driver malfunction.

---

### Post by dad311 on 2008-01-28
Sounds like bad hardware to me.  Ive render 2 hour movies  in both Cinelerra and kdenlive and never had an issue.  Bad Ram or maybe not enough power supply.

---

