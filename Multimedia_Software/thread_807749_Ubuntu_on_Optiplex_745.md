---
title: "Ubuntu on Optiplex 745"
date: 2008-05-26
forum: Multimedia Software
---

### Post by olaeke on 2008-05-26
Hi,

I have a Dell Optiplex 745 with Intel Q965/963 Express Chipset Family graphics, using the DVI output and a Dell 2007WFP monitor.

Trying to intall ubuntu 8.04, but the screen goes black just after the splashscreen, then nothing!
I have search around and tried a couple of tips, like nosplash at boot and so on. But it still just stops loading and goes black after the progressbar is done.

7.10 installed just fine!

I can get 8.04 to install in graphics safe mode, but I want to be able to use higher resolutions.

What might have gone wrong? 

Please help!

Best regards

---

### Post by wilbbe01 on 2008-06-25
I'm experiencing the same deal.  I'll look into it a bit more now that I know someone else has the problem.  I don't have any 745s at home...only at work...so when my boss doesn't have anything for me to do I'll play with the 745 a bit.

---

### Post by wilbbe01 on 2008-07-07
I haven't been able to get a chance to test things out on a 745, and I doubt I'll have a chance anytime soon, but I do have an idea.  It appears based off of bug reports at I think a comment section for kernel bugs somewhere (I don't remember the site anymore) the problem we are experiencing is possibly fixed with the most recent kernel update.

I would try to boot off of the live cd, comment out the section about the graphics in the /etc/xorg.conf (make sure to mount your hd and modify that conf file), reboot to the hd, update everything (especially the kernel), then fix xorg.conf to match what it should for correct graphics and such.  I think that might fix things, but I can't be sure since I can't actually test it anytime in the near future.

Tell me if that helps.

---

### Post by rahmath on 2008-07-27
Dear All,

I am also stucked with this problem. Anyway to solve this... i didnt find any solution after googling.... not much pages about Hardy + Dell Optiplex 745.


Awaiting ur response...

---

### Post by wilbbe01 on 2008-08-14
try what I suggested on July 7th in my second paragraph, I think it looks promissing.

---

### Post by olaeke on 2008-08-19
Hi,

Im unsure if your solution works, I doubt it tough. I found a solution at the ubuntu bugreport forum. It involves downloading and compiling the drivers for the Intel graphics card. 

It seems as if the problem is with the current version of xorg and the 2.2.2 driver. (works with 2.2.3 driver)

---

