---
title: "rdesktop connection to Windows server fails"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by earlycj5 on 2012-04-20
Hi all, I just upgraded my workstation from 11.04 to 11.10, I know, a bit behind.

Now I'm thinking maybe I shouldn't have.

I've been using the rdesktop connection to connect to my Windows server in my lab with no hiccups whatsoever.

However, now that I've upgraded to Oneiric, my rdesktop connection just plain doesn't work and I can't figure out why.

I had a small script written that I just used to launch it from the terminal when needed.

```

#!/bin/bash
rdesktop -a 16 -g 3840x1028 IP.ADDRESS

```

So I know that didn't change on the upgrade.  However now when I try to use it, all I get is a black screen.

Anyone have any insight?

---

### Post by earlycj5 on 2012-04-20
Ok, it may just be coincidental, I cannot get my Windows 7 laptop to connect now, either.  I'll investigate further on the server side of things.

---

### Post by earlycj5 on 2012-04-20
Definitely server side, sorry for this, totally coincidental.

Marked as solved.

---

