---
title: "Sound randomly cuts out"
date: 2010-06-15
forum: Multimedia Software
---

### Post by RobinBrown on 2010-06-15
This is one of two niggles I've had in migrating to ubuntu, which I must say is (otherwise) absolutely fab. Problem 1 is an 18 month old "legacy" ATI card, which refuses to be fixed. Problem 2 (I suspect) is more solvable.

When listening to music, (either from youtube or rhythmbox) after an indeterminate period of time, (it varies substantially from around  5 mins - 1 hour) the sound cuts out without warning. Videos continue to play, but in silence. This silence affects the browser as a whole (chromium). A workaround for this has been to simply restart the program, but this is becoming quite annoying. Sometimes issuing ```
pulseaudio -k
``` is necessary to restore sound. What is going on? Anyone else with similar problems?

Thanks in advance :)

---

### Post by lilychef on 2010-06-15
I have had similar problems, although I've never been present when the audio stops playing...  It actually began as more of your problem, but now has evolved to another... Not sure if the first fix caused the second issue, but I appear to not be alone.... Check out my thread [here]("http://ubuntuforums.org/showthread.php?t=1503928").

I'm still waiting fror help as well.  Something tells me this is a population-wide issue, and hopefully there'll be a fix provided in an update sometime soon...

---

### Post by RobinBrown on 2010-06-16
Some more info:
When the sound cuts out, looking in System-->Preferences-->Sound and checking the program levels reveals that the chromium alsa plugin disappears from the menu. It seems that either the alsa plugin or pulseaudio has crashed. However, as this bug also affects rhythmbox, I suspect pulseaudio is to blame. Consequently, I have tried the pulseaudio fix on your thread, and see if that sorts it. 
Also, in the output tab, the correct sound card remains checked, so that isn't the problem.

Can anyone else confirm this bug?

---

### Post by Hartknyx on 2010-06-17
I can confirm it - at least, I've been having the same trouble. My sound cuts out occasionally in Chrome (infrequently - maybe once or twice a day) and when I play Guild Wars under Wine (much more often, randomly about every 5 minutes to half hour), and the only way I can find to fix it is to completely restart the program. I haven't noticed a problem in Rhythmbox, though, and I've never had to kill pulseaudio to solve it. Also, my problem appears to differ in that when I check System > Preferences > Sound after the sound has cut out, the Alsa plug-in is still listed - at least for Wine; I haven't gotten the opportunity to check for Chrome yet.

I'm running a clean install of Ubuntu 10.04 32-bit, and I haven't installed any extra sound drivers - I'm just using whatever comes out of the box.

---

### Post by lilychef on 2010-06-17
What was really strange for me is how everything worked like a charm for a few days before it quit working.  And there was DEFINITELY a system update in between working and not working.   I just wish I had paid attention to exactly what it was....

---

### Post by RobinBrown on 2010-06-18
The pulseaudio fix turned all the sound off for me, so I suggest undoing that. I thought this may have been happening to me because I have installed the ubuntustudio-audio and ubuntustudio-audio-plugins packages, but this seems not to be the case. 64 bit flash was another wrongly accused suspect.

This is infuriating ](*,)

---

### Post by jiex on 2011-02-03
Hi there
I wonder if anyone has found a solution to this problem? In Karmic, I had not sound problems at all. With Lucid, I found that with Totem (and vlc) the sound cuts out randomly. As far I I can work out, the song playing resumes not where it cuts out, but where the song would have been if the sound had not cut out.
BTW, I am using a RAEDON 4200.

---

