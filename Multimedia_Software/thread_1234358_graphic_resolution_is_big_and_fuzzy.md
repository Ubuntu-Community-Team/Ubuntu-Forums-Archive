---
title: "graphic resolution is big and fuzzy"
date: 2009-08-07
forum: Multimedia Software
---

### Post by gjohnson10 on 2009-08-07
i just loaded ubuntu today. love it except for the fact that i cannot change the resolution (800x600 is as high as I can go). with xp i had 1200x800?? or something like that, but my graphics were much clearer. also, web pages span across the screen. i have read some of the posts in the forum on this subject, but i'm still unsure how to fix. i have a hp1703 monitor with nvidia graphics card and i have installed the driver in the ubuntu section. help please. thanks!

---

### Post by overdrank on 2009-08-07
> **gjohnson10 said:**
> i just loaded ubuntu today. love it except for the fact that i cannot change the resolution (800x600 is as high as I can go). with xp i had 1200x800?? or something like that, but my graphics were much clearer. also, web pages span across the screen. i have read some of the posts in the forum on this subject, but i'm still unsure how to fix. i have a hp1703 monitor with nvidia graphics card and i have installed the driver in the ubuntu section. help please. thanks!

Hi and welcome, you may look under system, Administration, Hardware drivers to see if any drivers are available for your graphics card.
If none are shown then you can use this command in the terminal ```
lspci | grep VGA
``` to identify your hardware. The terminal is located under applications, accessories. :)

---

