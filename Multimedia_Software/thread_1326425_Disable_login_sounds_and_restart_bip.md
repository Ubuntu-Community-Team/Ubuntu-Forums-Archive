---
title: "Disable login sounds and restart bip"
date: 2009-11-14
forum: Multimedia Software
---

### Post by Hesediel on 2009-11-14
I would like to disable all sounds on my login, at user selection and login on system.

I disabled the gnome login sound on startup apllication, but the sound on user selection remains.

Also..when i shutdown or restart my laptot a higher bip sounds, i tried to insert blacklist pcspkr on the blacklist file but it is already there! 

How can i disable all of that sounds? 

Thx

---

### Post by Hesediel on 2009-11-15
up...

the only way to disable the drums at start for me was to run  a sudo apt-get remove ubuntu-sounds

Also the beep on shutdown/restart still remains, 
my pc is a laptop Acer AS6930, the beep isn't from pcspkr i think, if i put headphones the beep goes in them. The pc speaker is blacklisted and i tried also with  sudo modprob -r pcspkr whitout working, so i think it isn't a question of pcspkr


I think there is a bad and not understanding regression in audio control and option, in KK

---

