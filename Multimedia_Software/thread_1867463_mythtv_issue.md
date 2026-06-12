---
title: "mythtv issue"
date: 2011-10-23
forum: Multimedia Software
---

### Post by treymchattie on 2011-10-23
before i get started, i have looked around the forum for similar issues but my searches havnt turned up this exact issue.

i have been setting up a HTPC running MythTV on Ubuntu 11.10 (fresh install) and when i enable my tv tuner in backend it will give me the "could not connect to backend, check ip settings bla bla bla" error immediately upon entering frontend. this only happens when the tuner is enabled in the Capture Cards section of backend. the second i delete it, i am able to open frontend  and can click on Watch TV without ever seeing the message, but obviously i cant watch tv.

i have checked my IP settings a hundred times, 127.0.0.1 and all the ports are correct. database password has been checked as well. i have verified that mysql is running, but i am not very familiar with it.

the tv tuner is a Hauppauge HVR1250 and i have verified it works in VLC.

any help would be greatly appreciated, im stumped.

---

### Post by s13_mills on 2011-10-26
Hi there,

When you were setting up the backend, did you declare a PIN number for frontends to connect? If so, try setting it to 0000 so all frontends can connect, and try again.

I have had trouble with that PIN in the past, and have found it is best to leave it at 0000 until you get everything else set up how you like it.

Cheers,

Andrew

---

### Post by praganzi on 2011-10-26
I find that often the easiest way to sort out issues like this is to install "mythbuntu setup" (or something similar).  In the "system roles" section you can ensure that it is set up correctly.

---

