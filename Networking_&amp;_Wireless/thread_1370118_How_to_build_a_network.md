---
title: "How to build a network ?"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by Mongao on 2010-01-01
Hi friends,

I have two computers wired connected to a Linksys router, starting from scratch, I have formatted both computers and installed, on computer A, both Ubuntu 9.10 and Windows 7, on computer B, just 9.10.

From the Windows 7 environment on computer A, I asked windows to set up a home network, it seems to have done everything, gave me a password that should be used somewhere on computer B to allow access to computer A.

On both computers running Ubuntu, I installed Samba (I think...), edited the smb.conf file accordingly.

what happens:

from computer B, when trying to access the shared folder on computer A running windows, it says that "Ubuntu can`t mount windows share..." (or something like that);

when running 9.10 on both computers, one doesn`t see the other, it seems that 9.10 on both computers don`t identify the existence of a network.

Do I have to set up a network on both computers running 9.10 ?

When windows 7 created my network, did it write something onto the router chip ? I accessed the router through 192.168.1.1, I haven`t seen anything particularly identifying that there is a "workgroup" network or something like that.

Should I set up two networks, one for windows + Ubuntu, and the other for Ubuntu + Ubuntu ?
Isn`t Ubuntu user friendly when creating networks ? Why don`t the shared folders see each other ?

Can someone give me basic instructions please on how to create a network with both computers running Ubuntu ? Do I have to care about Samba in this scenario ? Do I have to edit the smb.conf file when Windows is not involved at all ?
Why does Ubuntu mention "can`t mount Windows share" when both computers are running 9.10 ?

Thanks,
Mongao

---

### Post by mkoehler on 2010-01-01
Have you taken a look at these tutorials?

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Let us know if you have any problems that these two articles don't fix.

---

### Post by Mongao on 2010-01-01
> **mkoehler said:**
> Have you taken a look at these tutorials?

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Let us know if you have any problems that these two articles don't fix.

Thanks, the first part is OK ! I have followed the first link and the Windows computer now SEES my Ubuntu computer - OK !

But the other problem hasn`t been solved, the Ubuntu computer DOES SEE the shared folder in the Windows computer, but when I try to open it, it says :"failed to mount windows share"

Seems like an easy thing to solve, as Ubuntu does see the shared folder !

Any guess please ?

and how to proceed when BOTH computers run 9.10 ?

Thanks,
Mongao

---

### Post by Iowan on 2010-01-02
That second link should help solve SMB (AKA Windows) sharing problems. It helps if you know the host name, path, and share name. Not exactly browse and click, but I suspect you'd be happy with any connection at this point.

---

