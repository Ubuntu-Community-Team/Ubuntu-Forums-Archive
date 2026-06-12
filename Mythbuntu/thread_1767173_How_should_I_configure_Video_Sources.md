---
title: "How should I configure Video Sources?"
date: 2011-05-25
forum: Mythbuntu
---

### Post by dilbert2k on 2011-05-25
Hello,
 
I am looking for some advice as to how I should configure video sources for my DVB-S and DVB-T tuners. I have googled extensively, and am more confused now than before!
 
I have a Tevii S660 DVB-S (S2) tuner and a Kworld UB399 Dual DVB-T tuner, so three tuners in total.
 
 

I'm planning to use EIT for EPG data. My question is whether I should use 1, 2 or 3 EIT Video Sources:[LIST=1]
[*]One Video Source used by all three tuners
[*]One Video Source for the DVB-S tuner and a second for the two DVB-T tuners
[*]One Video Source per tuner.
[/LIST]What do others with similar combinations of tuners do?
 
TIA
D2K

---

### Post by klc5555 on 2011-05-25
You usually use different video sources when the channel lineups available to individual tuners differ, or the tuning specifics of the tuners differ. Because otherwise, Mythtv would have a hard time deciding which tuner to assign to a specific recording and could easily assign, say, an analog tuner to try to record a digital channel or the reverse if there were only one Video Source across a bunch of tuners of different types.

So in your case, the dvb-s would (I assume, I don't own one) have a different array of channels available, and would be tuned differently, than the dvb-t tuners. On the other hand, the two dvb-t tuners would likely have the same array of available channels tuned the same way for them both.

So, as a first try, you'd go with 2 Video Sources: one for the dvb-s tuner and one other for the two dvb-t tuners.

There could be cases where you'd need 3 Video Sources instead. For example, say one of your two dvb-t tuners was mildly defective, and simply could not tune three stations the other dvb-t tuner could. In this case, you'd prepare a 3rd Video Source for the defective tuner, in which the three untunable stations are deleted by using the Channel Editor. That way, Mythtv wouldn't try to assign the defective tuner to record something on a channel it was incapable of receiving.

I use dvb-c and analog across 3 backends on 3 pchd5500s, and 4 hauppauge 1600s. I have composed 3 Video Sources: Digital (which handles all the dvb-c Clear QAM channels for all 7 cards); Analog (which handles all the channels for three STB inputs on 3 of the 4 Hauppauge 1600s); and Old-Style Analog, which handles the few plain unencrypted analog channels my local Comcast still provides, and routes them to the analog halves of the 3 pchd5500s and the analog input of the one Hauppauge 1600 that I've never bothered getting a STB for.

---

### Post by dilbert2k on 2011-05-25
Thanks klc5555
 
You've confirmed my thinking. I was going to go for two video sources, but think I will now make it three. 
 
Thanks for the advice.
 
Cheers
D2K

---

