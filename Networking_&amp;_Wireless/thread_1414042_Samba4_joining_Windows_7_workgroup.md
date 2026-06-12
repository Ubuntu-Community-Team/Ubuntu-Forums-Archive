---
title: "Samba4 joining Windows 7 workgroup"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by shmk on 2010-02-23
Hello, I'm having some problem to add my Ubuntu 9.10 to a workgroup managed by Windows 7.

Windows 7 is managing the workgroup and has other 2 Windows PCs connected to him.

I'm trying to add to that workgroup also my Ubuntu 9.10 PC using Samba4, but from Ubuntu the Windows network is not shown inside networks and from Windows I can't see my Ubuntu.

Do you have any suggestion?

---

### Post by Jony35359595 on 2011-05-12
Hi all.
Still no solution for this?

---

### Post by spmcgann on 2012-05-21
Windows 7 uses 128 bit encryption but Ubuntu can only handle 40 bits.

Under advanced sharing options, go to security and change the 128 bit to 40 bit then restart windows computers. Do this on all Win7 computers.

---

