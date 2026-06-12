---
title: "ssh: connection reset by peer, then refused"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by kfiller on 2009-01-17
Hello,

New to Ubuntu, I've installed Intrepid on an older Dell notebook. Install went fine, and once logged in I can connect to the net via the wifi connection without problem.

However, I can't seem to get ssh working.  I've installed the ssh server through apt, but I'm met with the following error when trying to SSH from OSX 10.5.6 into Intrepid (all on the same network):

```
mbp:~ kfiller$ ssh 192.168.1.88
kfiller@192.168.1.88's password: 
Read from socket failed: Connection reset by peer
```

trying again, I get:

```
ssh -vvv 192.168.1.88
OpenSSH_5.1p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.88 [192.168.1.88] port 22.
debug1: connect to address 192.168.1.88 port 22: Connection refused
ssh: connect to host 192.168.1.88 port 22: Connection refused
```

This is fairly consistent, although sometimes I am able to ssh into Intrepid -- but after a few seconds it gives the 'read from sock failed' error and the connection is lost.

SSH seems to work fine from the Intrepid notebook itself, using 'ssh 192.168.1.88'. I can also ssh out from Intrepid into other local machines as well.  Finally, the OSX 10.5.6 machine is able to ssh into other machines on the same network without problem.

Here's the ifconfig from Intrepid:

```

eth0      Link encap:Ethernet  HWaddr <XXX> 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr <XXX> 
          inet addr:192.168.1.88  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe90:a2bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33622 (33.6 KB)  TX bytes:10631 (10.6 KB)
          Interrupt:17 Base address:0xe000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

sudo iptables -l gives:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

and the ufw firewall is not loaded.

I'm sure I'm missing something, but sure sure what else is happening here... any help would be most appreciated!

---

### Post by Iowan on 2009-01-18
I thought I saw the problem - my system fires up with ```
debug1: Reading configuration data /etc/ssh/ssh_config
``` ...different directory. But then I remembered you said OSX.  Can any other machines SSH into Intrepid?  Though I don't remember changing anything on my LAMP server, it might be beneficial to see your /etc/ssh/sshd_config

---

### Post by kfiller on 2009-01-19
Thanks for the tip. 

I installed the Intrepid server as a Vmware Fusion device on OSX, and I can ssh into the server just fine from a different OSX based notebook.  It's just the dell notebook running Intrepid that's giving me problems.  I'm wondering if it has something to do with the wifi on the dell...

Here's the sshd_config

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
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
PermitRootLogin yes
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

---

