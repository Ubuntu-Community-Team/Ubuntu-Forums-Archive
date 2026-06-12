---
title: "Stop recordings from interrupting live TV"
date: 2008-06-24
forum: Mythbuntu
---

### Post by naudster on 2008-06-24
I have two tuners in my mythbuntu box. Watching live TV always defaults to Tuner 1. But when I schedule a recording it also wants to use Tuner 1 even when I'm currently watching live TV on it and Tuner 2 is free. So I get the onscreen message "MythTV wants to record  <whatever> now ...". I can manually change tuners (Menu -> select input -> Tuner 2) but it's a bit annoying.

What I'd like is for myth to record on the unoccupied tuner. Does anyone know the best way to go about this?

I know I can specify the input to use when scheduling a recording. But it's an annoying extra step and I can't expect my wife to always get it right. So usually I leave it at the default "Any input" but as I say it always prefers Tuner 1.

If live TV always defaulted to Tuner 2 that would probably solve the problem. Can that be configured?

I've had a look at the Input Groups in mythtv-setup but didn't understand it. The myth wiki has yet to document it: [http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Capture_Cards]("http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Capture_Cards")

Thanks for any advice!

---

### Post by shad0w_walker on 2008-06-24
[http://www.mythtv.org/wiki/index.php/Scheduling_recording#Priority](http://www.mythtv.org/wiki/index.php/Scheduling_recording#Priority)
From the Wiki:
```

Input preference (Input Priority)-- in the MythTV back-end setup program, the "Input Connections" section allows you to add additional priority in the "Input preference". Hi-light the connection and press the enter key. This is simply another priority factor but has an interesting effect. If a card input has a higher value than the other cards, the scheduler will see that you would rather record showings of episodes on this card rather than a showing on another card. If you have cards of different quality, you may want to set input preference to encourage the scheduler to record shows on your best card(s) whenever possible. If you have multiple back-ends you need to do this on each back-end. 
```

If you setup the second cards priority to higher than the first it should record using that as a preferance, which means it should leave your primary card alone unless you are already recording something and try to record another program.

---

### Post by naudster on 2008-06-24
Thanks shad0w_walker! I'll try that out after work and let you know.

---

### Post by volkswagner on 2008-06-24
> **naudster said:**
> 

I've had a look at the Input Groups in mythtv-setup but didn't understand it. The myth wiki has yet to document it: [http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Capture_Cards]("http://www.mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Backend#Capture_Cards")

Thanks for any advice!

I had a hard time understanding this also.  What you want to do is create an input group name.  Assuming both tuners use the same lineup this should work.  Then for each tuner select the input group you created.  This should make the system smarter.

---

### Post by naudster on 2008-06-25
I upped the input priority of the second tuner and that seemed to do the trick. Recordings default to tuner 2 first so don't interrupt me when watching live tv on tuner 1. Thanks!

As a separate experiment I changed the priority back to zero and tried volkswagner's suggestion:

> **volkswagner said:**
> What you want to do is create an input group name.  Assuming both tuners use the same lineup this should work.  Then for each tuner select the input group you created.  This should make the system smarter.

That didn't work so well. mythtv-setup's onscreen help states that only one input in an input group is allowed to record at a given time, and that's exactly what happened - I couldn't record 2 programs simultaneously. But I could record and watch live TV at once. The help also says that you shouldn't need input groups unless your inputs share the same physical hardware device.

Thanks again for the help. My mythbuntu box is a few weeks old now and with this tweak it's pretty close to being perfect.

---

### Post by tgm4883 on 2008-06-25
Seems the most obvious answer has been left out.

In the frontend go into Utilities/Setup > Setup > TV Settings > General on the first screen there the bottom two options are 


Avoid conflicts between live tv and scheduled shows
Allow live TV to move scheduled shows

These are the options you are looking for.

---

