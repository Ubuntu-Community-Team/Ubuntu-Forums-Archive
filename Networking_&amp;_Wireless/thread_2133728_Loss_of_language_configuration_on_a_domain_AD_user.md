---
title: "Loss of language configuration on a domain AD user on ubuntu"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by ghimel on 2013-04-09
I'm an italian user of ubuntu 12.04.2 64bit and I use a computer with two users. 
One of these users is a domain AD user. I installed likewise-open to join to the domain AD with Windows Server 2003.
Well, after a recent update I found the language configuration changed only on the domain user: english for menu and windows.
Instead to the other user is all ok. I have tried to uninstalling and reinstalling likewise-open: nothing to do...

I found a similar problem [here]("http://superuser.com/questions/577358/changing-ubuntu-locale-settings-by-gui-crashes-the-accounts-daemon").

Any ideas?

Thank you in advance!

---

### Post by Lipaugus Vociferans on 2013-04-17
Hello Ghimel, I'm having exactly the same problem, but the only difference is that my language is spanish and not italian. 
Any ideas would be greatly welcome!!:D
Thanks

---

### Post by tito.brasolin on 2013-04-23
... It looks like a fix is on the way :)

[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/1162836](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/1162836)
(Bug #1162836 "likewise screws up PAM configuration for other services")

---

