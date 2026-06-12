---
title: "Frustration from sound and breezy"
date: 2005-12-03
forum: Multimedia &amp; Video
---

### Post by jlark on 2005-12-03
Yellow everyone,
   My first post here but I'v been running in and out of these forums since I insatlled ubuntu:) A good wasy to socialise i guess. Anyway I got on to a rough start with hoary and decided to pass on to breezy. At first my gnome broke and thanks to previouse posts I got that all that under control but now a more difficult promlem has risen. I have no Sound In breezy . Hoary was working just fine sound wise I only hat to kill esd for mplayer to work but on breezy nothing.

The previose posts weren"t helpfull either:(
 thus I created my own thread :)

My sound car is SB live and alas driver is on and running with all the volumes open.. 
I really would appreciate you help...Thanks

---

### Post by mistergq on 2005-12-03
this is stupid, but go into a terminal window, type alsamixer and scroll over to External Amplifer and press M to mute it.  I recommend having a CD playing before doing this and see if the sound comes on.

Good luck.

---

### Post by kaaskop on 2005-12-03
I've got the same problem and was looking for weeks in all sorts of newsgroups.
Turns out that I had to disable my onboard sound card in the BIOS.
And then there was music!

---

### Post by jlark on 2005-12-04
Thanks for the reply everyone But alsa mxer doens't seem to work I stll I am deaf.
I don't have an onboard sound card so I don't tink thats the problem either. 
Woever when Linux is booting up when is activating something called HOTPLUG 

right before the alsa driver I hear crackles from the speaker..

Any Ideas??

---

### Post by jlark on 2005-12-04
Hello everyone... Incredbily I fixed my problem...

While I was playing with the volume monitor and tryinf different configurations I decided to check on that external amplifier one last time I unchecked it after I entered in volume contol>file>select devixes and selected sigmatel (OSS) dirver 
Before I had amarak playing tunes in the back and suddenly my ears where filled with the sweet sound of ledzepplin..

I have to tell ya it's like I was hearing it for the first time :) tears to my eyes...

I  hope this works with everyone else...cheers.

---

