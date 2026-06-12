---
title: "Remote machines are unable to connect via ssh to my machine."
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by jms1989 on 2009-08-02
Hello, I am experiencing a rather odd problem. The thing is, I can connect to any linux computer on the network but they can't connect to me. They just report: (ssh: connect to host 192.168.2.3 port 22: Connection timed out). I have openssh-server and ssh install this box but they still can't connect. Connectivity between all the other boxes work but not to me.

What could be the problem?

---

### Post by Brandon Williams on 2009-08-02
Is it possible that you have an iptables rule enabled that filters this traffic out? On the machine that you can't connect to, run 'lsmod | grep iptable' to see if any iptables related kernel modules are loaded. If there is no output, then this is not the issue. If there _is_ output, then check for rules associated with the loaded modules. For example, if the iptable_filter module is loaded, then run 'sudo iptables -L -t filter' to see rules associated with that table. Are there any rules that appear to drop the traffic that you want to let through?

Edit: I corrected the command name for checking for iptables rules. Looks like you already figured out that this was the problem. If I had written the correct command name, you probably would have figure it out sooner. Oops ... sorry.

---

### Post by doas777 on 2009-08-02
what do you get from:
```

sudo ps -ef | grep ssh
sudo cat /etc/ssh/sshd_config 

```

---

### Post by jms1989 on 2009-08-02
Output of "lsmod | grep iptable"

```

iptable_nat            13700  0 
nf_nat                 25876  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21388  9 iptable_nat,nf_nat
nf_conntrack           72008  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle         10880  0 
iptable_filter         10752  1 
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               23044  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables

```

output of "sudo iptable -L -t filter"
```

[sudo] password for jms1989: 
sudo: iptable: command not found

```

Output of "sudo ps -ef | grep ssh"
```

jms1989   5289  5204  0 07:53 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/jms1989/.gnupg/gpg-agent-info-terminator /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute /usr/bin/gnome-session
jms1989   7927  7907  0 08:21 pts/0    00:00:00 ssh 192.168.2.20
jms1989  10360 10182  0 09:55 pts/2    00:00:00 ssh 192.168.2.21
root     11838     1  0 10:35 ?        00:00:00 /usr/sbin/sshd
jms1989  13783     1  0 11:54 pts/4    00:00:00 /usr/bin/ssh -oForwardX11 no -oForwardAgent no -oClearAllForwardings yes -oProtocol 2 -oNoHostAuthenticationForLocalhost yes -s 192.168.2.21 sftp
jms1989  17101     1  0 13:54 pts/1    00:00:00 /usr/bin/ssh -oForwardX11 no -oForwardAgent no -oClearAllForwardings yes -oProtocol 2 -oNoHostAuthenticationForLocalhost yes -s 192.168.2.50 sftp
jms1989  21590 21564  0 16:07 pts/3    00:00:00 grep ssh

```

Output of "sudo cat /etc/ssh/sshd_config"
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 127.0.0.1
ListenAddress 192.168.2.3
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

As far as I know, iptables only logss the packets. I don't mess with iptables. Why would it allow outbound but not inbound?

---

### Post by doas777 on 2009-08-02
most modern firewalls use a method called Stateful Packet Inspection, whereby all traffic is allowed outbound, but no traffic is allowed inbound unless it is in response to a connection initiated from the inside. generally the answer to that question is to open the port manually if you want the service available for connection initiation from the outside.

so what happens if from a client machine you run:
```
telnet <ipaddress of server> 22
```if the port is open and ready for business you should see:
```
Trying 192.168.xx.yy...
Connected to host.domain.net.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1

```then kill the connection (i used ctrl + C, enter)

or if the port is closed you will see:
```
telnet: Unable to connect to remote host: Connection refused
```

---

### Post by jms1989 on 2009-08-02
well after looking at my firewall settings, I found that it was filled with stuff I forgot was even there so I just cleared the rule list and I was able to connect remotely from another computer. I don't remember when I put those entries there but nevertheless, it works now.

---

