---
title: "Alternatives to NX Client for Windows-to-Linux remote session?"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by DiceRules on 2013-03-07
Morning, all.

At work, we have our standard issue Windows boxes that we must use.  We also have our dev boxes with are Ubuntu.  We can either switch back and forth between them using a KVM switch, or do what I've been doing which is use NX Client on Windows to open a remote X session on Ubuntu.

The reason why NX Client works is because it runs entirely in user space (I guess), and requires no installation, otherwise it would be a deal-breaker since we're unable to install software on our Windows boxes.

On the upgrade to Ubuntu 12.10, NX Client stopped working.  I won't go into it here, but it has to do with a problem with libcairo or something.  I employed a hacky workaround, and continued using NX Client.

Now, however, this hacky workaround is getting in my way.  As NX Client still doesn't seem to support Ubuntu 12.10 yet, I'd like to find an alternative, if there is any.  The key requirement is that the Windows client should not require administrative privileges, e.g., installation.

Any suggestions?

---

