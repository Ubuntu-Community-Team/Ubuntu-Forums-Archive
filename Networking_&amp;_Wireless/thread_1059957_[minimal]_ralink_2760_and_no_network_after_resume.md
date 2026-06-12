---
title: "[minimal] ralink 2760 and no network after resume"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by eqisow on 2009-02-04
I installed XBMC on Intrepid minimal using [this]("http://xbmc.org/wiki/?title=HOW-TO:_Install_XBMC_for_Linux_on_Ubuntu_8.10_(Intrepid)_step-by-step") guide.

I finally have most of the kinks worked out, except one.

I have no network after resume from RAM. I'm not sure what logs or info to post with this, except to say that I don't recall having this problem when I was testing xbmc (installed the same way) on my pc, before buying the htpc. Of course, I was also using a svn build from about a week ago, but that doesn't seem like something that would be an xbmc issue. My wireless is an Edimax-7727-in running the RT2760 chipset.

Any help, guides, or advice on either of those issues would be muchly appreciated!

Edit: I put a script containing only "/etc/init.d/networking restart" in /etc/acpi/resume.d. The error goes from something like "network unavailable" to the network being "up," but not being connected. ie. it says network shares unavailable instead of network unavailable. 

What's more, I can drop to the command line and issue "sudo /etc/init.d/networking restart" after it resumes and get networking back. This is obviously an unacceptable solution for an htpc, but it makes me wonder why it doesn't work in the script.

Edit again: I tried adding unloading and loading of the wireless module to the script - no dice. I tested and the stop/start scripts work perfectly if I run them manually. Surely this isn't a permissions problem? I'm not sure where the suspend/resume log is.. guess I'll look.

---

### Post by eqisow on 2009-02-04
bump :(

---

