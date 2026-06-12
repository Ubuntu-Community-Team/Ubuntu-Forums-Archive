---
title: "[SOLVED] Screens and Graphics"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by PhonicsMonkey on 2007-12-11
I have a problem and am the epitome of newb. I am a lowly vista user how recently learned the error of his ways and am in need of some aid. I was trying to hook my laptop up to my TV using a VGA to RGB cable. I am currently running Ubuntu. I went to screens and graphics then proceeded to select a second screen which would mirror the one on my laptop. It first of all didn't work. I tried restarting but that didn't work either. When I went back to click screens and graphics it tries to open, asks for my password, then promptly doesn't work. What is going on. Please, list any help in the most basic terms. I still need to get used to the terminal. THanks.

---

### Post by overdrank on 2007-12-13
> **PhonicsMonkey said:**
> I have a problem and am the epitome of newb. I am a lowly vista user how recently learned the error of his ways and am in need of some aid. I was trying to hook my laptop up to my TV using a VGA to RGB cable. I am currently running Ubuntu. I went to screens and graphics then proceeded to select a second screen which would mirror the one on my laptop. It first of all didn't work. I tried restarting but that didn't work either. When I went back to click screens and graphics it tries to open, asks for my password, then promptly doesn't work. What is going on. Please, list any help in the most basic terms. I still need to get used to the terminal. THanks.

HI and if you have a nvidia graphics card have you tried the command ```
gksudo nvidia-settings
``` by using the alt, F2 keys. There you can setup your tv. Good luck!

---

### Post by PhonicsMonkey on 2007-12-13
I still don't know what to do. The glitch I was getting stopped after I reinstalled Ubuntu 7.10. I have everything setup the way I like it. What I want to try now is playing video's from my laptop onto my tv with a VGA/RGB cable. I tried gksudo nvidia-settings but don't know what to do from there.

---

### Post by PhonicsMonkey on 2007-12-17
Ok I just got things working by placing a launcher on the desktop that will let me open screens and graphics. Thanks anyway. The trick when using nvidia and gnome is not to use the screens and graphics from the administrator but to use the terminal instead otherwise you get this glitch. BTW the reason for using a launcher is for ease of access instead of typing the command everytime I switch from my laptop to a tv (I have lots of movies on my laptop).

---

### Post by zhuzi on 2007-12-17
Hi, may I ask how did you set up the launcher for Screens and Graphics? What is the command, please?

---

