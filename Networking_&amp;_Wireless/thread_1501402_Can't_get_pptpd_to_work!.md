---
title: "Can't get pptpd to work!"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by lacertus on 2010-06-04
Hi

I'm having trouble setting pptpd up for ubuntu10.04-minimal on my VPS.

I've used this guide: 

[INDENT][http://www.vmcolonel.net/?p=19](http://www.vmcolonel.net/?p=19)[/INDENT]

But my Mac won't connect. pptpd is running.

There's no logs - not even a /var/log/syslog - why is that?

Here's my configs

[INDENT]pptpd.conf - [http://pastebin.com/C4vpJBq9](http://pastebin.com/C4vpJBq9)
pptpd-options - [http://pastebin.com/aTUmApaL]("http://pastebin.com/aTUmApaL")[/INDENT]

edit:Sorry for bad title.

---

### Post by lacertus on 2010-06-04
So now i installed syslog. I get this error:

Jun  4 13:22:53 vps pppd[3627]: Sorry - this system lacks PPP kernel support

When i run modprobe...

root@vps:/var/log# modprobe ppp
FATAL: Could not load /lib/modules/2.6.18-164.15.1.el5.028stab068.9/modules.dep: No such file or directory

How do i install PPP kernel support?

---

