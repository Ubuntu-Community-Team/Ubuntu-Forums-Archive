---
title: "I got A2DP working finally!! But now it sounds choppy..."
date: 2009-10-15
forum: Multimedia Software
---

### Post by lavadisco on 2009-10-15
Sound quality is fantastic, however, very often it sounds like it speeds up and is also often choppy with dropouts. None of this happens when I run A2DP from my Win XP side, so I know it's not the bluetooth send/receive hardware or even the range.

Anybody have any ideas for fixing this?

---

### Post by benmoran on 2009-10-16
What version of Ubuntu are you running? I had similar issues on Jaunty, after using all the different utilities to get it going. 

However i'm using Karmic now, and a2dp just works flawlessly out of the box. You can just change the default audio sink from the volume control application. 

If you aren't yet running Karmic, this is a good reason to switch to it. If you are, make sure you do all the updates. There have been a bunch of Pulse and Bluez updates in the last weeks.

---

### Post by lavadisco on 2009-10-16
Yep, I'm using Jaunty. I prefer to wait a few months before I grab the new distros... gotten burned a couple of times before. But you may have just convinced me.

---

### Post by benmoran on 2009-10-16
Why not set up another partition for Karmic, and see how it runs? I've run it since Alpha 2. There was a lot of stuff changing and a few problems, but since the feature freeze it's been rock solid. A lot of folks have posted that it's been pretty stable for them as well. Jaunty was a little bit rushed feeling, but Karmic feels pretty much ready. 

It's probably best to do a fresh installation anyhow, if you've installed different Pulseaudio or Bluetooth utilities. If you have the hard drive space, set up a dual boot and bring all your files over. 

The sound manager/pulse integration is so awesome I actually was thinking of making a thread about it. Pulseaudio had some growing pains, but it really is awesome. I mean, you can have your laptop volume muted. Once you pair the bluetooth and switch the output to it, it has it's own volume control. If you disconnect the headset, it goes back to being muted. I even tried it with a bluetooth handsfree, and it lets you output the audio stream to that if you want to. A new mic is added in the list as well. These are awesome times for bluetooth :guitar:

---

### Post by lavadisco on 2009-10-16
Wow, Koala sounds great! 

I don't think I will do a clean install. I have been using Ubuntu only since Hardy, so I am not super-experienced yet. And I have done so freaking much tweaking just to get it all working well like it is now that I'd hate to wipe it all. Although I would imagine that much of what I had to tweak before probably works out of the box in Koala.

---

