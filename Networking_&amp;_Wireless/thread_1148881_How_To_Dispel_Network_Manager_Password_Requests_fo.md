---
title: "How To Dispel Network Manager Password Requests for Keyring?"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by Andysan on 2009-05-04
Hi folks,

My brother has just installed Ubuntu Jaunty XFCE spin onto his Acer Aspire One laptop and all appears to be working well, however Network Manager asks for the gnome-keyring password in order to connect to his wireless network.

For his needs, this is a bit overkill and we'd like to turn it off - I've seen some dirty hacks that involve keeping passwords stored in unencrypted text files and this isn't really what i'd call a solution ([http://ubuntuforums.org/showthread.php?t=431893&highlight=libpam-keyring](http://ubuntuforums.org/showthread.php?t=431893&highlight=libpam-keyring)).

I'm thinking maybe the libpam-gnome-keyring package from the repos but i'm not entirely sure how to configure it.  Being on the other end of a telephone line from my brother makes it a bit more difficult - can anyone perhaps offer some help for resolving this please?

Interestingly i have no such issues running an XFCE 4.4 session in Intrepid, yet Kubuntu 9.04 asks for my keyring password to connect to my wireless (which I'm fine with).  Was this a new inclusion for Jaunty or is it to do with XFCE 4.6?

Thanks.

---

### Post by Andysan on 2009-05-06
If it helps anyone, this has been resolved.  Turns out that the machine was set to autologin.  Changing this resolved the issue.

---

### Post by The Pinny Parlour on 2009-05-09
> **Andysan said:**
> If it helps anyone, this has been resolved.  Turns out that the machine was set to autologin.  Changing this resolved the issue.

Pretty poor solution however.

---

