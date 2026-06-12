---
title: "missing a step, maybe more?"
date: 2011-04-20
forum: Multimedia Software
---

### Post by popsicle pete on 2011-04-20
Hey! long time windows user (but NEVER again), very short time Ubuntu user/fan. 
First of all, lemme just proclaim Linux my new cyber religion and say how much it is akin to a breath of fresh air after all these years of being an unknowing slave to mAcrosoft. It's actually more like an oxygen tank was  strapped to my back!   Phew...got that off my chest..if you're still with me thanks for listening. :D

ok, here's my plight, as minor as it may seem..the sticky thread in the 'absolute beginner' forum told me there are no stupid questions..
i'm trying to download a game or two off playdeb.net...
so far i've been able to google my way around every hurdle, but for some reason i feel like i'm missing something obvious on this one..like perhaps a simple apt get command, maybe? 

i'm hoping someone can help. i'm using version 10.10 and i've attached a screenshot of the error message from the software center i get when i try and download directly off of the website.

thanks a million in advance for_ any_ feedback and hopefully this post wasn't too long, it was my first. 
but i bet you an orange popsicle i'll get better at this over time =p

---

### Post by nothingspecial on 2011-04-21
Hi,

Don't open it with the software centre. Save the deb. then right click it and choose to open it with gdebi

 

or use your terminal

```
sudo dpkg -i game.deb
```

---

