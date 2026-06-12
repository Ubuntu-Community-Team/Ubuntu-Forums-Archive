---
title: "Private shared folders?"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by Saidear on 2010-02-24
I want to create three 'private' document folders on a networked Ubuntu installation.

User A (me)
User B
User C

All computers are running XP aside from my server.  Users B/C share 1 login on 1 computer, while I have my own seperate.  I want to set it up so that they all see a 'document' folder, but when they login, they only see their documents, not someone else's.

Is there a way to setup that their 'home' folder that is created as soon as i add them is shared, but only 1 shared connection shows up?
IE: They don't see 3 seperate shared 'home' folders, but only 1.  And which one that is, is determined after they give the password/username associated?

I did 'share' a folder via the nautilus GUI that did not give all access to everyone, but when trying to login, it gives me an error about only 1 person being logged in at a time. I've attached an image of the error. I did try logging in via my usual Ubuntu account info.

---

### Post by ndefontenay on 2010-02-24
Hi.

I think that would involve a rather complexe script to switch files not supposed to be seen by B or C to invisible.

It's honestly much easier to have 3 separate homes.
What are the constraints hiding behind this requirements?

---

### Post by Saidear on 2010-02-24
> **ndefontenay said:**
> Hi.

I think that would involve a rather complexe script to switch files not supposed to be seen by B or C to invisible.

It's honestly much easier to have 3 separate homes.
What are the constraints hiding behind this requirements?

Personal preference to avoid getting the other two users confused or snoopy.  If it's something overly complex, I'm game to try something less involved.

---

