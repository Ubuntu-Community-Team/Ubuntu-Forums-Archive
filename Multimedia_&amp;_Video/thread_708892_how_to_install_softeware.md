---
title: "how to install softeware"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by dascabins on 2008-02-26
how does one install software for it to work on ubuntu

---

### Post by fedex1993 on 2008-02-26
like what do you mean like what software do you need to install?

---

### Post by santiagoward2000 on 2008-02-26
> **dascabins said:**
> how does one install software for it to work on ubuntu

Hi!
Well, there are many ways. The first and easiest is through its repositories. You can go to **System>Add/Remove...** and look in there.
There are some applications that may not appear there. In that case you may look in **System>Synaptic Package Manager**.
If you know the name of the package you want to install, you may open a console and type:
```
sudo apt-get install name-of-the-package
```
Remember the name of the package may be a little different from the name of the application.
Some developpers may distribute **.deb** files on their pages (for example Frostwire does that). These are installed by simply double-clicking on them.
Others may build their own repository for Ubuntu. In that case you'll need to go to **System > Software Sources** and add their repository under the **Third Party Software** tab. You may need to add some key, but their page should tell you how. Then, open Synaptic and look for the application you wanted.
Finally, the hardest way would be compiling from source, but that may vary from program to program, so I won't explain it here.
I hope I covered your question. If you have any doubt, just ask!
Cheers!

---

