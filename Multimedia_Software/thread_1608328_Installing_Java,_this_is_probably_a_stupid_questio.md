---
title: "Installing Java, this is probably a stupid question."
date: 2010-10-28
forum: Multimedia Software
---

### Post by helios16v on 2010-10-28
I'm on the Java site and it gives instructions on how to install Java.

> **To install the Linux (self-extracting) file**
Follow these instructions:
1. **Change the permission of the file you downloaded to be executable.**
Type:
chmod a+x jre-6u<version>-linux-i586.bin

I did this but I obviously changed <version> to 22 which is the version I downloaded.

This is what I get in terminal when I did this..
> toshiba@toshiba-Satellite-A100:~$ chmod a+x jre-6u22-linux-1586.bin
chmod: cannot access `jre-6u22-linux-1586.bin': No such file or directory

What am I doing wrong?

---

### Post by yabbadabbadont on 2010-10-28
> **helios16v said:**
> What am I doing wrong?

Trying to install it from outside of the repositories.  :D

If you are using Gnome, System->Administration->Synaptic Package Manager.  Then search for sun.  You have to enable the "Partner" repository though.

---

### Post by helios16v on 2010-10-28
Oh, I got it now, I just forgot to change the directory to my downloads folder haha :P

---

### Post by helios16v on 2010-10-28
> **yabbadabbadont said:**
> You have to enable the "Partner" repository though.

Explain, so many things came up when I typed in Sun

---

### Post by yabbadabbadont on 2010-10-28
Search for sun-java6.  If nothing comes up then you will need to enable the partner repository.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

---

### Post by helios16v on 2010-10-29
Thank you very much, it just finished installing and the Java site confirmed its correctly installed and working properly. MUCH easier then what I was doing.

Credit to YabbaDabbaDont :)

Thanks again
-Ben

---

