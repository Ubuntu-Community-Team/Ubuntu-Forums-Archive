---
title: "CD Ripping Software"
date: 2008-12-17
forum: Multimedia Software
---

### Post by Aizawa on 2008-12-17
I want to be able to rip my CDs, but I can't find a program to do that. I mean, sure, I find these obscure programs, but the quality of programs I find through googling are usually worthless.

Sadly, as some of you may know, Songbird doesn't have CD ripping. So.. Uh.. What's a good program for doing so? I want it to be quick, of course.

Thanks in advance!

(I tried searching the forums)

---

### Post by logos34 on 2008-12-17
take a look here:
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

I love ABCDE --fast (but customizing abcde,conf can be difficult to get right).  command-line only

rubyripper is neat too and produces secure rips (the second most accurate after Exact Audio) but it's slower

grip is also pretty nice.  used to use it all the time.  again, getting the executable line correct can be a hassle

you can also use k3b.  You should probably be using that as your burning app (far and away the best), so maybe learn up on it ripping capability

---

### Post by binbash on 2008-12-17
you can use grip

---

### Post by andrew.46 on 2008-12-18
Hi logos34,

> **logos34 said:**
> I love ABCDE --fast (but customizing abcde,conf can be difficult to get right)

Well I tried to make life a little easier a while ago by publishing some sample $HOME/.abcde.conf files here:

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

These work well on my own system and according to the server logs they have been fairly popular.

Andrew

---

### Post by logos34 on 2008-12-18
> **andrew.46 said:**
> Hi logos34,



Well I tried to make life a little easier a while ago by publishing some sample $HOME/.abcde.conf files here:

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

These work well on my own system and according to the server logs they have been fairly popular.

Andrew

Yes, I'm aware of your thread, I consulted it when I customized mine. (In fact I made a tips guide of my own--no great shakes, got bored with it and never posted it). As much as I like it, it's my experience most people prefer a gui, and dislike configuring .txt files by hand.  So I hesitate to recommend it

---

### Post by Eddie Wilson on 2008-12-18
What format will you be ripping to?

---

### Post by NWAdawg on 2008-12-18
> logos34 wrote:
rubyripper is neat too and produces secure rips

I've used rubyripper for some time now. Here the thread for installation. 

[http://ubuntuforums.org/showthread.php?t=799621&highlight=rubyripper](http://ubuntuforums.org/showthread.php?t=799621&highlight=rubyripper)

---

### Post by Eddie Wilson on 2008-12-18
Asunder is a good program and simple also.

[http://www.getdeb.net/app/Asunder](http://www.getdeb.net/app/Asunder)

---

### Post by Piraja on 2008-12-28
My vote goes for abcde. I don't even think it really needs configuration: I'm used to just typing "abcde -o flac" or "abcde -o mp3,ogg" where "-o" stands for "output"; you can even encode to several different output types. For this basic task, I did not have to edit any configuration file at all, just installed abcde on my new laptop and started ripping.

I have one question, though: When CDDB does not contain an entry for the CD and I manually edit the information in ABCDE/VIM, how can I submit it to CDDB the easy way?

---

### Post by logos34 on 2008-12-28
> **Piraja said:**
> My vote goes for abcde. I don't even think it really needs configuration: I'm used to just typing "abcde -o flac" or "abcde -o mp3,ogg" ...for this basic task, I did not have to edit any configuration file at all, just installed abcde on my new laptop and started ripping.

true, if you're not fussy and are content with the default bitrate of 128k CBR or flac -5...But if you want to increase/adjust that it's not always immediately apparent to the noob exactly how to do that.  that's my only reservation about recommending abcde

---

