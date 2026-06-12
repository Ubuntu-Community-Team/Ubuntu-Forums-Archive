---
title: "ftp as a mapped drive"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by ehoxha on 2010-01-11
Hi

Does anybody know if it&#347; possible to make a ftp addressed to a mapped drive?

---

### Post by Lars Noodén on 2010-01-11
You can mount a directory from a remote machine locally using [sshfs](http://linux.die.net/man/1/sshfs).  Files and directories inside that mount point will actually be on the other machine.

If the remote server has openssh-server installed, then you can do the following without more than having an account on the server:

```

# create mount point (directory) if none exists, for sshfs to use
test -e ~/*faraway* || mkdir --mode 700 *faraway*

# using compression, if using it makes the transfer faster
sshfs -C ehoxha@server.example.org:. ~/*faraway*

# XOR 
# not using compression, if not using it makes the transfer faster
sshfs ehoxha@server.example.org:. ~/*faraway*

```

The above uses '.', the default current directory on the remote server.  But it is possible to specify other directories, too.

```

# direct to the web server's directory
sshfs ehoxha@server.example.org:/var/www/htdocs/ ~/*faraway*

```

---

### Post by ehoxha on 2010-01-13
Thanks for the answer.
Now it&#347; working:D

ehoxha

---

