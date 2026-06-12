---
title: "ssh to ubuntu 12.10 and 12.04"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by fredcarru on 2013-07-15
I cannot ssh to my desktop from other machines on the network. They can ssh to raspberrypi but not from Pi to them I get 'ssh: connect to host fred-desktop port 22: Connection timed out'

both sshd-server and sshd-client are installed and sshd-conf sets the port to 22.

---

### Post by Lars Noodén on 2013-07-15
Can you connect to your desktop from itself?

```

ssh localhost

```

Have you activated UFW or set up iptables?  If so, you'll have to open up port 22 to allow incoming connections.

---

### Post by fredcarru on 2013-07-16
yes I can ssh localhost and no I haven't set upUFW or iptables however the results of -L are

fred@fred-desktop:~$ sudo iptables -L | grep port
ACCEPT     udp  --  anywhere             anywhere             multiport dports netbios-ns,netbios-dgm /* 'dapp_Samba' */
ACCEPT     tcp  --  anywhere             anywhere             multiport dports netbios-ssn,microsoft-ds /* 'dapp_Samba' */
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
fred@fred-desktop:~$

However if I run

ufw disable 

I can connect. So what I need to know is how to enable port 22 in UFW, I'll try man ufw for this

Thanks for the tip. I didn't enable UFW but it must be enabled as part of the installation.


yep ufw allow 22 does the job

thanks for the help

---

### Post by steeldriver on 2013-07-16
When you installed OpenSSH server, it should have created an 'app profile' for SSH in ufw

```

$ sudo ufw app list
Available applications:
  CUPS
  OpenSSH

```

in which case you can allow it very simply by doing

```

sudo ufw allow ssh

```

however that allows connection from *any* host (usually fine if you are behind a NAT router) - if you need help setting up a finer grained rule post back

---

