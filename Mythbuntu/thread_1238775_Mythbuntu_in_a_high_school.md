---
title: "Mythbuntu in a high school"
date: 2009-08-12
forum: Mythbuntu
---

### Post by HW_Hack on 2009-08-12
While I'm still working on getting my first setup to work at home --- I started to wonder about doing a setup at our school.

I could see a dedicated back-end server and then 2 or 3 lightweight client front-ends on carts. 

A teacher sets up a recording - then later in the week checks-out a front-end client and rolls it to the classroom. Hooks it up to the net - connects video out to a projector - boots the system. Plays the recorded material.

Now one question is will the client (thats been sitting shut down for a day or 2) automatically connect and find the back-end server ? 

Anyone have any idea on how long a public school can store content from non-premium sources (ABC - CBS - PBS - etc.)

---

### Post by Prospero2006 on 2009-08-12
Hello,

I run a bunch of Ubuntu machines on my campus that are used for everything from student workstations to media storage. 

Here's what I suggest:
-Your campus probably dynamically assigns ip addresses to computers.
(Mine does)
-With your Mythbuntu server, find a subnet that's not being used and statically assign it there so it doesn't conflict with anything else in the building/hub. 
-Now, the client will always know where to look if you configure it.

?

Josh

---

### Post by HW_Hack on 2009-08-13
Glad to hear what you are doing - yeah we use DHCP and I'll have to request a static IP for this machine.

---

