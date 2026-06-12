---
title: "send message prompt from ubuntu to vista"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by KORPAH on 2010-04-16
I was wondering if it was possible to send a message pop up to vista from my ubuntu. I have researched a little but there wasn't enough clarity on the issue. 

Thanks.

PS . I know you can use smbclient -M but I'm shaky on the syntax.

---

### Post by 2hot6ft2 on 2010-04-16
Welcome to the forum.
You might take a look at kopete, you can find it in
System > Administration > Synaptic Package Manager
or install it like this
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install kopete
```
You will have to enter your password which wont be displayed just type it in and hit Enter.
Then it will be in
Applications > Internet > Kopete

See pic. below.

---

### Post by KORPAH on 2010-04-16
Thanks but that's not what I'm looking for. 

I want to know unix commands that will get the job done.

---

### Post by Iowan on 2010-04-16
[linpopup]("http://linpopup2.sourceforge.net/")
Also check **man write**.
**man wall** - more of a message broadcaster.

---

