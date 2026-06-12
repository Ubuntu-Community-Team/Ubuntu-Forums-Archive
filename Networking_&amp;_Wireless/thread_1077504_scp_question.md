---
title: "scp question"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by lastfrontier on 2009-02-22
i am wondering how is it that you can copy a file to not from but to a remote host using scp i use it all the time but i have to log in to the remote host and then pull it from the comp i am working on just to get it to the remote host what a pain in the *** can any one help with this problem it seems by default that it wants to copy from not to but the man page says it is able to copy to so i know it can be done just not sure of the command.

---

### Post by squaregoldfish on 2009-02-22
Just switch the two filenames around. To copy from a server:

```
scp <remote> <local>
```

To copy to a server

```
scp <local> <remote>
```

That's it!

Steve.

---

### Post by lastfrontier on 2009-02-22
terminal-junky@terminal-junky:~$ scp -r tech1@67.**.**.**:/Desktop ~/home/tech1/Desktop/case_folder
tech1@67.**.**.**'s password: 
scp: /Desktop: No such file or directory
terminal-junky@terminal-junky:~$

did i not do it right?? not sure what happen


terminal-junky@terminal-junky:~$ scp -r tech1@67.**.**.**:/home/terminal-junky/Desktop/case_folder* ~/home/tech1/Desktop
tech1@67.**.**.**'s password: 
scp: /home/terminal-junky/Desktop/case_folder*: No such file or directory
terminal-junky@terminal-junky:~$ 

will keep trying really want to know

here it is got right this time

terminal-junky@terminal-junky:~$ scp -r /home/terminal-junky/Desktop/case_folder* ~/home/tech1/Desktop tech1@67.**.**.**:
tech1@67.**.**.**'s password: 
cops2.avi                                                                3% 6012KB  65.9KB/s   40:25 ETAt

---

