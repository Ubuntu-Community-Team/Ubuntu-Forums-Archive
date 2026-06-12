---
title: "mythweb installation error edgy 6.10"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by kacheng on 2006-10-10
Has anyone else encountered this issue trying to install mythweb?

[INDENT]**kacheng@bigturtle:~$ sudo apt-get install mythweb**
Reading package lists... Done
Building dependency tree
Reading state information... Done
mythweb is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mythweb (0.20-0.6ubuntu2) ...
/var/lib/dpkg/info/mythweb.postinst: 31: Syntax error: Bad substitution
dpkg: error processing mythweb (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mythweb
E: Sub-process /usr/bin/dpkg returned an error code (1)
**kacheng@bigturtle:~$**
[/INDENT]

---

### Post by phoenixsong44 on 2006-10-10
Yes, I encountered the same error. Its because the wrong shell is used in the post install script. 

You will need to edit /var/lib/dpkg/info/mythweb.postinst.

Replace the line: ```
#!/bin/sh 
```

with ```
#!/bin/bash
```

then type: ```
set -e 
sudo aptitude upgrade
```

Mythweb should then install cleanly. You might run into other problems that I did. [This website]("http://stacktrace.org/") helped me out a lot.

---

### Post by kacheng on 2006-10-11
Thanks for the fix - that worked brilliantly.

---

### Post by caa on 2006-10-12
How about just doing 
sudo ln -s /bin/bash /bin/sh

Then you never have to worry about whether a script calls for sh or bash

> **phoenixsong44 said:**
> Yes, I encountered the same error. Its because the wrong shell is used in the post install script. 

You will need to edit /var/lib/dpkg/info/mythweb.postinst.

Replace the line: ```
#!/bin/sh 
```

with ```
#!/bin/bash
```

then type: ```
set -e 
sudo aptitude upgrade
```

Mythweb should then install cleanly. You might run into other problems that I did. [This website]("http://stacktrace.org/") helped me out a lot.

---

