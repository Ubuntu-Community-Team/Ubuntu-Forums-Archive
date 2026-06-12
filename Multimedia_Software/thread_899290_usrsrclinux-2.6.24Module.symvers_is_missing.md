---
title: "/usr/src/linux-2.6.24/Module.symvers is missing"
date: 2008-08-24
forum: Multimedia Software
---

### Post by fspade on 2008-08-24
Hello,

I am trying to install the driver **matroxdriver-x86_32-1.4.6** for a **Matrox Parhelia 128** on a **ASUS A7N8X-E Deluxe** motherborad and receive the following errors: 
**Module.symvers is missing,** and **scripts/genksyms/genksyms: not found.**

What can I do to correct that?

My search hasn't brought up any workable solutions so far. I am attaching the make.log file.

Kind regards,

Frank

---

### Post by fspade on 2008-08-24
Well, we figured it out:[PHP]cd /usr/src/linux* && sudo make scripts[/PHP]did the trick.

---

### Post by anandbabu on 2011-07-07
I am also facing the same problem...
Will you explain in detail about how you solved the issue?
Moreover, i am new in building kernel...

thanks in advance
anand

---

