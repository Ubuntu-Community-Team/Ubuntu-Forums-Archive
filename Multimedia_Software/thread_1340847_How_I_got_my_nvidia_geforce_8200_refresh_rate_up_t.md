---
title: "How I got my nvidia geforce 8200 refresh rate up to 75 hertz"
date: 2009-11-29
forum: Multimedia Software
---

### Post by princezuda on 2009-11-29
Hi,
I use a GEforce 8200 Nvidia graphics card. I was getting migraines from using it with ubuntu because it had a refresh rate of 69 hertz. I did a lot of googling and it looks like a lot of people are experiencing the same problem as I was. I am posting how I fixed the issue so others can benefit from it. 

Okay, I went into my nvidia x server settings which is located underneath system>administrator. I went to  nvidia x server display configuration. My monitor is a 23 inch samsung with the biggest display setting at 1680 by 1480. Thats a pretty big display setting and the highest refresh you can get is 69 hertz... which will give you a headache. I changed the screen resolution to 1280 by  1024, changed the refresh rate from auto to 75 hertz. This still didn't change the refresh rate that was set under gpu-0 (geforce-8200) and than the name of my monitor which is Samsung.  I clicked on the name of my monitor  and unchecked the box force full gpu scaling.  Once you uncheck the gpu scaling box select aspect ratio scaled and hit apply. Your refresh rate should now be at 75 hertz. hit the quit button in the nvidia x server to make sure your configuration settings are saved.

You can get a better refresh than 75 hertz but you have to settle for a smaller resolution. Anyways I hope this help :).  

I'm pretty new to ubuntu so if there is an easier way to solve this problem please share.

---

