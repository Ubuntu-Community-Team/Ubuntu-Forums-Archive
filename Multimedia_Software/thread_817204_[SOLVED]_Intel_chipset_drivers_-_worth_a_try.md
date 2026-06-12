---
title: "[SOLVED] Intel chipset drivers - worth a try?"
date: 2008-06-03
forum: Multimedia Software
---

### Post by jasontu on 2008-06-03
I hope people aren't sick of my adventures in trying to get my microphone to work.  It seems like I'm always taking two steps forward only to fall two steps back.

Just to review:
Mic unmuted in alsamixer and graphical volume controls: check
Feed from mic heard on speakers: check
Mic detected by any program like sound-recorder or teamspeak?: negative :confused:
USB mic attempted: detected, but not even heard through speakers

I am using onboard sound from the Intel 945 chipset.  I have also never installed the Intel drivers from Intel's website.

Is it worth trying the Intel drivers?
How difficult is it?
What are the odds I'll seriously botch anything that wasn't a problem before trying to do this?

Thanks!

---

### Post by wolfen69 on 2008-06-03
i guess it's worth a try if they have a microphone driver for linux. but dont get your hopes up. ask around and find out what people are using for microphones. if you can afford it, buy a new one. it will save some headaches.

99% of hardware that will work with ubuntu will either work from the beginning, or is a paperweight.

---

### Post by jasontu on 2008-06-03
Any recommendations for a soundcard in that case?

---

### Post by jasontu on 2008-06-18
I got a TurtleBeach 5.1 Channel sound card and it worked right out of the box.  I had to change the priority to make it the default sound device, but it was a lot easier than fiddling with the HDA intel chipset.

---

