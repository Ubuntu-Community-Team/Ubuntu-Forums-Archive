---
title: "export DISPLAY does not work anymore"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by DJ_Cyberdance on 2006-06-06
I am running some tools from other machines (in fact these are UML instances but that does not matter...). That worked fine when I was using Debian sid but now I just switched my host system to Ubuntu 6.06. When executing some java tool I receive the following error message:

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using '192.168.200.2:0.0' as the value of the DISPLAY variable.

192.168.200.2 is the address of the host system that can be pinged. I executed xhost + on my new Ubuntu system. As mentioned before, when Debian was running the application was executed and the windows showed up on the host system. But now in Ubuntu I get this weird error message. Is there anything more required to allow other clients to connect to my box?

---

### Post by keeb on 2006-12-05
Make sure the server sshd_config file allows it.

---

### Post by bjd on 2006-12-05
X is probably not listening for network connections because of security reasons. The usual way is to use X forwarding facilities of the ssh client
(see -X or -Y option in man ssh).
If you want to enable network connections anyway, edit /etc/X11/xinit/xserverrc and remove the *-nolisten tcp* part.

---

### Post by zammtronic on 2007-10-18
> **bjd said:**
> X is probably not listening for network connections because of security reasons. The usual way is to use X forwarding facilities of the ssh client
(see -X or -Y option in man ssh).
If you want to enable network connections anyway, edit /etc/X11/xinit/xserverrc and remove the *-nolisten tcp* part.

I added this line (I am having the same difficulty), and I still cannot export windows to my Feisty box.

---

### Post by dkpelder on 2007-10-22
> **zammtronic said:**
> I added this line (I am having the same difficulty), and I still cannot export windows to my Feisty box.

Zammtronic,

You may have the same issue I found that I had.  My kdmrc file (/etc/kde3/kdm) was from an older version of kdm so a new version was created in /var/run/kdm every time I started kdm.  Thus my editing in /etc/kde3/kdm/kdmrc had no effect.  Once I removed /etc/kde3/kdm/kdmrc and replaced it with the kdmrc file in /var/run/kdm, things worked better.  I could then edit that file and have my edits work.

---

### Post by zammtronic on 2007-10-22
> **dkpelder said:**
> Zammtronic,

Once I removed /etc/kde3/kdm/kdmrc and replaced it with the kdmrc file in /var/run/kdm, things worked better.

Hmm...I sounds good, but I am running gnome. Certainly there is a way to port this over.

---

