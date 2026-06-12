---
title: "VMWare Workstation in 11.04"
date: 2011-02-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by satyaas on 2011-02-14
I upgraded to 11.04 alpha.
Everything seemed to work fine except VMWare Workstation. 

When I started VMWare, it displayed the following message:

[I]Before you can run VMware, several modules must be compiled and loaded into the running kernel.

[/I]I clicked on 'install' and the following error message was displayed.

[I]Unable to build kernel module.

See log file /tmp/vmware-root/setup-1879.log for details.

```
Feb 14 23:58:21.431: app-140497418254112| Log for VMware Workstation pid=1879 version=7.1.3 build=build-324285 option=Release
Feb 14 23:58:21.431: app-140497418254112| The process is 64-bit.
Feb 14 23:58:21.431: app-140497418254112| Host codepage=UTF-8 encoding=UTF-8
Feb 14 23:58:21.431: app-140497418254112| Logging to /tmp/vmware-root/setup-1879.log
Feb 14 23:58:21.539: app-140497418254112| modconf query interface initialized
Feb 14 23:58:21.539: app-140497418254112| modconf library initialized
Feb 14 23:58:21.567: app-140497418254112| Your GCC version: 4.5
Feb 14 23:58:21.575: app-140497418254112| Your GCC version: 4.5
Feb 14 23:58:21.591: app-140497418254112| Your GCC version: 4.5
Feb 14 23:58:21.610: app-140497418254112| Your GCC version: 4.5
Feb 14 23:58:21.622: app-140497418254112| Your GCC version: 4.5
Feb 14 23:58:21.661: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.665: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.666: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.668: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.670: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.684: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.686: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.688: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.690: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.692: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.696: app-140497418254112| Your GCC version: 4.5
Feb 14 23:58:21.707: app-140497418254112| Your GCC version: 4.5
Feb 14 23:58:21.843: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.845: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.847: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.849: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.851: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.856: app-140497418254112| Your GCC version: 4.5
Feb 14 23:58:21.867: app-140497418254112| Your GCC version: 4.5
Feb 14 23:58:21.919: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.922: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.924: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.926: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:21.928: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:22.371: app-140497418254112| Trying to find a suitable PBM set for kernel 2.6.38-3-generic.
Feb 14 23:58:22.372: app-140497418254112| Building module vmmon.
Feb 14 23:58:22.394: app-140497418254112| Extracting the sources of the vmmon module.
Feb 14 23:58:22.468: app-140497418254112| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.38-3-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.5.2
Feb 14 23:58:27.818: app-140497418254112| Failed to compile module vmmon!
```



[/I]Please help me.

---

### Post by uRock on 2011-02-14
Moved to NNT&D. 

Please create threads here when using the developmental version.

Regards,
uRock

---

### Post by satyaas on 2011-02-14
Thanks uRock.. I'm a newbie here... ;)

---

### Post by rinocom on 2011-03-21
getting the same thing here...

anyone have any ideas?

---

### Post by Vigh on 2011-03-22
same problem here

---

### Post by GrzesiekC on 2011-03-22
Hi all,

I am using this kernel 2.6.38-7-generic #36-Ubuntu SMP Fri Mar 18 23:18:58 UTC 2011 x86_64 GNU/Linux with Workstation 7.1.3 on ubuntu 10.10.

I have to apply a patch from the attachment.

I found it on the VMWare forum.

Cheers
Grzesiek

---

### Post by rinocom on 2011-03-22
> Hi all,

I am using this kernel 2.6.38-7-generic #36-Ubuntu SMP Fri Mar 18 23:18:58 UTC 2011 x86_64 GNU/Linux with Workstation 7.1.3 on ubuntu 10.10.

I have to apply a patch from the attachment.

I found it on the VMWare forum.

Cheers
Grzesiek


I'm not 100% sure how this should be used.  I unpacked and:

```
$ sudo sh patch-modules_2.6.37.sh

```

to which I got:

```
[: 26: workstation7.1.3: unexpected operator
[: 27: workstation7.1.3: unexpected operator
Sorry, this script is only for VMWare WorkStation 7.1.3 or VMWare Player 3.1.3. Exiting

```

I'm running workstation 7.1.3, so I'm sure that my procedure is flawed.  Any tips?

---

### Post by GrzesiekC on 2011-03-22
> **rinocom said:**
> I'm not 100% sure how this should be used.  I unpacked and:

```
$ sudo sh patch-modules_2.6.37.sh

```to which I got:

```
[: 26: workstation7.1.3: unexpected operator
[: 27: workstation7.1.3: unexpected operator
Sorry, this script is only for VMWare WorkStation 7.1.3 or VMWare Player 3.1.3. Exiting

```I'm running workstation 7.1.3, so I'm sure that my procedure is flawed.  Any tips?

This are the sources:

[http://communities.vmware.com/thread/293321](http://communities.vmware.com/thread/293321)
[http://communities.vmware.com/message/1642135](http://communities.vmware.com/message/1642135)

One more thing. As far as I remember I uninstantiated VMware and started with fresh installation.

Cheers

---

### Post by rinocom on 2011-03-22
actually, I just did a 
```
uname -a
```
and realized that I'm on 2.6.38-7, so now I'm off to find the patch for this kernel!

---

### Post by GrzesiekC on 2011-03-22
> **rinocom said:**
> actually, I just did a 
```
uname -a
```and realized that I'm on 2.6.38-7, so now I'm off to find the patch for this kernel!



No you are not. Check my kernel version ;-)

---

### Post by rinocom on 2011-03-22
Here's the real culprit, me thinks.

[http://communities.vmware.com/thread/304307?start=0&tstart=0](http://communities.vmware.com/thread/304307?start=0&tstart=0)

---

### Post by Vigh on 2011-03-25
I think VMware are going to try to release a patch for kernel 2.6.38-7 soon. I have submitted a technical ticket.

---

### Post by ayates on 2011-03-28
There is a workaround posted now at: [http://communities.vmware.com/thread/304307?start=0&tstart=0](http://communities.vmware.com/thread/304307?start=0&tstart=0)

---

### Post by monemihir on 2011-04-07
Had the same issue with 7.1.3

They have released a newer version 7.1.4...Just download, the problem has been fixed apparently cos i havent seen that error pop up again yet !!

---

