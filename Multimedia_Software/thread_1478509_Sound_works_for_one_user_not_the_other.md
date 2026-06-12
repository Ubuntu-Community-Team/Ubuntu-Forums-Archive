---
title: "Sound works for one user not the other"
date: 2010-05-09
forum: Multimedia Software
---

### Post by lile001 on 2010-05-09
I've got a sound problem, read through the sticky post about comprehensive sound problem solutions and didn't see anything that looked relevant.  However, I am a rank NOOB so the solution could have been there and I'd not recognize it.  

Here is the issue:  There are two users on my system, and sound always works on one of the logins.  On the other login, after we start the computer the sound does not work.  However, if I go to Sound Preferences and click any test button, the sound suddenly starts working under that user's login. Usually by that time someone has tried to start Pandora or play a playlist or something, and the sound starts right up in the middle of a song, which was playing but unheard.   I don't have the foggiest idea how  to test any of this from the terminal, which is of course where all the Geeks want you to start.  None of these problems existed a month ago, and the whole system was loaded new with Ubuntu 9.04 in July of 2009.  No recent hardware chagnes that I can think of.

---

### Post by lile001 on 2010-08-28
> **lile001 said:**
> I've got a sound problem, read through the sticky post about comprehensive sound problem solutions and didn't see anything that looked relevant.  However, I am a rank NOOB so the solution could have been there and I'd not recognize it.  

Here is the issue:  There are two users on my system, and sound always works on one of the logins.  On the other login, after we start the computer the sound does not work.  However, if I go to Sound Preferences and click any test button, the sound suddenly starts working under that user's login. Usually by that time someone has tried to start Pandora or play a playlist or something, and the sound starts right up in the middle of a song, which was playing but unheard.   I don't have the foggiest idea how  to test any of this from the terminal, which is of course where all the Geeks want you to start.  None of these problems existed a month ago, and the whole system was loaded new with Ubuntu 9.04 in July of 2009.  No recent hardware chagnes that I can think of.


Upgraded to Ubuntu 10.04.  Some random Youtube videos don't have any sound (I am pretty sure they are sending it), sometimes when I switch users, the second user has no sound, usually fixed on reboot.  This is the case through headphones and also through the speaker jack in the back of the machine.  So far all I can say is randomly the sound does not play, and it appears the hardware is working OK.  Any ideas where to start looking.

---

### Post by lile001 on 2010-08-29
Does anyone have any idea where to even start?  Surely there is some way to troubleshoot this problem?  No responses at all......

---

### Post by gordintoronto on 2010-08-30
You could run Administration/Synaptic to check that the apport package is installed, if not install it.

Then in Accessories/Terminal, paste this command:
ubuntu-bug audio

It should give you instructions for reporting a bug.

---

