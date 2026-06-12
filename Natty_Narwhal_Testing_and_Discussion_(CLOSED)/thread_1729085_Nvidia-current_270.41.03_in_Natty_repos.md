---
title: "Nvidia-current_270.41.03 in Natty repos"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-04-14
Nvidia-current_270.41.03 is right now available also from Natty repos.
See here:
[https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.41.03-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.41.03-0ubuntu1)

There is, however, a dkms.conf addition to the one in X Updates (or xorg-edgers) and it is this one:

> 
* debian/dkms.conf{.in}:
- Prevent builds with kernels newer than the ones we ship. This
makes sense as we do not update drivers to add the support for
kernels that are not in Ubuntu. This will reduce the amount of
bug reports which are generated when DKMS fails to build modules
for unsupported kernels.


What do you say about the addition (the ones who use 2.6.39 kernel)?

---

### Post by 23dornot23d on 2011-04-14
That link is not working for me Harry 33 .....

do you have a full web address for it ........ will try it out ....

---

### Post by Harry33 on 2011-04-14
> **23dornot23d said:**
> That link is not working for me Harry 33 .....

do you have a full web address for it ........ will try it out ....

Sorry for that. Now it works.

---

### Post by dino99 on 2011-04-15
> **Harry33 said:**
> Nvidia-current_270.41.03 is right now available also from Natty repos.
See here:
[https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.41.03-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/270.41.03-0ubuntu1)

There is, however, a dkms.conf addition to the one in X Updates (or xorg-edgers) and it is this one:



What do you say about the addition (the ones who use 2.6.39 kernel)?

I understand that raison to reduce the useless bug reports but why not using ubuntu-bug to refuse these reports (not genuine package) as usual instead of creating this dkms.conf ? Wonder about the consequences on the user side. Is that means only "nouveau" will be available on newest kernels ? Dont hope so, newest kernel have to be able to run with nvidia-current of course. By the way i'm surprised that such bugs have been reported as ubuntu-bug usually detect these non genuine package. Need clarification.

---

### Post by MacUntu on 2011-04-15
Why would anyone report such bugs in the first place?

---

### Post by VinDSL on 2011-04-15
> **Harry33 said:**
> Nvidia-current_270.41.03 is right now available also from Natty repos.

There is, however, a dkms.conf addition to the one in X Updates (or xorg-edgers) and it is this one:

> * debian/dkms.conf{.in}:
- **[COLOR="Red"]Prevent builds with kernels newer than the ones we ship.[/COLOR]** This
makes sense as we do not update drivers to add the support for
kernels that are not in Ubuntu. This will reduce the amount of
bug reports which are generated when DKMS fails to build modules
for unsupported kernels.

What do you say about the addition (the ones who use 2.6.39 kernel)?

Heh!  Ignorance is bliss...

```

vindsl@Zuul:~$ sudo cat /proc/driver/nvidia/version
NVRM version: **[COLOR="Red"]NVIDIA UNIX x86 Kernel Module  270.41.03[/COLOR]**  Sat Apr  9 00:04:57 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) 

vindsl@Zuul:~$ uname -a
**[COLOR="red"]Linux Zuul 2.6.39-999-generic #201104141057 SMP Thu Apr 14[/COLOR]** 12:16:32 UTC 2011 i686 i686 i386 GNU/Linux

```

I didn't know I couldn't build it, so I did.  :D

---

### Post by dino99 on 2011-04-15
> **VinDSL said:**
> Heh!  Ignorance is bliss...

```

vindsl@Zuul:~$ sudo cat /proc/driver/nvidia/version
NVRM version: **[COLOR="Red"]NVIDIA UNIX x86 Kernel Module  270.41.03[/COLOR]**  Sat Apr  9 00:04:57 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) 

vindsl@Zuul:~$ uname -a
**[COLOR="red"]Linux Zuul 2.6.39-999-generic #201104141057 SMP Thu Apr 14[/COLOR]** 12:16:32 UTC 2011 i686 i686 i386 GNU/Linux

```

I didn't know I couldn't build it, so I did.  :D

by the way you dont get anything new till next rc

---

### Post by VinDSL on 2011-04-15
> **MacUntu said:**
> Why would anyone report such bugs in the first place?
Not sure which bugs we're talking about...

I reported a bug in 2.6.39 rc1, and they were all over it -- fastest response I ever got.

What bugs are you referring to?  I'm a little sleepy and thick-headed, right now...  ;)

---

### Post by VinDSL on 2011-04-15
> **dino99 said:**
> by the way you dont get anything new till next rc
You can't prove a negative, so I'll be nice, and take your word for it...  :)

---

### Post by dino99 on 2011-04-15
> **VinDSL said:**
> Not sure which bugs we're talking about...

I reported a bug in 2.6.39 rc1, and they were all over it -- fastest response I ever got.

What bugs are you referring to?  I'm a little sleepy and thick-headed, right now...  ;)

reporting bug against those early rc is useless, thats why they want to avoid them now

---

### Post by dino99 on 2011-04-15
> **dino99 said:**
> I understand that raison to reduce the useless bug reports but why not using ubuntu-bug to refuse these reports (not genuine package) as usual instead of creating this dkms.conf ? Wonder about the consequences on the user side. Is that means only "nouveau" will be available on newest kernels ? Dont hope so, newest kernel have to be able to run with nvidia-current of course. By the way i'm surprised that such bugs have been reported as ubuntu-bug usually detect these non genuine package. Need clarification.

@Harry
please can you elaborate, whats the point ?

---

### Post by Harry33 on 2011-04-15
> **dino99 said:**
> @Harry
please can you elaborate, whats the point ?

You mean what is the point in implementing this obiously debian policy patch (dkms.conf)?
Well to be honest, I do not follow the logic behind this.
If the patch works, it should prevent dkms from building the "non-ubuntu" kernel module (nvidia-current.ko). That would make it hard to use that driver with such kernels.
Basicly it seems Canonical does not want to publish a driver update, which also supports a non-ubuntu kernel.
This is a restrictive policy in my opinion. It means less freedom of choice.
That, on the other hand, is something I do not accept.

---

### Post by dino99 on 2011-04-15
> **Harry33 said:**
> You mean what is the point in implementing this obiously debian policy patch (dkms.conf)?
Well to be honest, I do not follow the logic behind this.
If the patch works, it should prevent dkms from building the "non-ubuntu" kernel module (nvidia-current.ko). That would make it hard to use that driver with such kernels.
Basicly it seems Canonical does not want to publish a driver update, which also supports a non-ubuntu kernel.
This is a restrictive policy in my opinion. It means less freedom of choice.
That, on the other hand, is something I do not accept.

that is what i've understood too, thats weird, but i've not updated that new package, will wait because i want to continue testing new kernel rc with nvidia (so use x-swat previouly published), not "nouveau" fallback.

Thanks for your time, have a good WE

---

### Post by Harry33 on 2011-04-15
> **dino99 said:**
> that is what i've understood too, thats weird, but i've not updated that new package, will wait because i want to continue testing new kernel rc with nvidia (so use x-swat previouly published), not "nouveau" fallback.

Thanks for your time, have a good WE

Thanks for you too Dino, and a nice weekend.

I found this similar or identical note regarding the fglrx update of today:

> 
Changelog
fglrx-installer (2:8.840-0ubuntu2) natty; urgency=low
  * debian/dkms.conf.in:
    - Prevent DKMS builds with kernels newer 2.6.38.


---

