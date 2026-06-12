---
title: "s-video out not working (laptop)"
date: 2008-10-14
forum: Multimedia Software
---

### Post by Manati74 on 2008-10-14
Hi there. I own a Fujitsu Siemens Laptop (Amilo L1310G) which has given me lots of trouble after I decided to use Linux. And it was only yesterday that I discovered that my s-video jack is apparently not working either. In other words, I tried to connect my laptop with my TV via a s-video to s-video cable and nothing happened. Is the recognition of s-video a known problem under linux. [Btw: I can also not use a second (external) screen by plugging such a screen into the scree jack of my laptop. May be these problems are related?] What can I do? I am not an expert, so please let me know if you need further information (and how I can get it).

Cheers,
Tobias

---

### Post by overdrank on 2008-10-14
> **Manati74 said:**
> Hi there. I own a Fujitsu Siemens Laptop (Amilo L1310G) which has given me lots of trouble after I decided to use Linux. And it was only yesterday that I discovered that my s-video jack is apparently not working either. In other words, I tried to connect my laptop with my TV via a s-video to s-video cable and nothing happened. Is the recognition of s-video a known problem under linux. [Btw: I can also not use a second (external) screen by plugging such a screen into the scree jack of my laptop. May be these problems are related?] What can I do? I am not an expert, so please let me know if you need further information (and how I can get it).

Cheers,
Tobias

Hi and welcome, if you use the command lspci in the terminal located under applications, accessories. Then you can identify your graphics by looking for VGA
You may also try the command using the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` And adjust your extra screen there

---

### Post by Manati74 on 2008-10-14
> **overdrank said:**
> Hi and welcome, if you use the command lspci in the terminal located under applications, accessories. Then you can identify your graphics by looking for VGA
You may also try the command using the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` And adjust your extra screen there

Thanks for that. The following line is the only one having anything to do with VGA:

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

What does this mean now for my problem?

---

### Post by Manati74 on 2008-10-16
Ok, slowly but surely I am getting somewhere. I used the ATI Catalyst Control Center and when I booted with the laptop connected to the TV, the Display Manager identified two displays: 1 digital dispaly (ie my laptop screen) and a TV. So far so good. The problem is, that nothing appears on the TV screen... it stays, well, blue. What must I do now? I am in South Africa but the laptop was manufactured in Germany. May be it has something to do with PAL Secam etc??

---

