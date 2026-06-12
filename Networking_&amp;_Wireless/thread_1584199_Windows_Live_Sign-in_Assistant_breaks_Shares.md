---
title: "Windows Live Sign-in Assistant breaks Shares"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by Tamperous on 2010-09-28
I am unable to connect to the shares on my Windows 7 box after installing windows live messenger with its sign in assistant which is now integrated into the core application as of the upcoming 2011 version. 

I am running Karmic and the LibSMBClient version is 2:3.4.0-3Ubuntu5.7


The exact cause has been documented in the following links and has been patched by the Samba team as of July (second link).


[https://bugs.launchpad.net/samba/+bug/458637](https://bugs.launchpad.net/samba/+bug/458637)


[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)


Has this issue been patched in any version of Ubuntu? If so how can I get a patched binary. Alternately is there any way I can compile a patched binary myself. I'd like to get my network working again. I've been using FTP to move stuff to my Windows box since this problem occurred.

---

### Post by kreggz on 2010-09-29
Looks like you might have to use the workaround until you can get this via apt-get:

Thierry Carrez wrote on 2010-03-18:
until upstream/someone comes up with samba patches to support Windows-Live-sso-powered shares, the workaround is to ask your colleague to disable the Windows Live Sign-In assistant on his Windows 7 machine.

or subscribe to the bug report you posted and ask them for assistance.

---

