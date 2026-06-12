---
title: "Direct TV"
date: 2008-04-30
forum: Mythbuntu
---

### Post by wolfster101 on 2008-04-30
Not really sure how this should all be set up but I will explain what I have and hopefully someone can point me in the right direction.

DirectTV satellite connect to the satellite box.  Box connects to PVR-350 tuner 1 on backend server. Laptop is frontend with s-video out to TV.  

How do I change or see more channels other then what the DirectTV box is currently on?

---

### Post by majoridiot on 2008-04-30
> **wolfster101 said:**
> Not really sure how this should all be set up but I will explain what I have and hopefully someone can point me in the right direction.

DirectTV satellite connect to the satellite box.  Box connects to PVR-350 tuner 1 on backend server. Laptop is frontend with s-video out to TV.  

How do I change or see more channels other then what the DirectTV box is currently on?

you will need a channel-changer to tune the sat box.  depending onthe model, this is possible by a
serial or usb connection or an ir blaster.

for a the best chance of possible solutions, please post the model of your directv receiver.

---

### Post by wolfster101 on 2008-04-30
So I can only watch what the satellite box is set to like I didn't even have Mythbuntu?

The hauppage PVR-350 has 2 tuners in it, am I not able to watch one channel and record another or record 2 different channels at the same time?

The satellite box is a rca drd440re

---

### Post by majoridiot on 2008-04-30
> **wolfster101 said:**
> So I can only watch what the satellite box is set to like I didn't even have Mythbuntu?

The hauppage PVR-350 has 2 tuners in it, am I not able to watch one channel and record another or record 2 different channels at the same time?

The satellite box is a rca drd440re

you can watch one channel and record another, but *only* if each 350 tuner has a separate signal source.
the only way you would be able to watch one channel and record another is if you had 2 directv receivers- 
with each feeding one pvr-350 tuner... or if you connect another signal source like cable box, or antenna, 
etc. to your second tuner input.

think of the 350 as two tv's... you can't connect 2 tvs to one directv receiver and watch 2 different
channels at the same time, can you? ;)

---

### Post by wolfster101 on 2008-04-30
Oh wow.  Maybe I have gotten into something I do not need.  I was under the impression I could set up a Mythbuntu box and therefore eliminate the DirectTV DVR box for $100 plus $6 a month.

This would allow me to record one channel and watch another with a single box, or record 2 channels while sleeping.  Of course I am sure you are very familiar with what I am describing but I didnt think I would need two boxes to get two channels.  Or maybe I am mistaken there too.  :-P

Perhaps the only purpose for a Mythbuntu setup is for those on the old antenna TV's and to burn your pre-recorded shows to DVD.  I am assuming if I wanted to record something in the future, say when I am sleeping, I have to make sure the satellite box is already on the channel I need.

Thanks for your input!

---

### Post by tgm4883 on 2008-04-30
> **wolfster101 said:**
> Oh wow.  Maybe I have gotten into something I do not need.  I was under the impression I could set up a Mythbuntu box and therefore eliminate the DirectTV DVR box for $100 plus $6 a month.

This would allow me to record one channel and watch another with a single box, or record 2 channels while sleeping.  Of course I am sure you are very familiar with what I am describing but I didnt think I would need two boxes to get two channels.  Or maybe I am mistaken there too.  :-P

Perhaps the only purpose for a Mythbuntu setup is for those on the old antenna TV's and to burn your pre-recorded shows to DVD.  I am assuming if I wanted to record something in the future, say when I am sleeping, I have to make sure the satellite box is already on the channel I need.

Thanks for your input!

Lets go ahead and break down your whole problem.

First off you have satellite.  That in itself should make you want to hurl.  But perhaps it is your only option (unfortunatly it is my only option, which means that when you title your thread "Direct TV" I have the overwelming urge to click on the link and help fix your issue).  So in order to make that work, you have to play by their (being DirecTV) rules.  This means that for every show you want to record, you need a DirecTV tuner (IE a box, capable of receiving a DirecTV signal, decoding said signal, and then displaying it on a TV).  I know that part is difficult to understand because DirecTV has a box that can record 2 shows at once, so why can't you pass both shows on to the MythTV box.  Simply because you can't watch 2 tv's on 1 box at the same time (none that I have seen anyway).  If you do happen to have a box that will _display_ 2 seperate DirecTV channels then I stand corrected and I would really appreciate a link to this.

Second.  You have a PVR-350.  A PVR-350 has a single (1) tuner, not 2.  So in order for you to watch a show and record another, you will either need to get a PVR-500, or a PVR-150 (you could get another PVR-350 I suppose, but what would be the point in that?)

Third.  You seem to have no concept for the benefits of a MythTV system.  Last I checked (and it wasn't that long ago) DirecTV does not have (nor has plans to implement) show sharing between DirecTV DVR's (Unlike the superior TiVo units that they used to have).  So if you want to have a TV, you need to have a DirecTV box hooked up to that TV.  And if you have a DirecTV DVR, and record shows on it, you have to watch those shows in that room and only that room.  If you don't happen to have coax wired to that room from a central smart panel, then you are pretty much screwed (I suppose you could let the 3rd party contractor from DirecTV drill holes in your walls.  I wouldn't though).  Then there is the whole 4 box/multiplexer thing, need to buy & rent each box, seems like a real pain to me and really expensive.  Of course, you could just get a MythTV backend to record shows on (in a central location so you don't have to run lots of coax), then network frontends to each of your TV's so you don't have to have a DirecTV box at every location (which is $6/month as you stated before)

But to each his own.

---

