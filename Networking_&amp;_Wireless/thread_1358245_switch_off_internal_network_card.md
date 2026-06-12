---
title: "switch off internal network card"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by trethomil on 2009-12-18
This is following earlier posts and thanks to people's help, my old laptop is now connected to the internet and busy downloading and installing updates to xubuntu. Marvellous.

Now, I have two wireless cards. One is internal - a RaLink RT2400 / RT2460 Adapter, which barely works and the other is a plug in one - Netgear WN511B - which works very well.

Do I need to switch the internal one off? And if so, how do I do that?

---

### Post by oOarthurOo on 2009-12-18
You can prevent your system from loading the modules needed to run the internal card by locating the module being used (us lsmod and google to determine), then blacklisting the module.

There are many posts on this forum and elsewhere with instructions on how to blacklist a module.

---

### Post by oOarthurOo on 2010-01-01
Yours sounds  like a very different problem. Create a new thread with an appropriately detailed subject line, and the output of lspci.

---

