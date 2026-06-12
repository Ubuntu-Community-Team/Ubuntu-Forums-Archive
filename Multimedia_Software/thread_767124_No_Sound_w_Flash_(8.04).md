---
title: "No Sound w/ Flash (8.04)"
date: 2008-04-25
forum: Multimedia Software
---

### Post by fullmetalgerbil on 2008-04-25
I just managed to get Hardy installed on my box, but after installing the flash-nonfree plugin I get flash video yet without sound.
Any help would be much appreciated.

---

### Post by fullmetalgerbil on 2008-04-25
Note: the sound is working with Rythmbox etc. just not with flash videos.

---

### Post by cotcot on 2008-04-25
I had the same when I upgraded from 7.04 to 7.10 in 64 bit. Removing the alsa configuration files (~/.asoundrc and another one that i do not remember anymore) solved the problem.

---

### Post by fullmetalgerbil on 2008-04-25
Thanks for the hint. However I have no idea exactly how to remove those files nor do I know whatall files to remove, or even if its necesary considering I'm running 32 bit.

---

### Post by savagenator on 2008-04-25
sound does not matter in different archs. Delete the file in the home folder (enable hidden files)

---

### Post by fullmetalgerbil on 2008-04-25
I'll give it a try, though I'm not exactly sure how to enable hidden files

---

### Post by Comreak on 2008-04-25
You might try what I suggest here:

[http://ubuntuforums.org/showpost.php?p=4789145&postcount=27](http://ubuntuforums.org/showpost.php?p=4789145&postcount=27)

It got sound in flash working for me, at the cost of making flash a little unstable.

---

### Post by baju on 2008-04-25
I had the same problem, but I solved it.
Method 1:
killing PulseAudio with killall pulseaudio

Method 2:
installing non-free flash player and install the package libflashsupport

---

### Post by fullmetalgerbil on 2008-04-25
cot cot and savagenator: the file ~/.asoundrc does not exist on my system to be deleted. Thank you for the wild goose chase.
Comreak:Tried it, no success at all.
Anybody got any other ideas?

---

### Post by ubuntu-freak on 2008-04-25
Have you tried baju's suggestion? Install the libflashsupport package, then restart Firefox and/or logout.
 
Nathan

---

### Post by fullmetalgerbil on 2008-04-25
Nothing so far has worked. Nice try with the killall pulseaudio "command". The more time I spend on this thread the more I feel you people are just taking the piss out of me.

---

### Post by fullmetalgerbil on 2008-04-25
My apologies everyone, for being such a cranky b*stard. I feel so stoopid. I installed libflashsupport and was just needing a browser restart. Duh!
Thanks everyone for the suggestions, somehow at least one of them worked.

---

### Post by ubuntu-freak on 2008-04-25
> **fullmetalgerbil said:**
> Nothing so far has worked. Nice try with the killall pulseaudio "command". The more time I spend on this thread the more I feel you people are just taking the piss out of me.

 
Really? He suggested that to see if was PulseAudio related.
 
Try part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683), install the packages for whichever Ubuntu Hardy variant you are running. Then try purging flashplugin-nonfree from your system and install it manually with the instructions in my thread. 
 
Nathan

---

### Post by ubuntu-freak on 2008-04-25
*snip*

---

### Post by reilly2040 on 2008-04-26
Just wanted to say thanks to baju.  I was having the same problem (no sound with the non-free flash player).  Installed libflashsupport and it works a treat.

Thanks :)

---

### Post by locky28 on 2008-04-26
Hi all, I'm having trouble with Flash aswell. I installed the non free flash player and video's play fine except theres no sound. Sound works fine in Rythembox and I get system sounds ect.

I had a look in System, Preferences, Sound and my mixer device is set to HDA Intel ALSA, and I couldn't see any options for Pulse Audio, should there be something there?

BAH Scrap that, bad video it's working fine thanks everyone.

---

### Post by baju on 2008-04-26
fullmetalgerbil: This command seems a bit stupid, but the problem is that the flash player doesn't work with the pulseaudio server auto of the box. By killing Pulseaudio you will force Ubuntu to select a different Audioserver ( e.g. Alsa ). This worked on my machine and some other. Finally I now use libflashsupport,non-free flasg and Pulseaudio.

Btw: I found this page: [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup) . It shows solutions for different problems with pulseaudio.

---

### Post by Fitech on 2008-11-23
Thanks Ubuntu-Freak.  You pointed me in the right direction to be able to fix my flash audio problem.  [http://www.pulseaudio.org/wiki/FlashPlayer9Solution](http://www.pulseaudio.org/wiki/FlashPlayer9Solution)  has great instructions.  The one trick was figuring out to type...

git-clone git://git.0pointer.de/libflashsupport.git

---

### Post by psyke83 on 2008-11-24
> **Fitech said:**
> Thanks Ubuntu-Freak.  You pointed me in the right direction to be able to fix my flash audio problem.  [http://www.pulseaudio.org/wiki/FlashPlayer9Solution](http://www.pulseaudio.org/wiki/FlashPlayer9Solution)  has great instructions.  The one trick was figuring out to type...

git-clone git://git.0pointer.de/libflashsupport.git

Please, don't do that.

Read: [http://ubuntuforums.org/showpost.php?p=6231499&postcount=8](http://ubuntuforums.org/showpost.php?p=6231499&postcount=8)

---

### Post by ubuntu-freak on 2008-11-24
> **psyke83 said:**
> Please, don't do that.

 
Agreed. My post was made when libflashsupport was useful - many months ago.

---

