---
title: "Another sshd question"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by HypNemes on 2010-10-06
Hi all

Just recently installed sshd openserver and I have it started and listening on normal port 22.

My little network is pretty basic.

I have my router connected to the internet and my 2 pc's connected to the router.

1 pc is the new ubuntu box/install and the other pc is a windows 7 install.

Im trying to ssh from the win box using putty to the ubuntu box.
But i keep getting the error
"server refused our key"
"Disconected, No supported authentication methods available"

Anyone explain to me what im doing wrong or missing out?

The conenction is being made - just its not authorising somehow..

At least thats how im seeing it.

Hyp

PSS EDIT -> I'm very new to linux.

---

### Post by joberly on 2010-10-06
Please post the contents of your /etc/sshd_config.

There are two ways to authenticate with SSHd, either with Key based authentication (which is what it seems to be *attempting*) and simple password based. You can set which you prefer in the config file.

---

### Post by Iowan on 2010-10-06
I'm missing specifics, but *seem* to remember reading that PuTTY-generated keys need to be converted to work with OpenSSH.

---

### Post by HypNemes on 2010-10-07
Thanks for the replies people :)

As requested copy/paste of /etc/sshd_config below......

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
StrictModes no

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys

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
PasswordAuthentication no

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
```


Re the converting keys made by putty - for use withOpenSSH - thats totaly something I havent heard off or expected...
If so then that may very well be it.. can you ellaberate further any??

Hyp

---

### Post by luvshines on 2010-10-07
This helps ??
[http://wiki.contribs.org/SSH_Public-Private_Keys](http://wiki.contribs.org/SSH_Public-Private_Keys)

---

### Post by joberly on 2010-10-07
Your SSHd config file has the following line:

PubkeyAuthhentication yes

which in short means that you need to generate a key-pair to use this style of login credential. I think since you are new, this is possibly beyond the scope of what you're trying to do *_right now_*.

If you simply want to verify that your SSH server is working, you can set that parameter to no.

PubkeyAuthentication no

and also set 

PasswordAuthentication yes

This will allow you to login with your username and password. (Don't forget to restart sshd after you make changes to the config by issuing the command "service sshd restart".)

This is only recommended within your internal network, and really not advisable via connecting over the internet.

I'd suggest reading "luvshines" link, as well as reading up on how SSH works within the Ubuntu Server guide.

[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

Good luck!

---

### Post by HypNemes on 2010-10-08
Ive managed to do as u described - and connected to the sshd box using password auth with no problems.

I really would like to be able to get a more secure form of auth going however.
Generating the keys on the sshd server was no problem - and copying keys from the putty/windows machine across to the sshd server is doable - however - still no luck.

Keep getting the same authentication error.

Thanks for the assisstance..

Hyp

---

### Post by joberly on 2010-10-08
Try this guide here. It will give you a good overview of SSH Keys and also show you how to implement them.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

