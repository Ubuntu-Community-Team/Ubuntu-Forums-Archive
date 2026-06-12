---
title: "SSH from a nother network."
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by Aphexlog on 2013-03-16
I am trying to set up an SSH server on my computer. I already have open-ssh installed and when anyone enters this command SSH [ip.add.re.ss] they are able to see ' user' prompt and they enter username and password to what i set it and they get an access dinied message. any steps that i might be missing?

---

### Post by CharlesA on 2013-03-16
Check /var/log/auth.log for the reason why they are getting access denied messages.

---

### Post by Aphexlog on 2013-03-16
im noobish sorry, where is the var dir located? (or were should it be?)

---

### Post by gtmurff on 2013-03-16
For log files, have a look at: 

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

It may be helpful to brush up on using a terminal.  You can do that at:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by Lars Noodén on 2013-03-16
> **Aphexlog said:**
> im noobish sorry, where is the var dir located? (or were should it be?)

You can use [less](http://manpages.ubuntu.com/manpages/precise/en/man1/less.1.html) to view the log files in the terminal.  Open a terminal (ctrl-alt-t) and then enter the following:
```

less /var/log/auth.log

```

With 'less' you can scroll back and forth in the file and can even search using regular expression pattern matching.

---

