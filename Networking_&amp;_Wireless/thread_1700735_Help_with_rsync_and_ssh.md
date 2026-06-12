---
title: "Help with rsync and ssh"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by pranavkaranjkar on 2011-03-05
I am trying to sync a folder on my ubuntu notebook to a ssh network. When I try to install rsync, it tells me that it is already installed. But when I issue the following command
```
rsync -auv /home/user/Desktop/ user@****.edu:~/pcfiles/
```I get following error
```
sh: rsync: not found
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [Receiver=3.0.7]

```Please help with my issue as I am new to using rsync and using ubuntu. Also, I need to use rsync from a windows machine in my school (I have no choice of the operating system there), but thats later part. I am trying it first in ubuntu.

---

