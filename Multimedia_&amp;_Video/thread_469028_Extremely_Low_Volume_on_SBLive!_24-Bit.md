---
title: "Extremely Low Volume on SBLive! 24-Bit"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by DocHoliday52090 on 2007-06-09
Just installed Ubuntu on my desktop, and there's barely any sound. 

There wasn't any at first, but after muting "IEC958" and bring "Analog Side" to max, I got a tiny bit of music from MPlayer with everything up. I get tons of white noise as well. 

Ubuntu identifies the card as "SB Audigy LS".

Is there anything I can do?

---

### Post by blastus on 2007-06-09
In System->Preferences->Sound->Sounds have you tried the play some of the system sounds? Have you checked your audio cables/adapters? I just recently replaced the y-adapter for my audio cables because I started to experience the same thing you describe...a lot of white noise and sound you can barely hear with the volume maxed.

---

### Post by DocHoliday52090 on 2007-06-09
Yeah, that didn't work either. Only cao106 works. 

The cables all work in Windows, so that can't be it.

---

### Post by DocHoliday52090 on 2007-06-09
The kernel module for my card seems to be included in ALSA, and it's loaded as well.

---

### Post by JavaJim on 2007-06-09
DocHoliday :

I was having the same problem  :

     SBLive 24-Bit
     Recognized as SB Audigy LS

     Had to mute IEC958 to get anything out.


In AlsaMixer :

Try finding the channel  'Analog Front' and max its volume.
That did it for me !

In fact, it turns out that is the only one that effects volume on my box.

Good luck.   :D

JavaJim

---

### Post by DocHoliday52090 on 2007-06-09
Tried that. 

Strange thing is, I get a miniscule amount of sound in MPlayer, but nothing at all from Exaile. 

My volume can only be changed with "Analog Side", but even at max, the sound is incredibly low. I have to turn my speaker up all the way up to 100% ot even really identify the sound. Even then, there's so much white noise from the speaker's amplification it's useless. 

It's almost as if I can't bring the card's volume high enough.

---

### Post by JavaJim on 2007-06-09
What about Headphones ??

Have you tried plugging them directly into the sound card??
To see if you get adequate volume there??

I know this is reaching...since it works in Windows.

But,  it was the first thing I got working before moving on
to other issues.

JavaJim

---

### Post by DocHoliday52090 on 2007-06-10
Solved!

It was the strangest thing. 

While I was reaching behind the PC to put in the headphone cable, I accidentally knocked the left and right cables halfway out. 

Perfect sound!

It seems like only ONE of the connectors on each input cable can be connected (the one on the side of the jack that touches first when you enter it in. The other one - the connector on the very top tip - only meets its counterpart when fully pressed in. This is why you get only sound in one of your headphones when you knock your headphone cable half out). 

I think this may be a result of Ubuntu thinking this card is the Audigy LS. If this is true, I am unable to get left and right differentiation.

---

### Post by JavaJim on 2007-06-10
Glad you solved it !!

Now you know why I wanted you to try the Headphones....   :D

I have found many gremlins by trying different input/output devices.

Your thread helped me as well.  At least I knew someone else with the
same card was having the same problem.

Thanks again,

JavaJim.

---

### Post by MichiganMan on 2007-06-10
Here's how I solved my problem of Ubuntu being too quiet.  Right click the Volume Icon.  Choose Preferences and change the selected device from Master (which you probably have maxed) to PCM. Max that out.  Then go back and change it the selected device to Front.  Max that one out as well.  By now you've hopefully blasted yourself out.  ;)  So go back to preferences, change it back to Master and tune it to a more family friendly level.  

Hope this helps.

---

### Post by DocHoliday52090 on 2007-06-11
:(

It looks like I spoke too soon. 

I can't jack the volume too high from my speakers without the famous high pitched wine from hell. It probably stems from the fact that the jacks are only half in. 

Is there any way I can get my sound card working with the jacks all the way in? Maybe that will cut out the humming. 

In addition, I don't hear anything from flash. 

Help please :(

Oh, and m y card doesn't have a PCM slide. That worked on my laptop though, ages ago. A fine fix, that one.

---

### Post by benjoseph on 2007-06-20
Hi MichiganMan, You solved my problem, it worked FANTASTIC. Thank you ever so much:p

---

