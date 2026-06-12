---
title: "ssh cronjob"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by Bradj47 on 2010-11-17
I'm trying to create a cronjob that simply uploads a file to a server then runs a command through ssh. Here are the commands that I would run in a Terminal: 

```
scp /home/user/path/to/file user@example.net:public_html/foobar
*asks for password*
ssh user@example.net <command>
*asks for password*
```

The problem I'm having is figuring out how to specify the password it should use when it automatically runs the commands. How do I specify the password?

---

### Post by matt_symes on 2010-11-17
Hi

Can you use keys instead of a password. Much safer anyway and transparent.

From the terminal type.

man ssh-keygen
man ssh-copy-id

Kind regards

---

### Post by tgm4883 on 2010-11-17
Here is a good article on it  [http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

---

### Post by matt_symes on 2010-11-17
Hi

Maybe you should read this. It gives you the solution using expect, but also argues why you should not use it and offers a better way using keys.

[http://ubuntuforums.org/showthread.php?t=551723](http://ubuntuforums.org/showthread.php?t=551723)

My advice also is to use keys.

Kind regards.

---

### Post by Bradj47 on 2010-11-17
Thanks for the replies guys. The commands you gave me worked perfectly.

---

