---
title: "Hauppage PVR-150, Mythbuntu 10.10 horrific signal quality"
date: 2011-02-13
forum: Mythbuntu
---

### Post by MyersVandalay on 2011-02-13
Alright I am scratching my head at this. I spent most of the weekend figuring out how to get the sql database working, finally got everything linked up, and almost working.

Almost being the key word, at first I had mistakenly set the system up to us-bcast, and was of course only able to get the local channels in mediocre quality, after figuring that out I switched it to us-cable-hrc, now all channels work but the signal quality is horrendous, sound is 90% static, impossible to hear, picture is extremely fuzzy, much worse then when I was set incorrectly. Basically looks as if I were using an old school antenna trying to pick up a station 3 cities away. (it's using time warner cable if that information is of any use). Looking this up I'm hearing some saying things like it's likely to need an amplifier for the signal, then on the other hand i'm also hearing other people with similar problems and the issue being the signal to strong and needing a resistor or something of that nature, how can I figure out which is the case, or if the frequency is just off by a bit?

My brain is frying, anyone have any ideas?

---

### Post by klc5555 on 2011-02-14
The PVR-150 is analog only. Does Time Warner in your area still transmit analog at all? Or if they do, do they transmit analog beyond the channels 2-20, which will now be in low-power and poor quality mode en route to being discontinued completely?

If Time Warner is transmitting the locals (maybe including HD) in clear QAM digital, you'll need a QAM-capable tuner. If Time Warner is expecting the standard digitals to be received and converted to analog via a settop box or DTA, and then fed into your analog tuner through channel 3 or 4, you'll need to set up your PVR-150 on that channel, and have mythtv tune the DTA or settop using lirc.

If however you really do have a wide range of analog stations available to you for the time being, and suspect that your signal is too strong and may be swamping the tuner, you could test this. Simply stick in a cheap 2- or 4-way splitter (which you may already have on hand) just ahead of your tuner card and give it a go. The signal will either be better or worse --if better, you can arrange for a more permanent signal attenuator solution; if worse than this is likely not the problem.

---

### Post by nickrout on 2011-02-14
Also I think the default for the pvr is set to something less than ideal. You need to set it to something like 720x480. There is a thread here:

[http://www.gossamer-threads.com/lists/mythtv/users/120311](http://www.gossamer-threads.com/lists/mythtv/users/120311)

---

### Post by Boppy3125 on 2011-02-15
My own plan would be to start with any TV you have that might have a old analog tuner and verify the coax connection/cable/splitter is all working.  If you have similar issues there you can call Time Warner.  (My experience with them that most of the field guys are fascinated by the idea of MythTV but won't really support it.)  I don't recall what I used for scanning the channels though, I haven't change part for about 2 years.

If the TV works fine, you know it is something with your tuner card setup.

Good luck.

---

### Post by MyersVandalay on 2011-02-15
Well I pretty much noted without the cable box and plugging straight into the TV, 1-75 (all the channels I might actually watch) do work, and plugged into the mythbox, it gets the picture, just extremely fuzzy. If it were the resolution, I wouldn't expect the sound to be covered in static. I'll dig around and see if I can find a splitter, if I find one I'll report back on it.

---

### Post by agamotto on 2011-02-17
> **MyersVandalay said:**
> Well I pretty much noted without the cable box and plugging straight into the TV, 1-75 (all the channels I might actually watch) do work, and plugged into the mythbox, it gets the picture, just extremely fuzzy. If it were the resolution, I wouldn't expect the sound to be covered in static. I'll dig around and see if I can find a splitter, if I find one I'll report back on it.

This may fall under the stupid category, but I bet what is going on is that the signal isn't strong enough for the card's tuner.  Every time to branch/tap the cable line coming into your home, you halve the signal strength.  When I had cable, I hooked up a $15 signal booster from Radio Shack to the line before any splits, and that solved my poor 'reception' with the pvr-150.  It may also work for you hooked up to just the section of coax going into your tuner.  Experiment!  

Good luck!

---

### Post by johntaylor1887 on 2011-02-18
You don't need mythbuntu if you just want to watch basic cable with your card. I have the pvr150, and it works great with VLC player. If you post back, I'll watch this thread and tell you how I did it. Very easy.

---

