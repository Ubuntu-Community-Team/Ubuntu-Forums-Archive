---
title: "Nvidia Geforce 6200 Ubuntu 8.04 Help!!!"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Tommykry on 2008-04-28
Hello All, and master Ubuntu Gurus! I have spent over a week on this problem and have tried everything, I mean Everything! any help from you guys would be greatly appreciated!
 
The System is: Athlon 1.4, Asus a7v 133 MB, 1 Gig Ram, Agp Nvidia Geforce 6200 256 meg Video Card,

OS: DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

The Problem: Cant enable visual effects under appearance Preferences, When i select Extra i get this message: Desktop effects could not be enabled
I have Google searched this problem and combed these forums and have found plenty info about it and have tried every recommendation, every time i tried a fix it, was on a fresh install of ubuntu 8.04 so i could try and eliminate any possible variables.
I can provide any info needed, i have tried everything! now im at the point that i want to solve this just because how much time i have invested in this project.
I have tried every way to load the video driver The default Restricted driver Method, Envy, even manually (all on a different fresh install of ubuntu) All the methods work great! And im able to enable them in the proprietary hardware drivers box and they show they are enabled and in use
Also the nvidia X sever settings work too.
But when i go to select Extra (to enable 3d stuff) in the appearance Preferences box i get the message:Cant enable visual effects! I want to use the 3d Cube and all the cool eye candy.
As a note: i can get it all working perfect on gOS Rocket 2.0.0 ( which is based on (ubuntu 7.10 i think) on the same exact pc so i know the Pc and video card are ok. (video card i just purchased new)
Anyone that can help me figure this out i will be so thankful because i have spent so much time on this, now i just want to beat it and know how it was fixed. Im new to linux, i mainly use Xp and Mac osx, but stumbled upon Ubuntu on acccident now im obssessed! i love it and am going to get 2 pc's one for sister and one for mom with ubuntu installed.
Thank you so much for your time.
Tommy:guitar:

---

### Post by Tommykry on 2008-05-01
Hi, Everything works great on a fresh install of ubuntu 7.10 any ideas why its not working on 8.04?

Thank you for any help!

Tommy

---

### Post by Tommykry on 2008-05-01
anyone know anthing i can try?

Thanks
Tommy

---

### Post by warp99 on 2008-05-01
Open a terminal and issue the following command:
```
compiz --replace
```
and paste the contents of the output to this thread.

---

