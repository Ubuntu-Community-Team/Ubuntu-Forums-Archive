---
title: "mangler/error probing smdb/rythmbox questions"
date: 2010-06-13
forum: Multimedia Software
---

### Post by Metrop021 on 2010-06-13
allright i've got 3 questions.

1: not sure how many people use mangler but i'll pretty much copy and paste what i put on their forums.

> I'm trying to recreate this problem consistently but at the moment it seems to be completely random. That can't be though, there has to be method to this madness&#8230;

 

Sometimes someones "talk duration" (the time they push their mic down to the time they let go) will just not come through my audio, however the received bytes counter at the top will increase as if everything was normal. The thing is this only happens sometimes&#8230; other times everything will be normal and i'll hear everything. I'd say the problem has about a 20 percent occurrence rate.

 

Anyone have any idea? this is pretty strange and it bugs me since the problem doesn't occur in Ventrilo running through wine (but ventrilo in wine has it's own problem, like i need to have it selected for my push to talk to work and what not).

This happens using any of the sound systems...


This is with mangler1.2beta

2: I think this is a reported bug but just in case someone knows a workaround. When i boot i get flashed the error "[...Nvidia n....]Error probing smb1 (flashes too quick to read)". I'm pretty much 100% sure this is a problem with the Nvidia 195 driver, since I don't get this problem when i'm not using the driver. It doesnt seem to do anything other than flash that message, and to make the splash at bootup and shutdown be a bad resolution for my monitor. It just looks ugly and if there's some workaround or some way to set the resolution of the splash ahead of time (i never use a different monitor) then that'd be nice.

3: Is there a way that i can specify which output I want rythmbox to play music to? In audacious I was able to choose to send my music through my speakers as opposed to my headset. This is nice cause i'd rather have voice communications through my headset and music through my nice speakers. I'm having trouble finding the same option in rythmbox.

Thanks for any help!

---

### Post by Metrop021 on 2010-06-13
I downgraded my mangler version to 1.1 stable and i'll see if i still get the same problem (will test that tomorrow)

---

### Post by Metrop021 on 2010-06-13
looks like using pulseaudio on 1.1 my problem is fixed... might just be luck though

---

### Post by Metrop021 on 2010-06-14
yeah i'm almost positive the mangler problem is solved now :)

---

