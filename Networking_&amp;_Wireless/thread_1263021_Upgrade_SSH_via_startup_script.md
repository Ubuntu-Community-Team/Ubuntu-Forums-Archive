---
title: "Upgrade SSH via startup script?"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by lsp432 on 2009-09-10
I was experiencing terrible scp speeds, and while trying to troubleshoot I realized my openssh was out of date, and also ran across the HPN-SSH patch [here]("http://http://www.psc.edu/networking/projects/hpn-ssh/"), so I went ahead and upgraded my client computer's openssh to 5.2 with the patch. Scp is considerably faster now, and I'd like to do the upgrade on my server as well, which is sitting in the house of a friend who knows nothing about computers, and lives considerably far away.

The best idea I could come up with is to scp the patched openssh source, a customized sshd_config, and a script to the server machine. The script purges the openssh-client and -server packages, builds and installs the patched source, backs up sshd_config and replaces it with one with the proper settings, and starts the sshd daemon. Testing on my client computer, the script works perfectly.

I figure if I tell the server to run the script as root at startup and reboot, it will sort itself out and then after a couple minutes I can log back in, take the script off running at startup, and set sshd to run at startup, and everything will be gravy.

So my question is, does this seem like a viable plan? Am I overthinking it, and there's a more straightforward way to upgrade ssh over ssh? Or is something just likely to go wrong and I'll be locked out of my server? I figured I'd ask for advice before I went ahead with it.

Thanks

---

