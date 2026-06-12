---
title: "Plz help-deleted default.keyring!"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by dyingsun on 2009-04-25
Hi ppl, I've had a monumental catastrophe (form my perspective anyway!) - was following some guidelines to stop an annoying keyring login prompt (not the commonly reported nm issue, this was gTwitter).

I deleted the default.keyring file but before I could restart the app we lost power and the machine went down - now when the Ubuntu login screen boots up it wont let me enter my name and password :(

What do I do? I can get into a basic CLI using restore option ofrom GRUB, but don't know what to do to fix the problem once I'm there. I don't want to be stuck in Windoze forever!

Using Hardy/Studio, if that makes a difference.

Thanks all!

---

### Post by sahabcse on 2009-04-25
For login CLI press alt+ctr+f1 to f6. For fixing the grub and default keyring issue pls follow below url

[http://sahabm.blogspot.com/2009/02/default-keyring-cant-unlock-ubuntu-810.html](http://sahabm.blogspot.com/2009/02/default-keyring-cant-unlock-ubuntu-810.html)

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by dyingsun on 2009-04-25
Thanks for your response, Sahabcse. I finally removed the problem by removing the "common-pamkeyring" line from the /etc/pam.d/gdm file. Also had to reset my login password and reboot.

Thanks!

---

