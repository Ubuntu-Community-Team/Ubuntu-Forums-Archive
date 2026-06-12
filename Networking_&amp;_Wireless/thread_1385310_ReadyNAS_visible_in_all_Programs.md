---
title: "ReadyNAS visible in all Programs"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by rob_c on 2010-01-19
Hi,
Yet another new convert to Ubuntu. So far so good...
My current problem is this.

I have a ReadyNAS Duo on my network with a USB hard drive hanging off that.
I can navigate to them through Places etc but I cannot select them from some of the applications that I have installed. e.g. I can open files on them from GIMP but not from EasyTAG - which cannot 'see' the Network at all.

Any help is greatly appreciated.

Rob

---

### Post by elliotbeken on 2010-01-19
this is a touchy subject there are a few posts that are simalar but i totally see what you mean i find it just easyer to create a launcher and then copy the files to a local drive and use them from there

---

### Post by Morbius1 on 2010-01-19
When you connect to the NAS, a mount point will be created at:

**/home/user_name/.gvfs**

See if your application can find /home/user_name/.gvfs

And don't forget the "." in front of the gvfs

---

