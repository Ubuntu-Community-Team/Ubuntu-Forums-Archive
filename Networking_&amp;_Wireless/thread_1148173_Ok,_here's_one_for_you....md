---
title: "Ok, here's one for you..."
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by ioxmo on 2009-05-04
First of all, I want to say I *just* installed Ubuntu on my netbook and am a complete linux newbie.

Here's the situation.  I want to share my dial-up connection from my Windows XP computer to my netbook with Ubuntu 9.04 via crossover cable.  Now, before I installed Ubuntu, this worked fine...but now that I've installed Ubuntu, I don't know how to set it up.

Btw, I have dialup only because I live in the middle of nowhere and nothing else is available right now.  

Thanks in advance!

---

### Post by mikezila on 2009-05-04
What kind of setup were you using before?  Just the normal connection sharing that comes with Windows?  If so it should "just work", so to speak.  So long as ICS (the connection sharing) is setup on the host computer, then the connection to the netbook should work like any normal network connection.

What exact problem are you running into?

---

### Post by Iowan on 2009-05-04
I gotta admit - I haven't tried ICS on Windows (does it have DHCP server?).Does Ubuntu machine have DHCP or static address?  Check IP addresses on both machines to insure they're in the same subnet.

---

### Post by mikezila on 2009-05-04
> **Iowan said:**
> ...does it have DHCP server?...

Depends on a few things.  I think the ICS in Vista and 7 will do DHCP, but I think XP's had to be set static.  It's been a long time since I've used it though.

There are a bunch of tutorials for setting up ICS with laptops and Xbox 360s.

[Annoyances.org](http://www.annoyances.org/exec/show/ics) will has some nice guides showing how it works on various versions of Windows.  It would be a good place to start if you're having trouble.

Upon doing a quick scan, Win2k and up (maybe farther back too) all have DHCP servers as part of their ICS, so getting your netbook to work with it should be more or less plug and play.

---

