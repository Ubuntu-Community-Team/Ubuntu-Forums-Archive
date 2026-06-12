---
title: "LMMS and libasoun2 missing"
date: 2008-07-11
forum: Multimedia Software
---

### Post by LK_gandalf_ on 2008-07-11
Hi, I have Kubuntu 8.04 64 bit, I have downloaded the amd64.deb of lmms, but when I try to install it says that libasoun2 is missing.
So, i have installed it from adept, but nothing change!!
What can i do?
Thank you

---

### Post by LK_gandalf_ on 2008-07-12
up

---

### Post by LK_gandalf_ on 2008-07-13
up :(

---

### Post by Claus7 on 2008-07-13
Hello,

are you sure that the name of the library is the one you specify and not libasound2?

I also wanted to install a program, not in kubuntu but in ubuntu, and even though I had this library, the deb package I wanted to install said that it was missing. In order to avoid that, I installed the source code of this program and I had no problem at all. So I suggest you to do the same.

Regards!

---

### Post by LK_gandalf_ on 2008-07-17
the problem is that the compile fails while makings, it gives a lot of errors but i't difficult to determine the error or how to fix it

So i think the best is to install the deb...but boh...the problem is still here with this libasound.

---

### Post by Claus7 on 2008-07-17
Bona Sera,

I think that you will get errors, while you execute configure, in order to see what dependencies you are missing. Now libasound library is an important one to one's system. If you stick with deb then do:
man dpkg to see the option you get in order to install the deb package with different configure options. I should suggest you to type dpkg -configure file.deb to see what it suggest you. 

I do not know, yet I suppose that you could give to the deb file to understand where this libasound library is. If you cannot, then you should see the errors that the source file gives you and try one by one to solve them.

Regards!

---

### Post by markbuntu on 2008-07-17
When I installed xmms I needed the libasound2 from Launchpad to fix a deb issue on hardy64. The one in the repos did not work. It was kind of a circular confused little time there but it ended up working. Something like dpkg deb failure, get the debs, dpkg debs, force deb packages, remove some of them, resume, success. It was really weird but it worked.

I got the libasound2 to from a link at the Launchpad page that listed the debs for the xmms package. You might want to try that but from where you got the LMMS.

---

