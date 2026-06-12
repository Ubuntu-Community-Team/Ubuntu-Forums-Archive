---
title: "Compiling ndiswrapper from source..."
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by icanfly0307 on 2009-01-30
Hi,
   I've compiled my own custom kernel and I want to install the ndiswrapper module into it. However, I get a bunch of errors like "too few arguments to compile" when I try compiling from source. I know that it's a bug, but none of the other packages, even the old ones work.

So is it possible to install the ndiswrapper module into the kernel like Debian does? Debian uses module assistant commands like:

m-a prepare
m-a a-i ndiswrapper

So would this work in Ubuntu the way it does in Debian? Thanks for your help...

---

### Post by Ayuthia on 2009-01-30
Ubuntu and Debian are usually the same.  However for ndiswrapper, it is a source compile that installs it by doing "sudo make install".

Are you using ndiswrapper-1.54?  The older versions won't compile without a patch.

---

### Post by icanfly0307 on 2009-01-30
Has ndiswrapper-1.54 been released? I'm using ndiswrapper 1.53 because it used to be the latest stable and I had it downloaded and ready on my computer, so I thought I would use it. So you're saying that the errors have been fixed in 1.54, right? Thanks.

---

### Post by Ayuthia on 2009-01-30
Yes, it is out.  I have been able to compile it in Gentoo under a 2.6.28.2 kernel without any patches.  I did not try it out with 2.6.27, but I am sure that it should compile fine.

---

### Post by icanfly0307 on 2009-01-31
The kernel that I'm going to compile is actually the 2.6.28.2 version. So, I guess it should work. I'll post back once I try it. Thx! :)

---

