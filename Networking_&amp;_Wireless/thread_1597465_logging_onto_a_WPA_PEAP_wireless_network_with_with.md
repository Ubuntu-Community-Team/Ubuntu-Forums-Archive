---
title: "logging onto a WPA PEAP wireless network with/ without CA Certificate"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Hansmc on 2010-10-15
The collage I am going to has a secure wireless net work that we are suppose to be able to log into with a user name and password they give us. They have instructions on how to connect with windows and mac, but not for linux.

There tech support has not been any help and I have tried quit a few different combinations but with no luck.

According to their instructions for windows their net work uses WPA-Enterprise for security type, and PEAP. They do not seem to use any root certification authorities, and they have you unchecked "validate server certificate".

At [http://lug.wsu.edu/wireless/peap/ubuntu](http://lug.wsu.edu/wireless/peap/ubuntu) there is some similar thing were you can see screen shots, but I cannot follow these because I do not know what "CA Certificate" to use. Is there a way to do it with out a "CA Certificate"?

Does any one have an idea of what I might try? Thanks

---

### Post by luvshines on 2010-10-15
> **Hansmc said:**
> 
According to their instructions for windows their net work uses WPA-Enterprise for security type, and PEAP. They do not seem to use any root certification authorities, and they have you unchecked "validate server certificate".


Well if for windows they make you uncheck "Validate server certificate", I think you won't need CA at all and try to connect with 'none' default
But again I am not expert on this and maybe wrong

---

