---
title: "Another Broken Nvidia driver"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by chucklechops on 2007-01-16
So my nvidia driver suddenly fails to load, presumably as a result of a kernel update when I wasn't paying attention. When I try reinstalling with

> sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx

I get the message

> The following packages have unmet dependencies:
nvidia-glx: Depends: nvidia-kernel-1.0.9629

When I try to install said package I get:

> Package nvidia-kernel-1.0.9629 is a virtual package provided by: <blank>
You should explicitly select one to install.

This is a bit beyond me. Anyone?

TIA

---

### Post by chucklechops on 2007-01-18
:confused: Bump:confused:

---

### Post by _asc_ on 2007-01-23
Hi,

I have the same problem. Have you found a solution yet?

---

### Post by chucklechops on 2007-01-23
> **_asc_ said:**
> Hi,

I have the same problem. Have you found a solution yet?

I posted this in the beginner forum and got some replies.

[http://www.ubuntuforums.org/showthread.php?t=341855](http://www.ubuntuforums.org/showthread.php?t=341855)

Basically I commented out all the repos except for the official ubuntu ones in sources.list then did

> sudo apt-get update
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx

..and everything was hunky dory.

Hope this helps.

---

### Post by _asc_ on 2007-01-24
Yes, that solved my problem. Thank's a lot!

---

