---
title: "About to buy a 5.1 system and sound card, please advise!"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by herbster on 2007-03-17
I am about to buy a 5.1 speaker system, most likely a Logitech. I am pretty much a newb when it comes to audio technicalities on the PC, so I was wondering:

a) I need a new sound card right? (I only have my onboard sound, don't know if it's "good" enough or however it's termed lol), and
b) If so, what is/are the most compatible sound card(s) with linux/Ubuntu or does it matter? (I am planning on getting a Creative Audigy series, can anyone testify or recommend specifically??)

Please, any advice is appreciated, I want to get this set up real soon :)

---

### Post by desheikh on 2007-03-17
Hi,

Weather your onboard sound card is "good enough" as you say it depends on you. Does it support 5.1 speakers? Do you need to have 5.1 speaker or will 2.1 do just as good? Do need all the extra features that come with a separate sound card. Personally I have 2.1 connected to my onboard card and I cant tell the difference between that and my friends soundblaster audigy2 with 5.1  speakers.

If your going for a creative card, you shouldnt have a problem running it with ubuntu. Just be sure to disable your onboard card in your system bios.

---

### Post by tranquanghvac on 2007-03-17
wait buddy, i have audigy value  creative sound card and there is no sound in Ubuntu. Still researching to make it sings.

---

### Post by DoorGunner on 2007-03-17
I have an audigy and it works great

once you get your sound card dont forget to 
sudo gedit ~/.asoundrc 

and add the following lines

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}

---

