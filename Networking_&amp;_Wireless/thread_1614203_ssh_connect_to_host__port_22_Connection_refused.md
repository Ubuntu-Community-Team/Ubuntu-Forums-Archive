---
title: "ssh: connect to host * port 22: Connection refused"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by sohlinux on 2010-11-05
I cannot ssh to any computer on my local network

ssh: connect to host 192.168.0.252 port 22: Connection refused

I cannot even ssh to localhost

I have allowed port 22 in the firewall

I can ssh to other servers outside my network

Any ideas?

Thanks

---

### Post by sedawk on 2010-11-05
If you really have sshd running on your local machine,
e.g. check with "pgrep sshd", then you really have
to solve that "ssh localhost" issue first ...

You can inspect network traffic with GUI tool wireshark
or command line tool tcpdump to see what really is
visible on the network.

E.g. "tcpdump -i any port 22" should show all traffic
that uses ssh port 22.

---

### Post by sohlinux on 2010-11-05
ssh is running because I can ssh to any computer outside my network

$ pgrep ssh
pid 1758


tcpdump -i any port 22 doesnt show anything because ssh is not working localy :confused:

---

### Post by sohlinux on 2010-11-05
dont know if this is any use but here is the output of ps aux | grep ssh

amy       1758  0.0  0.0   3352   204 ?        Ss   14:06   0:00 /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/amy/.gnupg/gpg-agent-info-amy /usr/bin/dbus-launch --exit-with-session gnome-session
amy      18559  0.0  0.0   4016   772 pts/2    S+   16:59   0:00 grep --color=auto ssh



also remote desktop viewer is unable to see any other computer on my network but I can connect to computers outside my network

---

