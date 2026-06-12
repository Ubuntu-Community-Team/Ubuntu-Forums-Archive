---
title: "Network Manager Keyrin"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by rickyjames22 on 2010-04-25
Hi Eveyrone,
I am new to linux and ubuntu. I am using ubuntu Hardy Heron release 8.04

I have not used it in a long time and then when I did fire up the laptop. I get a message asking me to enter a password for keyring. 

The message is as follows;

Unlock Keyring

"The application 'Network Manager Applet' (/usr/bin/nm-applet) wants access tot he default keyring, but it is locked.'

Password: _______________

Then I can Deny or OK it. 

How can I disable that and keep it from popping up. 


Also, it there a way to figure out/change the administrator password if you don't remember it as well? 

Thanks guys,

Rick

---

### Post by agnes on 2010-04-25
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/")
Hope that helps for the keyring network-manager thing.

For the root password "hack": iirc if you start GRUB go to the "recovery mode" (or similar), then to the "drop to root prompt" (or similar). Then you should be root automatically. Type *passwd* to edit the root password, then.
There are other methods for automatic login as root via GRUB such as adding "ro init=/bin/bash" or "single" to the normal boot line (press "e" in Grub to edit the boot line). 
Now I don't recall exactly, which version those methods apply to... sorry - maybe somebody else knows. Those methods could be fixed by now, but you have an old version, so good chance they work.

---

### Post by rickyjames22 on 2010-04-26
> **agnes said:**
> [http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)
Hope that helps for the keyring network-manager thing.

For the root password "hack": iirc if you start GRUB go to the "recovery mode" (or similar), then to the "drop to root prompt" (or similar). Then you should be root automatically. Type *passwd* to edit the root password, then.
There are other methods for automatic login as root via GRUB such as adding "ro init=/bin/bash" or "single" to the normal boot line (press "e" in Grub to edit the boot line). 
Now I don't recall exactly, which version those methods apply to... sorry - maybe somebody else knows. Those methods could be fixed by now, but you have an old version, so good chance they work.

First, Thank you very much for your help. 
Your link for the keyring works just great, I followed the instructions and it all worked. I am still prompted for a keyring and this time I have my password. 

Second, I did use the above instuctions to change my password. Ubuntu asked me to type in my 'unix password' and verify it which I did successfully. 
However,  once I rebooted the computer and got to the desktop, and wanted to check for updates, it would not accept the new password. 
Is there another way to change the root password by chance, please? 


Thanks again, 

Rick

---

