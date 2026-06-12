---
title: "Upgrade to kernel 2.6.30 kills wireless..."
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by christoforever on 2009-06-16
I'm running Kubuntu. When I use the 2.6.30 kernel my wireless craps out. Not only that, when I plug into the internet directly I still get nothing. So I'm assuming that I need to reinstall some drivers only I don't know which ones. I have a Broadcom wireless card. However when I open the package manager and type broadcom none of the packages are installed. However under the hardware drivers program it sais I have a Broadcom STA wireless driver enabled.

Any ideas?

---

### Post by Ayuthia on 2009-06-16
Ubuntu provides the Broadcom STA driver with their kernel as a restricted module.  What this means is that if you compile your own kernel, you will need to go to the [Broadcom site]("http://www.broadcom.com/support/802.11/linux_sta.php") and compile the module manually.  Since you are using 2.6.30, you will also need to install the patches to allow the source code to compile with 2.6.30.  I am currently using Gentoo with 2.6.30 kernel and they provide the package for the Broadcom STA module (which works for this kernel).  You might try their patches from this [link]("http://packages.gentoo.org/package/net-wireless/broadcom-sta?full_cat").  I have not tested it out by compiling it from the Broadcom source so I can't confirm that it will work for you.

Hope that helps.

---

