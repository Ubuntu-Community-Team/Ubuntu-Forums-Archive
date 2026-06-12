---
title: "No Sound (most of the time)"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by avi650 on 2007-05-22
Hello,
 i am new to linux, have been playing with it for about 2 weeks now. and about 10 installation later i still dont understand what is going on. somthimes i have sound and all is good at other times the sound is dead.is there anyone who can help me because music is the deal breaker for me and i dont want to go back to XP

sound card is Creative Sound Blaster Audigy SE

---

### Post by josesanders on 2007-05-24
When you say the sound is dead, can you be more specific?  If you look in the upper right part of your desktop, does the sound icon indicate that sound is working?  If Ubuntu believes that sound is working, you will have a small image of a speaker.  If not, the same image will have a red line through it.

Is your sound card PCI?  Do you also have sound on your motherboard?  I have sometimes had problems when running two sound devices because when you boot Ubuntu, the devices are not necessarily registered in the same order every time.  Most of your audio applications are set to automatically use the first sound device, but which physical device that corresponds to can change every time you boot.  That could explain why it works sometimes and not other times.

That's just an idea.  Let me know more details about exactly what happens when it is working and when it is not.

---

### Post by twistedtwig on 2007-05-25
I have a very similar if not the same problem with an Audigy 2 card.  

by DEAD I mean there is nothing.  The icon things there is sound.  Cant see anything muted on any of the windows.

It has me very confused

---

### Post by twistedtwig on 2007-05-29
found this link worked for me when nothing else did

[http://ubuntuforums.org/showthread.php?t=457761&highlight=audigy](http://ubuntuforums.org/showthread.php?t=457761&highlight=audigy)

---

### Post by stchman on 2007-05-29
> **avi650 said:**
> Hello,
 i am new to linux, have been playing with it for about 2 weeks now. and about 10 installation later i still dont understand what is going on. somthimes i have sound and all is good at other times the sound is dead.is there anyone who can help me because music is the deal breaker for me and i dont want to go back to XP

sound card is Creative Sound Blaster Audigy SE

My one PC has an Audigy2 and the built in sound.  You need to specify a default sound card.  The best way to do that is follow my procedure:

[http://www.stchman.com/mult_sound.html](http://www.stchman.com/mult_sound.html)

This fixed the problem on my setup.

---

### Post by avi650 on 2007-06-04
thanks stchman that solved the problem. my card is audigy SE and the 

this was the list i got:

Names of available sound cards:
ICH5
CA0106
U0x46d0x8ad
 
a little googling and i found out that the SB audigy SE is the CA0106 and it worked like a charm after setting it as default

---

