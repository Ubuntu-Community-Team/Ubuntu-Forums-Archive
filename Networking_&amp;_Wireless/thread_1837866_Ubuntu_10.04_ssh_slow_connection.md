---
title: "Ubuntu 10.04 ssh slow connection"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by heba on 2011-09-02
I am having troubles with ssh connection. I saw that is common in Ubuntu 10.04. However, I tried all the suggestions like: Use DNS no, and/or commenting 
#    GSSAPIAuthentication yes
#    GSSAPIDelegateCredentials no

but it still does not work. Any help will be appreciated!
Thanks,

---

### Post by ktrnka on 2011-09-02
If it is taking a long time to prompt you for a password edit your sshd_config file:

```
sudo nano /etc/ssh/sshd_config
```

Scroll down and uncomment:

#GSSAPIAuthentication no

to look like

GSSAPIAuthentication no

Then scroll down to the bottom and add:

UseDNS no


Save it with ctrl-x then press y and hit enter.
Next restart the ssh service:

```
sudo service ssh restart
```

---

### Post by heba on 2011-09-06
I upgraded to 11.04 and did the suggested modifications but still does not work :(
Here is my config file:

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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
GSSAPIAuthentication no
GSSAPICleanupCredentials no

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
UseDNS no

Thanks,

---

### Post by ktrnka on 2011-09-07
Another suggestion I found is to change the GSSAPIAuth in your /etc/ssh/ssh_config as the sshd_config change does not work for everyone (I guess... seems to be only a ubuntu problem. Works fine in Debian).

[http://technology911.blogspot.com/2011/03/ssh-and-scp-slow-to-prompt-for-password.html]("http://technology911.blogspot.com/2011/03/ssh-and-scp-slow-to-prompt-for-password.html")


Otherwise:


when connecting, try passing the -v parameter:

```
ssh -v user@host
```

And post the result. Also run:

```
dmesg
```

and if you see a bunch of eth up and downs, your switch or nic could be bad. (Has happened to me before).

Other suggestions I've read are to reboot your switch/router.

---

