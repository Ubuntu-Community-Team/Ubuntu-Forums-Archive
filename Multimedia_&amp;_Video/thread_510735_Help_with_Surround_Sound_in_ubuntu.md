---
title: "Help with Surround Sound in ubuntu"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by alexv305 on 2007-07-26
I cant get full surround sound in my ubuntu setup. I use feisty and for some reason I cant get the center channel to work at all. I got the rear to work by duplicating the front and setting it to shard and 4ch and it works like a charm but the center channel wont work :(     I dont know how else to try to get it to work...

Any ideas anyone?

---

### Post by hedgefighter on 2007-07-27
The other channels may be muted or be turned down. Try running "alsamixer" in a terminal. It lets you adjust the volume controls for all your channels. "M" toggles the mute. Up and Down control volume. And left and right move through the channels. There may be more channels that you can't see. Just keep moving right to see them. Usually the channels are labeled but sometimes they have names aren't helpful so it may take some trial and error. Good luck.

---

### Post by alexv305 on 2007-07-27
No, I tried this and enabled center channel. I still cannot get sound from the center channel and the volume is all the way up and not muted...

??

---

### Post by deadgobby on 2007-07-27
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

Gobby

---

### Post by lightstream on 2007-08-03
> **alexv305 said:**
> No, I tried this and enabled center channel. I still cannot get sound from the center channel and the volume is all the way up and not muted...

??

Have you checked the volume settings? Double click the speaker icon in the wotsit panel, go to Edit > Preferences, then enable Surround (at the top) and Channel Mode (near the bottom). Make sure your Surround level is turned up on the sound mixer. Then click Options tab and set Channel Mode to 6ch. 

Using this plus gobby and hedgefighter's info from this thread i got my 6 ch speakers working perfect. No need to duplicate front speakers with rear either  =D>

---

