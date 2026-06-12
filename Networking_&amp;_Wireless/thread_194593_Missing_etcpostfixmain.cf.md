---
title: "Missing /etc/postfix/main.cf"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by AskHL on 2006-06-11
Hello, when I run 
```
sudo /etc/init.d/networking restart
```
then it complains about a (fatally) missing file namely 
```
/etc/postfix/main.cf
```
In the /etc/postfix directory there are three files called main.cf.dist , main.cf.debian and main.cf.tls . What can I do? The computer frequently crashes while deconfiguring interfaces and I think might be the reason, symptoms appropriately described here: [http://ubuntuforums.org/showthread.php?p=1123328#post1123328]("http://ubuntuforums.org/showthread.php?p=1123328#post1123328").

It is a laptop with Dapper which was dist-upgraded from Breezy.

---

### Post by ns2048 on 2006-06-12
Are you using Postfix? If so, then you can create a symbolic link to 'main.cf.dist' by running 'sudo ln -sf /etc/postfix/main.cf.dist /etc/postfix/main.cf'
--ns2048

---

### Post by AskHL on 2006-06-18
Thank you for the advice ns2048, but it didn't fix the crash. Later that problem seems to have been fixed in a patch so everything is fine now.

---

