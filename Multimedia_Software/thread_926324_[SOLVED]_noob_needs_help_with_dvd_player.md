---
title: "[SOLVED] noob needs help with dvd player"
date: 2008-09-21
forum: Multimedia Software
---

### Post by Jesten on 2008-09-21
im an absolute noob to linux in general. ive tried reading some post but its a little confusing. im really tired of windows and linux is so stable on my laptop. the main thing keeping me from a full switch is i cant watch dvd's. i do a lot of traveling (army) and i can do pics and reg movies in linux. ive tried vlc, it just wont load. i dont know whats wrong. totem says it cant read resource. kmplayer will start to play the dvd like the fbi screen and all but then just quits. is there a way to install a program like windows where u run a .exe and it auto installs? seems like everytime i want to install something i gotta install like 4 things. besides doing the add/remove program under applications. all the help will be awesome.

---

### Post by mike1234 on 2008-09-21
> **Jesten said:**
> im an absolute noob to linux in general. ive tried reading some post but its a little confusing. im really tired of windows and linux is so stable on my laptop. the main thing keeping me from a full switch is i cant watch dvd's. i do a lot of traveling (army) and i can do pics and reg movies in linux. ive tried vlc, it just wont load. i dont know whats wrong. totem says it cant read resource. kmplayer will start to play the dvd like the fbi screen and all but then just quits. is there a way to install a program like windows where u run a .exe and it auto installs? seems like everytime i want to install something i gotta install like 4 things. besides doing the add/remove program under applications. all the help will be awesome.

   Open your terminal and type in: sudo apt-get install ubuntu-restricted-extras 

Installing this package will pull in support for MP3 playback and decoding, support for various other audio formats (gstreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback. It's a quick and dirty way of getting it done. This usually takes care of most playback issues.

M.

---

### Post by Therion on 2008-09-21
Go to System/Administration/Synaptic Package Manager.

Search for, and install:  **ubuntu-restricted-extras**

See if that helps with you being able to play DVD's.

---

### Post by mike1234 on 2008-09-21
Also opening up synaptic package manager, you can browse through the descriptions of available or installed packages. It's a great way of learning about Ubuntu. 

M.

---

### Post by Jesten on 2008-09-21
ok i ran that in the term. it installed. still no play. does it hurt ubuntu if i have more that one movie player installed?

---

### Post by mike1234 on 2008-09-21
> **Jesten said:**
> ok i ran that in the term. it installed. still no play. does it hurt ubuntu if i have more that one movie player installed?

 No it doesn't hurt anything. Does Totem launch when you insert a DVD? Have you tried to play other DVD's? You might try installing this also. I think I downloaded from Debian long ago. VLC recommends installing them. Install with gdebi. The dev file isn't really necessary, but I install it anyways.

M.

---

### Post by Jesten on 2008-09-21
ok just tried 2 diff dvds same thing. totem launches when i insert a dvd. it still gives me the error could not load from resource

---

### Post by Jesten on 2008-09-21
well totem just told me it could play my dvd cause it has the right plug ins but it wont. it says to make sure my dvd is configured correctly

---

### Post by mike1234 on 2008-09-21
> **Jesten said:**
> well totem just told me it could play my dvd cause it has the right plug ins but it wont. it says to make sure my dvd is configured correctly

 Launch VLC, with a disc in your DVD, click on File, open disc. What happens? All the above suggestions should work. 
Did you install libdvdcss? Otherwise encrypted DVD's won't play.
M.

---

### Post by Jesten on 2008-09-21
i was just googling my problem and came across the libdvdcss i have not installed it i think

---

### Post by Jesten on 2008-09-21
that was it. it plays now. now if i can just get my laptop to run smoothly seems like it slows and gets choppy after running a little while

---

### Post by jay buddhika on 2008-09-22
Hi Folks,

Could you tell me why I get this error when I open VCDs with MPlayer

ioctl dif1: Input/output error

---

### Post by Jesten on 2008-09-22
dont know man, u might wanna search and/or make your on thread. i bet u will get a quicker answer

---

### Post by mcmilner on 2008-09-28
> **mike1234 said:**
> No it doesn't hurt anything. Does Totem launch when you insert a DVD? Have you tried to play other DVD's? You might try installing this also. I think I downloaded from Debian long ago. VLC recommends installing them. Install with gdebi. The dev file isn't really necessary, but I install it anyways.

M.

Thanks from me, too, Mike. Now my DVDs work.:)
Margot

---

