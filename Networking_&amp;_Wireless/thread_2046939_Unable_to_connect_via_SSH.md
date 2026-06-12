---
title: "Unable to connect via SSH"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by ag415 on 2012-08-23
Hello,

I am aware that I am not the only one who has posted about this problem on here. However, I have looked through the existing threads regarding this issue, and have tried a number of different solutions offered both here and on other websites, and I am still not having any luck with my problem. Thus, I am posting this thread in the hopes that someone might know what the cause of this problem is and how to resolve it.


The problem:
I have a server running Ubuntu 11.10 (GNU/Linux 3.0.0-15-server x86_64). This server has been working fine for almost a year. I installed all necessary services on the server such as openssh-server and was able to log in to this machine using SSH just fine up until just a few months ago.

For some odd reason, I am randomly unable to connect to my server from any Mac OSX workstation on the network. When I say "randomly", I mean that sometimes I am able to login, and other times I receive one of the following errors (note: my server's static LAN IP is 192.168.1.15):

```
me@mac$ ssh me@192.168.1.15
write: Broken pipe
```

```
me@mac$ ssh me@192.168.1.15
ssh: connect to host 192.168.1.15 port 22: Connection refused
```

I don't know what is causing this error, and I never receive this message when trying to connect from other machines such as another Ubuntu server. 

I ***have* **checked the firewall configurations on both my server, my macintosh, and the network firewall. There is nothing in the firewall configurations on any of these devices that would prevent me from connecting.

I also have checked the sshd configurations, everything seems to be in order. The server is configured to listen on port 22, and I am able to connect to it fine from my other Ubuntu server. This problem seems to only occur when trying to connect from my Mac. (And again, I did check the firewall settings on my Mac as well, there is nothing in them that would prevent my connection - the firewall is set up to allow ALL connections outbound and inbound)

Today, I was finally able to connect to my Ubuntu server after about 25 attempts. Shortly afterwards, I get this message:

```
me@myserver$ Read from remote host 192.168.1.15: Connection reset by peer
Connection to 192.168.1.15 closed.
```I tried to re-connect, and this was the result:
```

me@mac$ ssh me@192.168.1.15
ssh: connect to host 192.168.1.15 port 22: Connection refused
```I also tried executing the command in verbose mode, to see if it might help me identify the problem. This was the output:

```
me@mac$ ssh -vv me@192.168.1.15
OpenSSH_5.2p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.15 [192.168.1.15] port 22.
debug1: connect to address 192.168.1.15 port 22: Connection refused
ssh: connect to host 192.168.1.15 port 22: Connection refused
```I have tried removing the entries in my local known_hosts file as well as the one on the server's end. I also tried removing the entire file altogether, which also yielded no results. I tried completely uninstalling the openssh-server, openssh-client and other related services and re-installing them. I am still having this problem.

The reproducability of the problem seems to be totally random. Some times (usually after about 25-100 attempts) I am able to finally connect to my server. Other times, I just keep getting the connection refused error message. When I finally am able to log in, the server randomly disconnects me.

Does anyone know what is going on here? I am totally stumped. I have searched all over the web and through these forums to see if I could find an answer. I have tried numerous solutions and nothing I've tried seems to get me anywhere.

I would greatly appreciate it if anyone has some useful advice for dealing with this issue.

Thanks!

---

### Post by ag415 on 2012-11-13
Sorry to bump this thread like this... I posted this back in August but still haven't received any responses... Can anyone help with this problem? Is everyone just as stumped as I am?

I'd really appreciate a response...

Thanks.

---

### Post by dannyboy79 on 2012-11-13
what is the ip address of your MAC? can you also please post your sshd_config from the server so we can take a peak at the settings. Also, is there a user named "me" on the server? If so, does it's UID match the UID of the user "me" on your MAC?

---

### Post by ag415 on 2012-11-13
@dannyboy79

The LAN IP address of my Mac is dynamically assigned. Currently, it is 192.168.1.188. The LAN IP address of my server is static and is set to is 192.168.1.16

My username is not the same on my mac as my username on the server. I don't believe the UID is the same either. Would this be a problem? I access various servers with different usernames and UIDs all the time, so I don't understand why that would be an issue...

Here is the /etc/ssh/sshd_config from my server:

```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
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

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

```NOTE: In my original post, the IP for the server was set to 192.168.1.15. I changed it to 16 after realizing it was in conflict with another device on our network using the same IP. Currently, the server is the only machine with the IP address 192.168.1.16. Changing the IP did not, however, fix the problem I am having connecting via SSH.

---

### Post by cjhabs on 2012-11-13
I vaguely recall getting a "Write broken pipe" message a while back which was some setting in my dot files in my home folder. I can't recall any details - sorry.

---

