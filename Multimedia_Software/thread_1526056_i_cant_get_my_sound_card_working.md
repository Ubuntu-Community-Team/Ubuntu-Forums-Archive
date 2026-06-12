---
title: "i cant get my sound card working"
date: 2010-07-07
forum: Multimedia Software
---

### Post by ahmednady on 2010-07-07
my creative sound card isnt working with my ubuntu
it's my 1st time to use ubuntu
i have a built in  sound card but it's not working
written Ectivia
i dont have an ectivia soung card
i have Creative and Realtik
i want the ubuntu to install the Creative

---

### Post by Yarui on 2010-07-07
The drivers for sound are the same pretty much no matter what card you are using.  You don't really need to install sound cards.  Open up your terminal and enter the command
```
alsamixer
```
This will open up a volume control program.  You can hit F6 to select a sound card.  M mutes and unmutes channels.  Make sure all the necessary channels are unmuted and have their volume up.

---

### Post by ahmednady on 2010-07-07
I did as u said 
not working

---

### Post by marin123 on 2010-07-07
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

maybe this can help.. i had some problems with my soundcard and this solved my problems...

---

### Post by lidex on 2010-07-08
> **ahmednady said:**
> my creative sound card isnt working with my ubuntu
it's my 1st time to use ubuntu
i have a built in  sound card but it's not working
written Ectivia
i dont have an ectivia soung card
i have Creative and Realtik
i want the ubuntu to install the Creative

So you have realtek onboard sound and add-on creative and you want to use the creative card, correct? You can make things simpler by disabling onboard sound in bios. Or try these links:
[http://ubuntuforums.org/showthread.php?t=922860]("http://ubuntuforums.org/showthread.php?t=922860")
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012]("http://ohioloco.ubuntuforums.org/showthread.php?t=843012")

---

