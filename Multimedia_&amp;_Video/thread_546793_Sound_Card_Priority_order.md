---
title: "Sound Card Priority order"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by skiwithpete on 2007-09-09
Hi guys,

I'm a total noob, so bear with me.

I have a laptop (compaq X1000) that has an onboard sound card, and I also have an USB SBExtigy.

Today, I was completely shocked to play around in XMMS and find that I could set the XMMS to play from the SBExtigy by configuring the output plugin ALSA to hw:1,0.  [It seems the onboard card is hw0,0.]

Of course, when I went to Firefox to watch a youtube video, it was playing out of my laptop speakers.  I changed it in System>Pref>Soundplayback to my Extigy and hoorah it worked again.  

But when I unplug my Extigy and I get no sound.  And have to reconfigure it every time.  Plus, I have to reconfigure XMMS each time I open it depending if I have the Extigy plugged in or not.
[B]
Is there a way to set a priority for the Extigy to play if its plugged in, and the onboard to play if it isn't?[/B]

Again, I'm a complete newbie, so you need to type in what code I need to put in where to make things happen (I haven't got a clue - I'm trying to learn but it ain't easy).

Thanks,

P

---

### Post by skiwithpete on 2007-11-28
I solved my own problem.

I found that you can prioritize the Extigy with the command:

**asoundconf list**

Then once you've seen the list I set the Exitgy to highest priority with :

**asoundconf set-default-card Extigy**

Now when my Extigy is plugged in, it works, and when it isn't it plays through the laptop speakers.

Unfortunately, I can't seem to get XMMS to recognize this, but it works with Rythmbox and Video Players like VLC.

If anyone knows what I'm doing wrong in XMMS do let me know.

Cheers,

P

---

