---
title: "squid with proxy server"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by manojpawar on 2009-09-30
hi,
  I have installed ubuntu server 9.0, I want to install squid proxy server over it but
could not find package squid, i am totaly new.
  please reply.

---

### Post by Davie In Dubai on 2009-09-30
did
>  sudo apt-get install squid 

produce any sort of error?

---

### Post by shredder12 on 2009-09-30
whenever you want to know the package name based on a keyword do this..

```
sudo apt-cache search <keyword>
```
replace keyword with squid in your case (don't include the <, > symbols)
then,, you will see a list and you can find the package name ...

once you have the package name run this command

```
sudo apt-get install <package_name>
```

---

