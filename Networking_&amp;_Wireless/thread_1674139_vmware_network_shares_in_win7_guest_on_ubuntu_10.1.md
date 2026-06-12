---
title: "vmware network shares in win7 guest on ubuntu 10.10 64 bit"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by BHEJU on 2011-01-23
Hi guys need help with finding / mapping network shares on Win 7 guest in vmware.
I am running 10.10 64 bit ubuntu and installed vmware workstation 7 (64 bit version). I created and installed win 7 (ultimate) vm. everything is good so far.
The issue is I have a second desktop with ubuntu and I have shared 4 drives on that desktop. I want those shared available to the win 7 guest. And even after enabling the shared folders I do not see them.

Note: I have a shared folder on the same machine where I have vmware installed and win7 has assess to that drive.. its just that the shares on network are not available.

Note2: i had virtualbox installed and it worked fine.

thanks for help.

---

### Post by xgt001 on 2011-01-23
Dude i am using Virtual Box
At first even i couldnt get it right .... i had to add a command in the DOS which looks like
"net use x: \\vboxsvr\sharename"
i think it will be analogous to that in Vmware
its a one time use command after that it will detect the host drives automatically :)

---

### Post by BHEJU on 2011-01-23
Thanks for reply / comments. However, my VirtualBox set-up was fine. Tt worked without any issues. I didn't have to do any manual work in (in dos or linux).
I am having problem making VMWare guest win7 see the network shares.

I would appreciate any help on VMWare.

Bheju

---

### Post by BHEJU on 2011-01-24
Bump.
Please help.

---

### Post by BHEJU on 2011-01-25
I don't know what was wrong. 
I just un-installed and re-installed vmware and it started working.
The only thing is now I have to manually map the shared drives. (win doesn't find them automatically).

---

