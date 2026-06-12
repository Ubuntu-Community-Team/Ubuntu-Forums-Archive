---
title: "Password Issues"
date: 2013-10-19
forum: Mythbuntu
---

### Post by jlp_engineer on 2013-10-19
For some reason, the normal password I have been using to run my Mythbuntu system no longer works.  I don't know if it had something to do with a recent power outage, but whenever the system now prompts me for a password, the password I have been using for that system no longer works.  I don't know if the password file is corrupt or what is going on.  I tried the GRUB recovery, boot into root shell password fix that is all over the Internet, but it does not work, since the root shell prompts me for a password that I don't have, so I can never get to a prompt.

So, the million dollar question is, how do I recover the password for my user account, or how do I reset the password for the root account?

Thanks,

---

### Post by uteck on 2013-10-21
That is very odd.  I was going to recoment Kon Boot, but looks like they stopped devlopment of the Linux version.
You could boot from a live cd/live usb and then do a chroot to reset the password.  These instructions should help you get the chroot setup:
[http://aaronbonner.io/post/21103731114/chroot-into-a-broken-linux-install](http://aaronbonner.io/post/21103731114/chroot-into-a-broken-linux-install)
Then you change the password as normal, or run apt-get to fix any broken pakages.

---

### Post by steeldriver on 2013-10-21
There have been several posts recently about mythbuntu setups suddenly wanting the root password, and it seems to be an issue with gksu-properties getting set to 'su' rather than 'sudo' - try running

```
gksu-properties
```

from a terminal and making sure the mode is set correctly.

---

