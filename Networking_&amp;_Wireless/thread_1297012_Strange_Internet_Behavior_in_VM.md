---
title: "Strange Internet Behavior in VM"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by kuhlbeans on 2009-10-21
I'm running Kubuntu 9.04 in the latest version of VirtualBox with a Windows XP host.  Note that VB is using whatever custom internet connection it installs in Windows and I am behind a proxy.  

Where my problem comes in is that aptitude/apt-get cannot update from the console nor does ping work.  The strange part is that Konqueror can access the internet just fine.  For example, I can easily go to ubuntu.com but ping tells me it is an unknown host.

Is this a network settings problem in (k)ubuntu or a VirtualBox problem?

---

### Post by kuhlbeans on 2009-10-22
Got it figured out, it was not having the proxy set correctly for use from bash, which doesn't use the global KDE setting which was allowing Konqueror to work.

Solution was to add the following to .bashrc:

```
export HTTP_PROXY=http://3.51.15.29:3128
export http_proxy=http://3.51.15.29:3128
```

I believe it was the CAPS version that fixed the problem but it doesn't hurt to have both.

---

