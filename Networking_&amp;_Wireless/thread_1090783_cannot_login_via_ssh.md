---
title: "cannot login via ssh"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by csc2ya on 2009-03-08
I've installed the openssh server on my laptop so that I can access it remotely when i'm out. However, it always says that my password is incorrect despite me using the exact same password that works when I use  it to log on via the gui when i'm front of the machine:

```
administrator@Laptop:~$ ssh -v Administrator@192.168.1.68
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.68 [192.168.1.68] port 22.
debug1: Connection established.
debug1: identity file /home/administrator/.ssh/identity type -1
debug1: identity file /home/administrator/.ssh/id_rsa type -1
debug1: identity file /home/administrator/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.1.68' is known and matches the RSA host key.
debug1: Found key in /home/administrator/.ssh/known_hosts:12
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/administrator/.ssh/identity
debug1: Trying private key: /home/administrator/.ssh/id_rsa
debug1: Trying private key: /home/administrator/.ssh/id_dsa
debug1: Next authentication method: password
Administrator@192.168.1.68's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
Administrator@192.168.1.68's password: 

```I've checked iptables and that's set to accept all connections:

```
administrator@Laptop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```The following is my configuration file for ssh:

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
#AuthorizedKeysFile    %h/.ssh/authorized_keys

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
```Before now, I could ssh from other machines on my home network and it would work, but now I cannot log in remotely at all without it saying that my password is incorrect.

---

### Post by bettlebrox on 2009-03-08
You can't really tell from the client side what the problem is. Look in /var/log/daemon.log and /var/log/auth.log on the laptop to see what sshd is reporting.

>PermitRootLogin yes
Why are you permitting root to login? That's a big security [no-no]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=qqn&q=securing+ssh+PermitRootLogin&btnG=Search").

---

### Post by csc2ya on 2009-03-08
I hadn't thought of root logins to be honest. I've disabled it and restarted the ssh server now though.

I've found the following in auth.log:

```
Mar  8 20:55:35 Laptop sshd[26126]: Invalid user Administrator from 192.168.1.68
Mar  8 20:55:35 Laptop sshd[26126]: Failed none for invalid user Administrator from 192.168.1.68 port 42734 ssh2
Mar  8 20:55:38 Laptop sshd[26126]: pam_unix(sshd:auth): check pass; user unknown
Mar  8 20:55:38 Laptop sshd[26126]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=laptop.home 
Mar  8 20:55:39 Laptop sshd[26126]: Failed password for invalid user Administrator from 192.168.1.68 port 42734 ssh2
```

I also had a friend try to log in via ssh and it's logged that in a similar way:

```
Mar  8 20:52:15 Laptop sshd[24574]: Invalid user Administrator from 66.93.*
Mar  8 20:52:15 Laptop sshd[24574]: Failed none for invalid user Administrator from 66.93.* port 50291 ssh2
Mar  8 20:52:26 Laptop sshd[24574]: pam_unix(sshd:auth): check pass; user unknown
Mar  8 20:52:26 Laptop sshd[24574]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=dsl093-*.pit1.dsl.*.net 
Mar  8 20:52:28 Laptop sshd[24574]: Failed password for invalid user Administrator from 66.93.* port 50291 ssh2
```

---

### Post by Woodsyx on 2009-03-08
Is the username the same on both machines if not you need to login with

```
ssh username@server
```

otherwise it will try to login with the username thats logged in on the client computer.

---

### Post by csc2ya on 2009-03-08
The way i'm trying to connect is from the same machine at the moment....while i'm trying to get it working.

I am entering ssh administrator@192.168.1.68 which is my username on the computer and it's lan ip

When I had the other person connect I told them which username and password to use (they run windows so would be using putty to connect) and it didn't work for them either.

---

### Post by y@w on 2009-03-09
In the snippet you first posted it says you're trying to authenticate as "Administrator" with a capital A. But, on the prompt it shows "administrator" I'd make sure your capitalization is correct as well as spelling since the logs are showing "invalid user".

---

### Post by csc2ya on 2009-03-09
I completely forgot usernames were case sensitive. Just tried connecting from my phone with my username spelt correctly, and it now works.

Thanks

---

### Post by y@w on 2009-03-09
Hehe, it's always the simple things. 

:)

---

