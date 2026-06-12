---
title: "not able to install application using wine"
date: 2010-03-21
forum: Multimedia Software
---

### Post by prasad.bh1 on 2010-03-21
Hello,

I have installed ubuntu 9.10 and installed wine, as I want to use VOIP packages like smart VOIP and Media Ring talk etc..
But I am not able to install them on ubuntu..

please go through the attachment.. 

please help me to install it.. I dont want to go back to widows :)

thanks for understanding and help.

wr,
prasad

---

### Post by themusicalduck on 2010-03-21
What is the problem when you try to run something in Wine?

By default, exe files don't open automatically in Wine. So if you have Wine installed already, you might want to find a .exe file, right click on it, go to Properties, Open With and select the Wine Windows Program Loader radio button. Then when you double click an exe it should load with Wine.

Otherwise, you could try running an exe file from the command line with ```
wine /path/to/exe
``` and see if any errors come up or if it runs at all.

---

### Post by prasad.bh1 on 2010-03-21
[SIZE=3]HI, later I did use this command #wine <path for exe>. This is the error ( please see the attachment )

Has anybody installed any .exe file with wine ? please tell me how to do it ?

Thank you,
wr,
prasad
[/SIZE]

---

### Post by themusicalduck on 2010-03-21
That error means that Wine is managing to load the exe but is having some problem with it.

Wine isn't a perfect clone of Windows. It's a bit hit and miss with running Windows programs. Usually you can look up how well a program would work at [http://appdb.winehq.org/](http://appdb.winehq.org/) but I can't see MediaRing there and Smart VOIP has a garbage rating, so it probably won't work.

It might be better to see if there are any native Ubuntu pieces of software to use instead.

---

### Post by prasad.bh1 on 2010-03-21
Hi themusicalduck
>>> It might be better to see if there are any native Ubuntu pieces of software to use instead.

I think you are right but please tell me if anybody knows what could be any native Ubuntu pieces of software to use instead. ? 

please I dont go back to the slowest ever OS vista ..

thanks 

wr,
prasad

---

### Post by prasad.bh1 on 2010-03-25
Hello Geeks,

well, just like empathy provides interface for IM like gmail, yahoo etc, ids. do we have any interface where we can use the VOIP provider access like smart VOIP, Rynga, media ring talk etc etc..

does anybody have any idea about this ?

wr,
prasad

---

### Post by Mark Phelps on 2010-04-13
> **Russell123 said:**
> i also have the same problem as prasad has. i don't know that how to install it. kindly give some suggestion to install.

Thanks

Read the comments provided earlier in post #4.

---

