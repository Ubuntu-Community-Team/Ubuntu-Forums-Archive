---
title: "Help with Netcat"
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by MrCrumbs on 2012-09-12
Hi all,

I know my question is regarding Windows and not Ubuntu, but I simply need people who know Netcat pretty well and I'm guessing here is a good place for that. So on with my question.

I'm doing some research, and I was playing around with netcat on a WinXP VM but I can't seem to get something.

I tried this command:

nc -l -p 80 -e "c:\notepad.exe"
(I copied notepad.exe to c:\ folder)

But what happens is simply that netcat closes and does nothing. It does connect, because if I leave the command without the "-e" parameter like this:

nc -l -p 80

It does show me an output. But when I add the "-e" and any program (I tried cmd, and others) - nothing will execute, and netcat simply shuts down.

Any ideas?
Thanks,
Jonathan

---

### Post by Bucky Ball on 2012-09-12
*Thread moved to** Networking & Wireless***

---

### Post by MrCrumbs on 2012-09-12
OK I will, but netcat isn't a Windows app, that's why I posted here. It's very popular in linux OS..

---

### Post by Bucky Ball on 2012-09-12
> **MrCrumbs said:**
> OK I will, but netcat isn't a Windows app, that's why I posted here. It's very popular in linux OS..

Oh, I see. But you're using it in Win? If so, Linux doesn't really work like Win so not sure what help you'll find. But again, good luck and I hope you get somewhere with it.

I've had a look and will move this to Networking. ;)

---

### Post by MrCrumbs on 2012-09-12
Thanks Bucky Ball, I understand that things are different, but I'm hoping someone will know enough about it to advise.

---

