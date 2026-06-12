---
title: "Keyring Password Prompt Won't Allow Remote VNC Access"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by rollin77 on 2011-11-11
Hi all,  I have a PC running Ubuntu 10.04 that I'm trying to setup as a headless system I can remote into.  Currently the PC is setup to auto login to the desktop without a password when powered on, I need this because VNC won't work until it is logged in.  The only problem I'm having is every time I VNC into the machine it asks for the keyring password on the remote PC before accepting the VNC session, so I have to physically walk over to the remote PC, enter the keyring password, then go back to the PC I'm remoting from.  

This process seems to kill the whole concept of a remote session.  I've read through some other threads with this same problem but can't find a definite solution.  Some solutions are to remove the keyring completely, but this doesn't sound very secure.  I don't want to remove password requests for root privileges, but only for VNC sessions so I can remote into this PC without having to physically walk over to the remote PC.

I can't leave the PC on continuously either, [S]eventually I will[/S] I just bought a switched PDU that I can power the PC on/off remotely.  The idea is for everything to be operated from a completely remote location.  I also can't use the server version of Ubuntu either as what I need to do is mostly graphical.  

How can I best setup this PC as a truly remote PC without sacrificing security?

---

### Post by rollin77 on 2011-11-12
bump?

---

### Post by rollin77 on 2011-11-18
I still can't remote into this PC because of this problem.  Does anybody know how to fix this keyring issue???

---

