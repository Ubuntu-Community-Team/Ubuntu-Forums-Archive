---
title: "Controlling Internet Access"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by mthalis on 2009-05-18
I want to write a program that control internet access according his level. My solution is between user machine and proxy setup a authentication server if authentication success he can access the proxy and go internet if not he  redirect to local web page.
surfing internet i found , using pac file can do this but i did it but not work ,i want control 200 people internet access.
please tell me how to do it using pac file or any other way. waiting for immediate response.

thank you

---

### Post by Alterax on 2009-05-19
Well, I prefer using squid for the proxy server, and squidguard to set up your access control lists.  If you have trouble with users trying to bypass it, it can always be set up as a passthrough server.

Setup will be complex--and I admit I don't have my notes handy--but there are plenty of tutorials on using the two together.  You might want to look them up--they may be exactly what you need.

---

### Post by mthalis on 2009-05-19
Thank for reply, using that software ,is it possible to user authentication and each user gave a particular time after expire that time then he can't access internet? 
i also found a software call **nocatouth**. please give me reference link that is very helpful for me. also give me some suggestions..
Thank for.

---

