---
title: "How to remove SSL Explorer?"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by neptune on 2009-05-15
Hi,

I'm running Ubuntu 8.10 Intrepid and want to know how to remove ssl-explorer.

Not sure when I installed it, but it wasn't done through the repositories.

Thanks!

---

### Post by pauna on 2009-05-16
> **neptune said:**
> 
I'm running Ubuntu 8.10 Intrepid and want to know how to remove ssl-explorer.

Not sure when I installed it, but it wasn't done through the repositories.


If you have compiled ssl-explorer from the source yourself, you should go back to the directory where you have the source and there should be an "unistall" script or Makefile rule that will do that for you.

If you have installed a package (even if from a non-default repository), "sudo apt-get remove sslexplorer" should do the trick.

---

### Post by neptune on 2009-05-16
Thanks, I will try that.

I think it should be in the package manager. Will check again.

---

