---
title: "problem with OpenGL / VMD"
date: 2009-01-06
forum: Multimedia Software
---

### Post by Elya on 2009-01-06
Dear All, 

I have a graphic driver problem. I try to run Visual Molecular Dynamics (VMD) but I can not do it in graphical mode. 
When I tried glxinfo
I have got the following. 

name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

Can somebody advise me what to do? 
Thanks in advance.

---

### Post by jespdj on 2009-01-06
What video card do you have and what driver are you using?

If you don't know what video card you have, try this command:
```
lspci | grep VGA
```

Check with System / Administration / Hardware Drivers if there's a proprietary driver for your video card and enable it if it isn't yet enabled.

---

### Post by Elya on 2009-01-07
I typed a command you said and this is the result. 

lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)

---

### Post by Elya on 2009-01-07
In System / Administration / Hardware Drivers there are no proprietary drivers
Could you please suggest which driver I should install? 
Thanks in advance.

---

