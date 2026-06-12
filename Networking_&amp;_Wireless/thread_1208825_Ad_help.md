---
title: "Ad help"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by bmobley on 2009-07-09
I have successfully added my laptop to my corporate 2003 domain. I can login at work with any valid AD account and can sudo with AD group specified without any issue, but once I remove it from the network and take it home I am not able to login with either a cached AD user (AD account) or a local user. With an AD account I get "No Login Servers" and with local account I get "Authentication Failed". What am I missing??
Many thanks in advanced!

---

### Post by pastalavista on 2009-07-09
Once you "remove it" wouldn't it need to be "successfully added" again? Why did you remove it? Couldn't you just logoff/disconnect? Are you trying to login from home? Have you installed samba?

---

### Post by bmobley on 2009-07-10
I guess I was unclear, "remove it from the network" is in reference to physically unplugging the network cable not remove it from AD. If I am not physically sitting on my works network, I can no longer log in.

---

### Post by Drate on 2009-07-10
you can't login with a user account at all?

i have had similar problems using likewise-open (btw, ARE you using likewise-open?) but it always let me login with the local account.  It would still SAY that I had failed when I login and everytime I had to give password for sudo... but it always worked.

If you are using likewise-open trying purging and re-installing.

---

### Post by bmobley on 2009-07-11
I can log in as an AD account at work to the gui. I can log in as Root in any other TTY. But not with any other local account. At home The only way I can get into the laptop is using GRUB recovery.

Thanks

---

