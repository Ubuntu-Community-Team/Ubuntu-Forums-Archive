---
title: "Another Linux Convert"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by robertsaron on 2007-05-01
I know this is the Ubuntu forums, this makes for a good story. I spent a month trying to get sound working on my room mates computer in Ubuntu. 

Finally a friend recommended  I try Mandriva. Last night as I was installing it, it came up and asked if the fire wall should be installed, I asked her do you want it. She asked me do I need it? I was like I dont know, do you want it? She said no, this isnt windows.

She does prefer ubuntu but for the sake of sound, she had to switch.

Mandriva did pick up the sound card instantly, and it worked. I spent the rest of night laughing my freking head off as  I finished setting up her computer. I myself prefer Ubuntu over other distros.

---

### Post by jfinkels on 2007-05-01
> **robertsaron said:**
> I know this is the Ubuntu forums, this makes for a good story. I spent a month trying to get sound working on my room mates computer in Ubuntu. 

Finally a friend recommended  I try Mandriva. Last night as I was installing it, it came up and asked if the fire wall should be installed, I asked her do you want it. She asked me do I need it? I was like I dont know, do you want it? She said no, this isnt windows.

She does prefer ubuntu but for the sake of sound, she had to switch.

Mandriva did pick up the sound card instantly, and it worked. I spent the rest of night laughing my freking head off as  I finished setting up her computer. I myself prefer Ubuntu over other distros.

I don't really understand what's funny about this situation, but if your friend needs help, tell her to post on the forums! We can fix it! No reason to try and fix it all by yourself when there's a perfectly good global community right behind you :D

---

### Post by robertsaron on 2007-05-01
I spent hours on the forums, and looking through volumes of information. i printed out 35 pages of how tos to get the sound working. I posted all kinds of things on myspace linux groups, and talking to linux people at work. 

I didnt make switch her distros just because. I did it because after a month,  I was tired of installing, I installed several different versions of Ubuntu, and reinstalled about 12-15 times at least. I even switched out 3 different sounds cards, so yeah, its not like I didnt try.

Besides you missed the whole point of the story. She does prefer Ubuntu, but got tired of her computer being broken. How would you like to be without a computer for a whole month? 

She no longer wants to use Windows.

---

### Post by robertsaron on 2007-05-04
ok So I got sound to work in Feisty. I downloaded 32bit Kubuntu, installed it hoping it would auto detect the trident wave 4dx. It didnt. so I then went into the packet manager and removed everything related to alsa, so I could then later install the OSS drivers from opensound. 

Anything and everything related to KDE was removed. No more GUI. I then used the sudo aptitude install kubuntu-desktop command. Once KDE was installed, I then rebooted the machine. Well what you know the sound worked. No alsa/oss drivers were installed. Except for the linux base sound. 

What I want to know is Why Kubuntu did not pick it up at time of install? I know the alsa drivers are default at time of install. 

I dont know enuf about linux to modify my xorg file or soundconf, I barely feel comfortable modding my fstab.

---

