---
title: "Y doesn't work to switch tuner cards"
date: 2010-03-05
forum: Mythbuntu
---

### Post by colinnwn on 2010-03-05
Hi,

I have 2 tuner cards. The primary is analog PVR-150 the secondary I added later is digital HVR-1250. When I am watching TV, Y does not switch from the PVR to the HVR. 

I tried watching the mythtvbackend.log when I press Y, but nothing happens there. I can use V to get into PIP mode and the HVR works. I can use B to switch focus and change channels on either card. I can even use N to switch the HVR to the main screen and PVR to the PIP. Then I can use V again to leave the HVR on the main screen and close the PVR PIP. But that is the only way I can change cards.

I searched and worked on this for almost 2 hours last night. The only reference on google I got was that Myth 0.21 switched the keybindings and Y is no longer bound to "NEXTCARD" and after the person did this, it worked. 

I used the mythweb keybindings utility to assign Y to "NEXTCARD", clicked save, restarted the frontend, and even the backend, I later went back and deleted all the other keybindings for Y except "NEXTCARD", but this didn't fix it for me. Does anyone else know what could be wrong?

Thanks.

---

### Post by klc5555 on 2010-03-05
With 0.21, the "next card" option came to be deprecated in favor of the current normal method: "m" for the menu in Livetv, followed by "switch inputs". You can't use this method? You should name each input (in Input Connections in the backend setup) so that these names in turn appear in "switch inputs" in the Livetv menu.

I'm not sure why "next card" came to be phased out. It may have had to do with its inefficiency when confronted with cards having multiple inputs of various types, and inputs existing on remote backends. I used to run into a problem where "Y" would only switch from whatever card I was on into my PVR 150, and then subsequently would only switch among the TV, S-Video, and Composite inputs on the 150 itself. With "m" and then "switch inputs", all available inputs are equivalent, however many there are of whatever sort or location, and switching seems always to work correctly.

---

### Post by colinnwn on 2010-03-08
Humm... That was the problem, thanks. Menu>Switch Inputs works fine. But it does cut into the girlfriend acceptance factor big time. Do you know if there is any way to enable 1 button switching between inputs anymore?

---

### Post by klc5555 on 2010-03-08
> **colinnwn said:**
> Humm... That was the problem, thanks. Menu>Switch Inputs works fine. But it does cut into the girlfriend acceptance factor big time. Do you know if there is any way to enable 1 button switching between inputs anymore?

Upon further review, you may have been bit by a known bug. There appears to be a recently closed ticket over at mythtv.org here: 

[http://svn.mythtv.org/trac/ticket/6472#comment:8](http://svn.mythtv.org/trac/ticket/6472#comment:8)

which seems to describe your problem, and lists it as "fixed" a couple of months ago. But I don't know the ifs and the hows of this fix's distribution, whether it is in fact your particular issue, nor whether you are running a version of mythtv which may have incorporated the fix, if the fix has in fact been distributed.

But at least it's a starting point for further investigation.

---

### Post by colinnwn on 2010-03-08
Well, bug or not, that trouble ticket directed me to the "Browse All Channels" option I didn't know about. That solved my problem. Thanks!

---

