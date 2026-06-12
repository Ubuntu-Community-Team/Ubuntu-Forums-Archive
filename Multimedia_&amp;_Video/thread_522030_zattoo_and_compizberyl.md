---
title: "zattoo and compiz/beryl"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by Buendia on 2007-08-10
Hi,

I have installed zattoo 32 on feisty 64 and I keep getting flickering video when compiz is on. Any ideas how to solve this?

---

### Post by nemesis7 on 2007-10-02
Hi,

Honestly I have no idea but I am particularly interested to know how did you install zattoo on x64 :

I cannot make it run .

zzz@X2:~$ zattoo_player 
zattoo_player: error while loading shared libraries: libgnomeui-2.so.0: wrong ELF class: ELFCLASS64
zzz@X2:~$ uname -a
Linux X2 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux
zzz@X2:~$

---

### Post by nemesis7 on 2007-10-08
Hi ,

I found the solution using a chroot 32 bits of feitsy :
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

Zattoo 32 bits runs perfectly.

---

### Post by Buendia on 2007-10-17
Yeah it does run in chroot, even without that, you may want to use getlib to download all the required libraries automatically.

The problem is that zattoo does not like compiz/beryl. It is very flicky under this environment.

---

### Post by stuckoverflow on 2008-06-25
Well, i have the same problem, the thread is quite old but i was wondering if somebody could make zattoo work under compiz. I have to disable compiz before i can watch tv.

Thanks in advance.

---

### Post by NilsHG on 2008-06-25
what video card do you have? zattoo runs fine on my desktop with nvidia +compiz and i have the flickering problem on my notebook with radeon mobility 9600, radeon driver +compiz.

---

