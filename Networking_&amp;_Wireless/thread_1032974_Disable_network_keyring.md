---
title: "Disable network keyring"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by PrateekParekh on 2009-01-06
Whenever I boot my computer I am prompted to enter my keyring to enable internet connectivity. How can i disable this? I couldn't find it in "System => Preferences => Encryption and Keyrings"

I am also prompted for my password when I start my laptop from Hibernate mode.

This is very annoying as I am the only person using my laptop, and I want to do away with this disfunctionality. 

Thanks.

---

### Post by Fifoxtasy on 2009-01-31
you should find a solution here: [link]("http://ubuntuforums.org/showthread.php?t=1034422")

---

### Post by diablo75 on 2009-01-31
Here's a better (easier) solution:

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

It's as simple as deleting a file, restarting, and not entering a new keyring password after re-typing your WEP/WPA password.

---

### Post by PrateekParekh on 2009-02-03
Thanks for your replies. I was able to get rid of the keyrings using seahorse and deleting all the stored keys. It's quite simple and very convenient.

---

