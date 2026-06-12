---
title: "Another Warcraft Thread"
date: 2009-01-31
forum: Multimedia Software
---

### Post by coachabower on 2009-01-31
Hi guys, first time posting to the forum, usually I'm able to find a solution in an existing forum but I've been searching for quite a while and frankly my head hurts.  So I'll just ask and hopefully someone can help me.

I was recently instructed to install Linux on my machine to do some c++ programming for a class.  I downloaded Ubuntu Ultimate Edition for gamers, I think its just called that because it has several included games.  Anyway, I really like the OS and would like to fully drop windows and just use linux(new laptop with vista...hate vista).  The only thing holding me back is the ability to play wow.

My first attempt was to use wine.  I enabled the virtual desktop, changed some files in the wow directory(which was on the windows partition btw), and ran the program.  It worked, just poorly, and some of the graphics weren't rendering properly.  So I moved on to attempt 2, I got a version of CrossOver, prof. ed. i think.  I installed wow directly to the linux partition this time and all seemed to be going well.
Certainly a mindless interface for the install, crossover made that part easy.  I took a look at the wtf file I modified the first time and the settings match the new install.  

For some reason I am now getting the "Unable to start the 3d accelerator" error message.  It's driving me nuts, the posts I've read say it's probably the graphics card...but it runs in windows and it ran when I used wine, just not as well as I wanted it to.  I hear Cedega is a horrible idea and that wine is the most compatible, but CrossOver is supposed to be mostly wine source with improvement, so I figured it should perform better.  If you have any suggestions for the best way to run wow I would appreciate it, even if I have to go back to wine as long as it runs better.  

P.S., it runs kind of choppy in vista, which is another reason I want to make the switch, I've read that people are experiencing better performance in linux than windows, so I want to get in on that.


So, my specs are for a sony vgn-ns240e laptop.
Intel Core2 Duo 2GHz, 800MB bus, 2MB cache
Intel graphics media accelerator 4500MHD
up to 1340MB available shared video mem
3GB Ram,PC2 6400 DDR2

---

### Post by binbash on 2009-01-31
start it with -opengl . wine adasd.exe -opengl

---

