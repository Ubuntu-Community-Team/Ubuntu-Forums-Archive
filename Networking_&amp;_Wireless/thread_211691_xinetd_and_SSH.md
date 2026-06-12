---
title: "xinetd and SSH"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by pt123 on 2006-07-08
In order to secure my ssh I installed xinetd using the following instructions on this thread

[http://ubuntuforums.org/showthread.php?t=159047&page=2](http://ubuntuforums.org/showthread.php?t=159047&page=2)


```

ervice ssh
{
port = 22
#the ip 192.168.0.1 is my local-net nic
bind = 192.168.0.1
socket_type = stream
protocol = tcp
user = myusername
group = users
type = INTERNAL UNLISTED
wait = no
instances = 4
# access restricted to one comp from my local network
only_from = 192.168.0.2
}

```

Then I tried
ssh myusername@192.168.0.1
from another computer on my network (192.168.0.3 , which shouldn't be allowed to based on the xinetd) and I was able to log on.

Can someone please help me as I plan to use xinetd to restrict services to my LAN and prevent access to them from the internet.

Thanks

Edit I looked at the daemon logs
when I restarted xinetd it had this
Jul 8 12:27:44 localhost xinetd[18046]: No such internal service: ssh/stream - DISABLING

What does that mean?

Edit I managed to get rid of the error by using
from this macos page:
[http://forums.macosxhints.com/showthread.php?t=24258](http://forums.macosxhints.com/showthread.php?t=24258)

service ssh
{
disable = no
socket_type = stream
wait = no
user = root
server = /usr/libexec/sshd-keygen-wrapper
server_args = -i
groups = yes
# flags = REUSE IPv6
session_create = yes
only_from = 192.168.0.2
}

But I am still able to ssh from the 192.168.0.3 computer.

Any ideas?

---

