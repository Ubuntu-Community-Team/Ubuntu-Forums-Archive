---
title: "How to control fan speed when running text only mode"
date: 2011-08-23
forum: Multimedia Software
---

### Post by fokuslee on 2011-08-23
I often run my ubuntu as SSH server only
so i stop GDM when i do that, but i found out that after i stop gnome, my ATI gpu fans spins up like crazy and sounds like a jet plane, (i have ati closed source driver installed) 
i am worried to leave the fan on like that, so i have to start a X session again. Then the fan slows down  
I would like to be able to have slow fan speed when i drop to text mode only, one is its light weight, two is for security 
Any ideas?

---

### Post by handy on 2011-08-23
If no one comes up with a simpler solution you could setup your machine so that you can startx without Gnome being called, after which you would have to call Gnome from the terminal.

Though looking at the power management section in the Ubuntu Stuff: section of the first post here:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

It looks like you are going to need to have X running to benefit PM wise.

You may miss this link in the above;- it adds some more info' re' cooling AMD/ATi cards. Not that I think it will do you any good without at least having X running:

[http://forums.amd.com/forum/messageview.cfm?catid=13&threadid=109000&messid=970779&parentid=970616&FTVAR_FORUMVIEWTMP=Single](http://forums.amd.com/forum/messageview.cfm?catid=13&threadid=109000&messid=970779&parentid=970616&FTVAR_FORUMVIEWTMP=Single)

---

### Post by fokuslee on 2011-08-24
OK i need to see how upstart works, will report to you the results

---

### Post by handy on 2011-08-25
> **fokuslee said:**
> OK i need to see how upstart works, will report to you the results

Cool. It really helps us all when people tell us what does & doesn't work. Growing the shared knowledge base is obviously what it is all about here. :)

---

