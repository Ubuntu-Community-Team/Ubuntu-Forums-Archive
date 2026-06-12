---
title: "Allowing Specific Program to Access Router"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by mthalis on 2009-05-05
Hello...

Please help me with this... I just need some expert's advice. I have read forums regarding this topic but unfortunately it wasn't sufficient.

How is it possible to communicate to a router, a CISCO router to be specific, using a  program instead of the hyperterminal?

I'll really wait for your reply...
Thank you for your help.

---

### Post by mthalis on 2009-05-05
Doing this type a program what is the suitable language.....

---

### Post by Mike'sHardLinux on 2009-05-05
Hi.

If I understand you correctly, the type of program you want to use is sometimes called a com or comm program. You can use CuteCom, which is in the repositories, I believe.

---

### Post by cariboo on 2009-05-06
I assume you are trying to connect to the router via a serial port, try minicom, it is in the repositories.

---

### Post by mthalis on 2009-05-06
Thank for helping me but what i really need is write a program that has user interface and using that interface access router change it configuration etc..Is it possible to write such a program?if can what is the suitable and easy language.

Thank you

---

### Post by loell on 2009-05-06
to write a program like that you can use python, pygtk for your user interface and python-serial for serial communication.

good luck in trying.

---

### Post by mthalis on 2009-05-06
Can you give some hints? like reference sites, that is great help for me.

---

### Post by loell on 2009-05-06
googling those would have  yield this

[http://www.pygtk.org/docs/pygtk/]("http://www.pygtk.org/docs/pygtk/")

[http://pyserial.wiki.sourceforge.net/pySerial]("http://pyserial.wiki.sourceforge.net/pySerial")

---

