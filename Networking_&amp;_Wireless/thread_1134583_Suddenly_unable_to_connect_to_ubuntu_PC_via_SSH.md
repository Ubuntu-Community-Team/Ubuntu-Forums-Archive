---
title: "Suddenly unable to connect to ubuntu PC via SSH"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by JPZG on 2009-04-23
Hello everyone,

I'm currently experiencing a sporadic problem with my ubuntu download box and have ran out of ideas on how to resolve the issue.

There are times when it is impossible for me to connect to my download box, even from the LAN.

When I connected to my server with VNC to troubleshoot, I verified that:

ps auwx |grep sshd
```
root      6446  0.0  0.1   5380  1052 ?        Ss   20:13   0:00 /usr/sbin/sshd
```
sudo netstat -lp |grep *.https
```
tcp        0      0 *:https                *:*                     LISTEN      6446/sshd
```

sudo iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


executed sudo /etc/init.d/ssh restart just in case...

ssh localhost -p 443 worked but connecting from LAN PC results in "connection refused" Client pc runs WinXP with puTTY, no firewall.

The only thing that fixes this for me right now is a good ol` reboot OR changing the port on sshd and restarting service.

Here is my config without comments in hopes of shortening my post:

/etc/ssh/sshd_config:
```
Port 443
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel VERBOSE
LoginGraceTime 30
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication no
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
MaxStartups 3:6:12
Banner /etc/issue.net
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM no
AllowUsers <my user goes here>
ClientAliveInterval 20
Compression yes
MaxAuthTries 3
```

The only thing I have in mind is the MaxStartups 3:6:12 settings?

Any comments, ideas or even resolutions are welcome =)

---

