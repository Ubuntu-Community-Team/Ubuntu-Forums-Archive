---
title: "Static while playing music"
date: 2012-11-23
forum: Multimedia Software
---

### Post by Peterfc on 2012-11-23
Today i removed the USB phone i had for Skype to see if the speakers woud work with an external Mike. After completing a new update and rebooting i tried Skype again but i had no sound. 

I have checked with the USB phone no luck.
I used a spare pair of USB speakers no luck.
I have checked all setting ad nothing seems at fault.
I have disabled the onboard sound and fited a Soundblaster sound card on one of the sockets there is faint sound but nothing from the correct socket. 
I have tried to go back to the onboard sound but the only sound i get is full of what sounds like static.  

Thanks for reading.

Peter

System: home made machine  
Ubuntu 12.04 fully up to date
Intel Pentium Dual cpu e2160@1.80ghz X 2
Memory 1gb
500GB har drive

---

### Post by AstroLlama on 2012-11-24
run ```
alsamixer
``` in a terminal and check to see if there are any sound devices muted. you can mute/unmute them with the "M" key. 

another option is to go into the skype settings and making sure the proper sound devices have been chosen.

---

