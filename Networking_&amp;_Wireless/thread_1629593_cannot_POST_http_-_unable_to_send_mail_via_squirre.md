---
title: "cannot POST http - unable to send mail via squirrelmail"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by dudlo on 2010-11-23
I have a really weird (but consistent) problem with my Kubuntu 10.10 install: I cannot post some HTTP forms.

First off, this is a client PC problem. My squirrelmail on the server works fine. I just use squirrelmail 1.4.17 to troubleshoot the ubuntu desktop problem

I used an old (07.04) Ubuntu install which worked fine. Then I wiped the disk and installed Kubuntu 10.10 on the same hardware. Everything works but **some** HTTP post does not work (I can log in but not send mail or save draft). I noticed I cannot log in to Yahoo, for example. 

My webhosting account can display the apache access_log. When I hit the <Send> button the POST request never arrives to the web server.

I use a router (Dlink DL-604) behind a DSL modem and ooma box. There is a Windows 7 PC and a Kubuntu PC connected to the router. I can use squirrelmail just fine from the Windows PC.

I tried several steps:
- reinstalled Kubuntu
- installed Firefox and Chromium (on top of reconq)
- ran from a CD on my other (Windows 7) PC
- installed Wireshark and compared the traffic (but was unable to pinpoint a problem)

The result was the same: the <Send> button just keeps waiting; the POST request never makes it to the web server.

This sounds (and is) scary and suspect. The fact that the "demo" Kubuntu install (from the CD on my other Windows PC) using the reconq exhibits the same problem on a totally different hardware leads me to believe this may be related to Kubuntu. For example, I had to type this very message on the Windows PC as I could not post it on the forum from my Kubuntu box.

I'd appreciate any suggestions or pointers.

---

### Post by SeijiSensei on 2010-11-24
Are you starting with a new home directory, or did you preserve your old home directory from 7.04?  If the latter, try moving $HOME/.mozilla to .mozilla.old and restarting firefox.  It will build a new configuration for you.  Maybe that will help?

I've never had this problem, and I've been using 10.10 since pre-beta days.  

Any caching proxies in between you and server like squid?

I'm rather clutching at straws here since I've never seen this myself.

---

### Post by dudlo on 2010-11-24
Thank you for the follow-up. No, there was no old home directory. I wiped the disk.
 
It is strange for sure. I am thinking this may be a combination of Kubuntu and hardware (router, DSL modem). The frustrating part is that I do not know how to debug the problem.
 
Thank you,
Dudlo

---

