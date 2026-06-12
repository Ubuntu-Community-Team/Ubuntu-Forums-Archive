---
title: "Sound problem"
date: 2006-09-09
forum: Multimedia &amp; Video
---

### Post by Anonii on 2006-09-09
Greetings,

*I suck in hardware, so I'll try to explain the problem the best I can, if you have more questions feel free to ask them <:* 

I have noticed a weird sound problem. In every reboot (I think) the sound switches from the sound card to to the internal sound card. I have an SB Audigy LS and the internal Intel sound card. So in every reboot I have to change the cables from the sound card sockets (thats how they are called? :/) to the internal sound sockets, which are on a different position in the tower...
Any ideas why? 

I'm using GNOME, btw. The sound was working from scratch.

---

### Post by Anonii on 2006-12-20
**Bump**, its getting really annoying.

---

### Post by lister171254 on 2006-12-20
Maybe the first thing you could do is to disable the internal card in the BIOS before you boot.

Leo

---

### Post by budgie9 on 2006-12-20
> **lister171254 said:**
> Maybe the first thing you could do is to disable the internal card in the BIOS before you boot.

Leo

There is almost certainly a jumper that controls the internal sound card. Check the m/board manual, and it  should tell you where it is located. Whne set off  it will be completly disabled even if in the BIOS it is set on. 
It will also cause a  IRQ conflict within your system so it would be wise to disable it all together.

---

### Post by deadgobby on 2006-12-21
I agree that you need to disable the on board sound card in you BIOS. . You will need to install ALSA as well. You can install Gnome ALSA too. 
Gobby

---

### Post by Anonii on 2006-12-21
I cant find out how to do that :/
I checked out every BIOS section and I still coudnt find something related to the sound card? Any more detailed ideas?

Thanks, btw!

---

### Post by lister171254 on 2006-12-22
Most BIOS menus have an section for 'Integrated Peripherals'. Yor onboard sound would be there. Also have a quick look in the manual for you motherboard or the manufacture's website. 

What's your motherboard?

Leo

---

### Post by Anonii on 2006-12-23
I think I found it, and fixed it. Well, I dont have the same problem after 2 reboots. We will see....

Thank you very much!

---

