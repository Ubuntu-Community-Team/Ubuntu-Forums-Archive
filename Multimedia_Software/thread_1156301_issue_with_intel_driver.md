---
title: "issue with intel driver"
date: 2009-05-11
forum: Multimedia Software
---

### Post by graphicsxp on 2009-05-11
Hi,

I have installed ubuntu on my Acer aspire 5600 laptop. It has an Intel graphic card.

It used to work great with Mandriva 2009, with full 3D acceleration, I could even use compiz with no issues. But on Ubuntu I had to disable all effects, and even that, it remains quite sloppy... I am in max resolution though (1280*800).

How can I solve this issue ? Is there a driver I can download ?

Thanks

---

### Post by binbash on 2009-05-11
[http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html](http://www.ubuntu-inside.me/2009/04/how-to-boost-your-intel-cards.html)

---

### Post by graphicsxp on 2009-05-11
Thanks for the link. This seems rather complicated though :( I don't want to install a new kernel, it's kind of overkill.
I was hoping just updating the driver would be enough.

How can I check the version of my drivers?

---

### Post by nilarimogard on 2009-05-11
You could try [these drivers]("http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html").

---

### Post by graphicsxp on 2009-05-11
thanks that was a useful link. I've updated my sources and can see that the drivers are installed and it;s version 2.2.7.99.1

So I guess I have latest drivers already. Not sure what to do anymore....

---

### Post by psyke83 on 2009-05-11
Did you see the sticky thread in this forum?

---

### Post by graphicsxp on 2009-05-12
No I had not seen it. 

I've followed the steps in Part A, and when I type 

sudo fixmtrr.sh

I get

/usr/local/bin/fixmtrr.sh: 1: --2009-05-12: not found
/usr/local/bin/fixmtrr.sh: 2: Resolving: not found
/usr/local/bin/fixmtrr.sh: 3: Connecting: not found
/usr/local/bin/fixmtrr.sh: 3: 91.189.90.235: not found
/usr/local/bin/fixmtrr.sh: 3: :80...: not found
/usr/local/bin/fixmtrr.sh: 4: HTTP: not found
/usr/local/bin/fixmtrr.sh: 5: Length:: not found
/usr/local/bin/fixmtrr.sh: 1: Syntax error: Unterminated quoted string

any idea what this means ? Ive followed the steps one by one so it should have worked...

---

