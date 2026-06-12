---
title: "Putty: Server Unexpectedly closed network connection"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by pingue110489 on 2009-04-19
Hi all,
I realise there's probably something blindingly obvious here, but I'm completely stuck, and no matter of searching has solved my problem.

Whenever I try to use putty to connect (within my home network) to my server (recent Ubuntu release, openbsd-ssh), I get prompted for my username / pw, and when I enter them correctly, it immediately halts saying "Server Unexpectedly closed network connection".
I've also tried ssh'ing from a root shell actually on the server (ssh -v 192.168.1.2), and I simply get "Connection closed by 192.168.1.2" after the same password prompt
I've tried reinstalling ssh (and deleting the .conf file at the same time), and updating all packages, but to no avail. Nothing is listed in hosts.allow/hosts.deny, and I'm still getting the same error when I remove both these files.

Up until a couple of days ago, everything was working perfectly, and I've never had any problems remotely accessing the server. The only changes I was making at the time were to do with cups and (trying to) install a networked printer, though I didn't touch any pre-installed packages. After a simple reboot, this was all that happens.

Any help/even vague pointers would be appreciated, and I'll happily supply any more information y'all need.
Cheers guys ;)
Mike

---

### Post by dmizer on 2009-04-20
Please post your /etc/ssh/sshd_config file.

Also, post the output of this command:
```
sudo iptables -L
```

---

### Post by pingue110489 on 2009-04-20
Doing this by hand (as I can't copy and paste :P), iptables gives
```

Chain INPUT (policy ACCEPT)
target    prot  opt   source      destination
ACCEPT    udp   --    anywhere    anywhere     udp dpt:domain
ACCEPT    tcp   --    anywhere    anywhere     tcp dpt:domain
ACCEPT    udp   --    anywhere    anywhere     udp dpt:bootps
ACCEPT    tcp   --    anywhere    anywhere     tcp dpt:bootps

Chain FORWARD (policy ACCEPT)
target    prot  opt   source      destination
ACCEPT    all   --    anywhere    192.168.122.0/24  state RELATED,ESTABLISHED
ACCEPT    all   --    192.168.122.0/24 anywhere
ACCEPT    all   --    anywhere    anywhere

Chain OUTPUT (policy ACCEPT)
target    prot  opt   source      destination


```

And the sshd_config file (though I've excluded the majority of comments) :

```


# Package-generated configuration file
# See sshd_config(8) manpage for details

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

Port 22
Protocol 2
#ListenAddress 0.0.0.0
#ListenAddress ::

HostKey /etc/ssh_host_key
HostKey /etc/ssh_host_rsa_key
HostKey /etc/ssh_host_dsa_key

UsePrivilegeSeparation yes

KeyRegenerationInterval 3600
ServerKeyBits 768

SyslogFacility AUTH
LogLevel INFO

LoginGraceTime 120
PermitRootLogin yes
StrictModes yes 

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
#IgnoreUserKnownHosts yes

#PasswordAuthentication yes
PermitEmptyPasswords no

ChallengeResponseAuthentication no

#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

UsePAM yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

AcceptEnv LANG LC_*

Subsystem	sftp	/usr/lib/openssh/sftp-server


```

Cheers :)

---

### Post by dmizer on 2009-04-20
Looks like you have firewall rules in place, and that's why your ssh connection is failing.

Did you install firestarter? If so, use synaptic package manager to uninstall it.

---

### Post by pingue110489 on 2009-04-20
I haven't got firestarter installed ('apt-get remove firestarter' said package not installed)
I'm presuming you were expecting to see nothing returned from iptables - would deleting rules manually make a difference? (I've had very little experience of firewalls in Linux)
:D

---

### Post by dmizer on 2009-04-20
Well, if it's not firestarter, then how did the iptables rules get there in the first place? You can delete them, but it may disable some other desired functionality.

Did you recently follow any route forwarding tutorials like internet connection sharing? If so, please link them.

---

