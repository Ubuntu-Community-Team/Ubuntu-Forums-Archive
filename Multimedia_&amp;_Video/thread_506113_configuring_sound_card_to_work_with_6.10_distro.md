---
title: "configuring sound card to work with 6.10 distro"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by NUBI2007 on 2007-07-21
I recently converted from windows XP to Linux Ubuntu 6.10 and I'm very new to the linux language. I've got a stock dell 2400 desktop that has a Sound Blaster Live Sound Card installed. After installation I noticed that sounds from GAIM were not working. I loaded a CD to check if I could get sound from that, but still nothing. I checked the device manager to see if the correct program was being applied and it lists Sound Juicer as the default. but that program gave me no sound either. 

Creative provides no back support for this card, as far as drivers, and I've run into a wall. 

Can some one please help solve this problem. I apologize, but a detailed explanation would be helpful. 

thanks

NUBI

---

### Post by dragonwings on 2007-07-21
to get list of sound cards
sudo asound list

sudo asoundconf set-default-card (your sound card name goes here)

eg: for mine i put 
sudo asound set-default-card Audigy2

---

