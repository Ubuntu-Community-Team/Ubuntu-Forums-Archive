---
title: "Sound stops working after hibernate"
date: 2005-11-20
forum: Multimedia &amp; Video
---

### Post by Flame0001 on 2005-11-20
I've noticed that after I put my computer into hibernate, the sound stops working. I've verified with Alsamixer that the proper channels are indeed open, it's just that hibernate does something...

This has been reported on the Ubuntu bugzilla, but as far as I can see, no solution or workaround is posted there.

So what I'm wondering is this: Is there a workaround for this? A possible solution?

---

### Post by thirek on 2006-03-01
i'm still having the same exact problem on my thinkpad t23 running ubuntu 5.10, after hibernate sound no longer works. rebooting is the only way i know to bring back audio.

---

### Post by jf/ on 2007-09-18
bumping up an old thread - this problem still exists!!! T61, audio working before resume here as well... An 'alsactl store', followed by restore after the resume does not work.

---

### Post by mambazo on 2007-09-20
I had this problem as well. Sound card was detected and working, but I get no sound after resuming from a hibernate. What I did was open the volume control program, and searched through all the available scroll bars. I found one called "Wave" which was turned down to zero, Upon raising it up, I could hear again! Apparently the hibernate had reset its value to 0. I dunno what the difference between "Wave" and "PCM" is, but both seem to affect the sound volume of anything using alsa.

I keep PCM and Wave at around 70, and only fiddle with the master volume or individual application volumes.

Cheers,
Loban

---

### Post by jf/ on 2007-09-20
thanks, mambazo, but I think i'll need some additional help here. First of all, what system and sound card are you using? And how do you get to this "Wave" control? I've been searching around, but I haven't been able to find "Wave". Even in "Edit" -> "Preferences", I don't see it...

---

### Post by jf/ on 2007-09-23
anybody?

---

### Post by Mark Stosberg on 2007-12-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/11149](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/11149) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a T23, and on Gutsy, sound did not work after suspending. The instructions posted here under "No Sound after suspending to RAM" did bring my sound back without a reboot. 

[http://www.thinkwiki.org/wiki/CS4299](http://www.thinkwiki.org/wiki/CS4299)

I'm investigating how to automate this now. 

   Mark

---

### Post by Mark Stosberg on 2007-12-03
Ok, I figured how to automated this and posted the solution on the ThinkWiki:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T23#Power_Management](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T23#Power_Management)

   Mark

---

