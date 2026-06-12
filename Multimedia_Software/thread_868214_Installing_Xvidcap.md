---
title: "Installing Xvidcap"
date: 2008-07-23
forum: Multimedia Software
---

### Post by mufn8r on 2008-07-23
Hi. I'm trying to install Xvidcap. When I type in sh filename.tar.gz I get ")" unexpected or something to that affect. Then I read that I need to install liblame0_version.deb first. When I tried to install that it said I had to be a superuser. I am the only account on this OS, how can I not have maximum access to everything by default? I tried to follow the directions I found at a web site but nothing works. Any tips for installing Xvidcap? Thanks.

---

### Post by collinp on 2008-07-23
Just download it from the repos:

```
sudo apt-get install xvidcap
```

O, and for your question about superuser: there is a root user that can do anything on the computer, but the account is disabled by default. Putting sudo infront of an application to execute in terminal will make the program run as root. Try to avoid running as root, as it is very dangerous. Really the only time you would need root would be when running apt-get, make install, or editing some system file.

---

### Post by mufn8r on 2008-07-23
Thank you very much. I just started using Linux Ubuntu a couple days ago after many failed attempts at using Linux. Unbuntu rocks! 

Finally I can use Linux comfortably! :-\"

---

### Post by mufn8r on 2008-07-23
OH, I wanted to ask you about the root account. I enabled it by giving it a password the using the ```
su root
``` command and entering the password.

How do I disable the root account again? Just go in and delete the password?

---

