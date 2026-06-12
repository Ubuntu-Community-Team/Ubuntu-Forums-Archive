---
title: "Planning question"
date: 2008-09-29
forum: Mythbuntu
---

### Post by deadpan on 2008-09-29
i'v been reading the forums but i cant really find the right answer but heres what i'm trying to get done.

i want to have mythbuntu setup for 4 tv's all standard tv no HD yet but i want to future proof it so its not to expensive to upgrade it.

right now i have 4 dish box's one at each tv. now its my understanding that i need 1 tv card for each tv? i want the ability to watch and record on each tv separately. so thats 8 cards? i was thinking maybe i can getaway with 5, 4 to watch tv and one setup to record as long as two shows dont have a scheduling conflict. 

another issue is changing the channels, i can put all the dish boxes in my liitle server closet and connect some sort of ir blaster to change the dish box but wouldnt having 4 of the same remotes interfere with each other?

on the issues of front ends, right now i have a hacked xbox running XBMC, i would need one xbox per tv right? also its rather loud and gets hot anyone know of any decent alternatives?

anyone running 3-4 tv's with one mythbuntu backend mind sharing how they have everything setup? thanks for reading.

---

### Post by tgm4883 on 2008-09-29
Using directv here, I have 3 directv boxes connected to my backend server.  I also have 3 remote frontends and a frontend on my backend server.

The directv boxes are controlled from the backend via usb/serial cables.  You need 1 tuner for every show that you want to record at the same time (live tv counts as a recording).  So in my setup, I can record 3 shows at a time, record 2 shows and have 1 for live tv, any combination of 3.  These boxes are connected to my system via PVR-500, and PVR-150.  Keep in mind you will also need one satellite box for every channel you want to record at a time.  So if you want 8 channels recorded at a time, you will need 8 tuners and 8 satellite boxes.  Most likely you won't want 8 though.  4-5 should do it.  Once you have some schedules setup to record the shows you like, and perhaps some extra shows to watch in between.

You would need 1 xbox per TV (frontend).  Keep in mind that the original xbox's wont do HD, and the new xbox's (360) won't be a mythtv frontend.  You can however, get some small computers to use as frontends.

When you are irblasting, the remotes are not going to interfere with each other because each tuner controls the box/irblaster independently of the other tuners.  That and the distance is pretty minimal between the blaster and the box, if you have issues I suggest a slight bit of electrical tape on the front of it.  

Heat will be an issue, space or fans to deal with this.

---

