---
title: "Nautilus times out when attempting to login to server"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by kyleflan on 2009-10-23
My school's server takes a while to log in to when not on the campus network. (Usually ~45 seconds) I can ssh and scp to the server via the command line, but I try to use nautilus to connect, I get a timeout error:

> Could not open location 'sftp://user@sun.box.edu/home/user'
Timed out when logging in

Is there a way to increase the time before nautilus times out? I've edited /etc/ssh/ssh_config and added
```
ConnectTimeout 10000
```
but that doesn't fix the problem either.

Thanks,
Kyle

---

