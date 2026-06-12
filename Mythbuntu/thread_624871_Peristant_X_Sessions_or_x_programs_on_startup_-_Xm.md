---
title: "Peristant X Sessions or x programs on startup - Xmove?"
date: 2007-11-27
forum: Mythbuntu
---

### Post by neilneil2000 on 2007-11-27
Hi all,

I have my mythbox up and running now and it is very nice.  However I also want to use the box for torrenting.  I have installed ktorrent on the device with the web interface so people can use it and all media is downloaded on the one machine.

What I would like to happen ideally is that at boot ktorrent is automatically run.  However I can't get this to work as it requires an X environment.

If I SSH in to the box then I can run ktorrent and the web interface works etc but when i close SSH, ktorrent dies.

I have installed VNCServer and so at present I am VNCing to the box and  running the program and then closing the VNC client but this isn't a very "clean" approach.

I would prefer to be able to use SSH and make the program continue to run after disconnect.  I was wondering if Xmove would do this?

So in short:

How can I run a program that requires X at boot?
Can I use Xmove to make an X program persistant across SSH sessions?

---

### Post by superm1 on 2007-11-28
Try torrentflux instead perhaps?

---

### Post by neilneil2000 on 2007-11-29
Thanks for the idea!  I am downloading it now!

---

