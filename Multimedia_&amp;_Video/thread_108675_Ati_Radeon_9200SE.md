---
title: "Ati Radeon 9200SE"
date: 2005-12-26
forum: Multimedia &amp; Video
---

### Post by projectgonewrong on 2005-12-26
Okay I put it in my computer I started it up and it didnt work I couldn't even get to the desktop it just said some stuff about X and graphics. tell me step by step how to get it to work. I took out the card for now so i could start it up. please

---

### Post by andril on 2005-12-26
I actually just replaced this card but If I am correct you are ready to typ e the following afetr you log-in:

"sudo dpkg-reconfigure xserver-xorg" and hit enter

Follow the prompts 

select "ati" for the driver and follow the rest to completion and reboot, you can also do a search for ATI in the forums - that's what helped me. But I went out and got an Nvidia card so I could use Automatix

---

### Post by projectgonewrong on 2005-12-27
That didnt work.

---

### Post by ed_agamemnon on 2005-12-27
I have the exact same card and it works a treat for me. On fresh install it comes with the Mesa3D drivers which i can easily replace following HOWTOs here with the ATI flgx thingies...

Aaaanyway, it might be something other than your card.

(PIII 3.0ghz, 512DDR, ATI Radeon 9200SE)

---

