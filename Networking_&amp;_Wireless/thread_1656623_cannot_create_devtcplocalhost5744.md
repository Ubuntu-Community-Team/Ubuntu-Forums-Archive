---
title: "cannot create /dev/tcp/localhost/5744"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by jambel on 2010-12-31
Hi,

I have an application that listens to port 5744. I send to it a command from a terminal like this

```
echo my-command > /dev/tcp/localhost/5744
```and replies

I need to built a script doing the job so I make one as simple as this

```
#!/bin/sh

# $1 = command
# $2 = hostname
# $3 = port

echo $1 > /dev/tcp/$2/$3
```then in terminal I write..

```
sh myscript.sh command localhost 5744
```and I come up with this error

cannot create /dev/tcp/localhost/5744: Directory nonexistent

Any ideas?

---

### Post by Brandon Williams on 2010-12-31
The functionality you're trying to use is available in bash, not the POSIX shell, so you need '#!/bin/bash', not '#!/bin/sh'. Try running your existing script with "bash myscript.sh ...". If that works, then just change the "#!" line and it should be fine.

---

### Post by jambel on 2010-12-31
So simple? :oops:

thanks man!

> **Brandon Williams said:**
> The functionality you're trying to use is available in bash, not the POSIX shell, so you need '#!/bin/bash', not '#!/bin/sh'. Try running your existing script with "bash myscript.sh ...". If that works, then just change the "#!" line and it should be fine.

---

### Post by Iowan on 2010-12-31
[[SOLVED]]("http://https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") ? ;)

---

