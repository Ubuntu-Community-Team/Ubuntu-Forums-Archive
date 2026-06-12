---
title: "ssh tunneling problem"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by morningsunshine on 2011-08-16
Hi friends,

My sys admin has set up ssh tunneling in our network. I am facing an issue with ssh tunneling connection and he has refused any help.

There are 2 servers on which he has configured access through ssh tunnels.

A. server1 -> jump pad
B. server2

I have to reach server2 via server1. On my ubuntu system, this is my .ssh/config file -
```

host server1
        Hostname server1.company.org
        ForwardX11 yes
        ForwardAgent yes
        TCPKeepAlive yes

host server2
        Hostname server1.company.org
        TCPKeepAlive yes
        User sunshine
        IdentityFile ~/.ssh/
#      Application access
        LocalForward localhost:10000 192.168.1.10:10000
```

192.168.1.10 -> server2 IP

I login as root and I can ssh directly to server1 by ```
ssh sunshine@server1
``` And as per my sys admin, I should also be able to reach server2 by doing ```
http://localhost:10000
```However, I can't reach server2.

I get this when trying ```
ssh sunshine@server2
``` -> ```
Enter passphrase for key '/root/.ssh/':
```

Can someone please tell me if I need to configure something else at my system or if I am doing something wrong?

My admin is not helping and I need to correct this at my end.

Thanks much in advance.

---

