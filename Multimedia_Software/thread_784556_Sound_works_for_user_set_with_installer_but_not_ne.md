---
title: "Sound works for user set with installer but not new user added later"
date: 2008-05-06
forum: Multimedia Software
---

### Post by wkulecz on 2008-05-06
I haven't a clue here.  For the default user setup by the installer sound works.  But for a new user added after installation everything seems to work but no sound!

--wally.

---

### Post by wkulecz on 2008-05-07
Bump.

I filed this as a bug report on launchpad #227841, after creating a third user that still gets no sound. Only the user created by the installer gets sound.

--wally.

---

### Post by wkulecz on 2008-05-13
So many problems, so few solutions ....

I've found a work around, If I log in with the default user (the one created by the 8.04 installer) I can get sound for the others (created by Add User) if instead of logging out I use the user switcher to run as one of the added users.

Not a great solution in general, but when I clone the system the default user is what everyone will be using, the added user is a login only for me so I will have my development environment available on the cloned systems.

I don't see anything in session startup running for the default user that is not also running for the added users.

What exactly was the upside of pulse audio supposed to be?  I see no gain, only pain.  Had zero audio issues with 6.06 and 7.04.

--wally.

PS re launchpad.  No response is better than posting boilerplate "troubleshooting" instructions which only proved you didn't really read what I wrote.

---

### Post by prshah on 2008-05-14
> **wkulecz said:**
> I haven't a clue here.  For the default user setup by the installer sound works.  But for a new user added after installation everything seems to work but no sound!


You have to add the user to the "audio" group;```
sudo adduser username audio
``` where your replace username with the actual username which needs audio access.

---

### Post by wkulecz on 2008-05-14
Nice try, but the "Add User" tool made all the users member of the audio group when the accounts were created since I had the "use audio" box checked.

If only it was that simple.

--wally.

---

