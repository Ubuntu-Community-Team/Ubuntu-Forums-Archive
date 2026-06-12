---
title: "Java chat"
date: 2008-05-08
forum: Multimedia Software
---

### Post by Gouz on 2008-05-08
Greetings all

I have installed java 1,6 Sun and 1,7 IcedTea but I am having a problem with a java chat. (Digit Chat)
But the log in and apparently the java chat can't log.

At the place were the log in box is I see a gray colored box (like when something is there but not loaded)
I have tried Firefox and Opera but nothing. And both Sun java and IcedTea

Any ideas?

Thanks Gouz

---

### Post by apoth on 2008-05-08
Is digit chat an application or an applet?

If it's an application try running this in a terminal before running the application:

export AWT_TOOLKIT=MToolkit

---

### Post by Gouz on 2008-05-08
DO I just past it the terminal or it has to be in a directory?

---

### Post by Sef on 2008-05-08
Are you running the 32-bit or 64-bit Ubuntu?

---

### Post by Gouz on 2008-05-09
hello 

64-bit

btw I used

gedit ~/.bashrc
and added
export AWT_TOOLKIT=MToolkit at the beginning.

but still it is not working.

---

### Post by anthony2010 on 2008-06-27
Hi there.

Im also running 64 bit ubuntu (8.04) and have exactly this same problem. A greyed out chat applet.

Just cant figure out whats needed. I downloaded everything that seemed relevent in Synaptic but still no joy.

Did you ever resolve this in any way?

Kind regards.

Anthony.

---

