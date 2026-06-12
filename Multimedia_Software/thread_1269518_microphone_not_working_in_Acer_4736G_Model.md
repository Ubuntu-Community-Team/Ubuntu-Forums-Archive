---
title: "microphone not working in Acer 4736G Model"
date: 2009-09-18
forum: Multimedia Software
---

### Post by prasad.bh1 on 2009-09-18
Hello all,


I installed latest Ubunut 9.04 on my laptop Acer 4736G.
Headphone and microphone not working, but headphone started working when I followed
instructions at the link [https://help.ubuntu.com/community/So...otingProcedure](https://help.ubuntu.com/community/So...otingProcedure).


OK, let me explain in brief,

I have dual boot, vista+ubuntu. Lan port blinks when i use vista, it means it detects it. But when i start ubunutu it does not. However, it detects wireless in both.


Microphones are not at all working, tried many things, like updating alsa mixer etc.
but to the no avail.

Looking forward for your advise/solution.

wr,
prasad

---

### Post by guushoekman on 2009-09-26
I have an Aspire 4736. Not a G. Still, same problem. Incredibly frustrating.

Does anyone have a solution??

---

### Post by MarcTH on 2009-12-31
Bump!

I am running Ubuntu 9.10 on an Acer Aspire 4736G and have two persistent hardware problems remaining: sound input and the card/memory stick reader are both not working.

Microphone: I use Skype a lot for international calls and I cannot get either the internal microphone on the laptop or my USB handset to work.


Any advice gratefully received, many thanks in advance,

Marc.

---

### Post by Neezer on 2009-12-31
I recently had this problem, but with an HP dv6. I hope this helps....

I have alsamixer installed, and didn't reallize there is a a section for input devices.

in a terminal type alsamixer

then press tab and it takes you to an input screen where you can change the gains on the input devices.....Mine was turned way down, so people I was skyping with couldn't hear me at all...

Hope this helps.

---

### Post by Jimtheplanner on 2009-12-31
I don't know if this helps. I opened "alsamixer" in terminal & set it side by side on screen with "sound" from preferences.

First check the input tab in "sound" make sure that the mute box in not ticked.

Second I worked my way along "alsamixer" with my mic plugged in to find which setting triggered a response within "sounds" for me it was the digital control in alsamixer, I had to set to "analog1" - bingo!!!

Hope this is of some help...

Jim

---

### Post by prasad.bh1 on 2010-03-09
so, not yet found any solution for this weird problem :(
anyone, has come acrsoss this problem before ?

Thinking, what could be wrong ? :(

no solution in sight so far .. pls help !

---

### Post by prasad.bh1 on 2010-03-21
Hi,

I got reply after such a long time when I had reported this problem as bug. well, I was really frustrated to see that microphone was not working and everything was just fine and out of that frustration, I removed ubuntu from my system..

But wait, I have certainly a very good news for you ! as some of you guys had this problem. After I got mail from Brad Fig of Cannonical, I thought to give it a try and woooh ! it worked. :D :D

I had cd for 9.04 and as soon as I installed it, I checked and it was the same story :( so then I upgraded to  9.10 and yes microphone worked well !

THanks so much for the team for their efforts :)

with regards,
prasad bhadrashete

---

### Post by akannankeril on 2010-03-27
@prasad.
hi i am having the same issues and been looking around for siolutions for months now. mine is an aspire 4736 with xp n ubuntu9.10 
my microphone is not working yet and its getting frustrating!

---

