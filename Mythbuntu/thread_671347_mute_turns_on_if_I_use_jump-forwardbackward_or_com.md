---
title: "mute turns on if I use jump-forward/backward or commercial skip buttons"
date: 2008-01-18
forum: Mythbuntu
---

### Post by the Goat on 2008-01-18
I have a weird problem.  On one of my frontend machines when I am watching a recording and I use any of the following commands: jump forward, jump backward, or skip commercials, the sound goes away.  Once I press the mute button MythTV says "mute off" and the sound returns.  So for some reason MythTV is automatically turning on mute whenever I try to navigate through a playing video.  Any ideas?

---

### Post by foxbuntu on 2008-01-20
Can you please provide more details about what you are doing? Are you using a remote? If so what remote?

---

### Post by the Goat on 2008-01-21
> **foxbuntu said:**
> Can you please provide more details about what you are doing? Are you using a remote? If so what remote?

I am using a keyboard.  None of the commands have been remapped.  I use the default keymap for MythTV.  The offending keys seemed to be:
right = jump forward 30 sec
left = jump back 2 secs
up = jump forward 10 min
down = jump backward 10 min
Z = skip commercials
Q = skip back commercials

This problem has disappeared after rebooting the offending frontend.  But another user reported the same fail on the mythtv-users mailing list.  He used ubuntu also.

---

### Post by drewbub on 2010-05-06
I can confirm this is happening to me too.

I just upgraded to 10.04. 

I haven't tried to reboot it yet but I will right now and post back.  I am using the Keyboard, and It also happens when using the network remote on my Android phone (MythMote) which uses telnet I believe.

---

