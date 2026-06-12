---
title: "SSH - ssh_exchange_identification: Connection closed by remote host"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by Pougnet on 2011-02-28
Hello,
For a while now I have been trying to set up a personal ssh server but have encountered many difficulties.
When I try to connect using the command ssh -vv -p 8080 user@server it gives me many errors that i will post below.
```

OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to (server) [12.34.567.890] port 8080.
debug1: Connection established.
debug1: identity file /home/richard/.ssh/id_rsa type -1
debug1: identity file /home/richard/.ssh/id_rsa-cert type -1
debug1: identity file /home/richard/.ssh/id_dsa type -1
debug1: identity file /home/richard/.ssh/id_dsa-cert type -1
debug1: ssh_exchange_identification: HTTP/1.1 400 Bad Request


debug1: ssh_exchange_identification: Server: httpd


debug1: ssh_exchange_identification: Date: Tue, 01 Mar 2011 02:49:28 GMT


debug1: ssh_exchange_identification: Content-Type: text/html


debug1: ssh_exchange_identification: Connection: close


debug1: ssh_exchange_identification: 


debug1: ssh_exchange_identification: <HTML><HEAD><TITLE>400 Bad Request</TITLE></HEAD>

debug1: ssh_exchange_identification: <BODY BGCOLOR="#cc9999"><H4>400 Bad Request</H4>

debug1: ssh_exchange_identification: No request found.

debug1: ssh_exchange_identification: </BODY></HTML>

ssh_exchange_identification: Connection closed by remote host


```I have my personal router forwarding all traffic on port 8080 to the ssh server. I have setup the ssh daemon to listen on port 808 in my /etc/ssh/sshd_config which I will post below.
```

 Logging
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
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
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
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

```I dont know what else to try here, any help is greatly appreciated.
Best regards,
Pougnet

---

### Post by dmizer on 2011-03-01
Port 8080 is reserved for HTTP connections. It looks like you have a web server somewhere on your network that's picking up the connection instead of your ssh server. You should use a much higher range unassigned port for your ssh server connection. Take a look here for more information about ports: [http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

Also, I strongly urge you to use public key based authentication rather than passwords. If you use passwords and PAM, basically the only thing keeping your computer safe from the throngs is a password. This extremely undesireable. More information on key-based authentication here: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by Pougnet on 2011-03-01
I tried changing the listening port to 123456789 and set the router to forward all UDP traffic to the computer but still no success. If this will help, my router is a linksys e3000.  There is a new message when i use the verbose option on the ssh command that I will post below. About the encryption instead of password authentication one I get this working I will implement the systems you have suggested.
```

penSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to (server) [ip] port 123456789.
debug1: connect to address (ip) port 123456789: Connection refused
ssh: connect to host (server) port 123456789: Connection refused


```

---

### Post by gmargo on 2011-03-01
There's nothing wrong with using port 8080; however, you seem to have an http proxy running that listens on that port.

You cannot use port 123456789 because the port number is a 16-bit quantity, so that maximum port number is 65535.  Try something like 8022.

---

### Post by Pougnet on 2011-03-01
Okay, I tried using port 1336 but still no success. If you need any further information don't hesitate to ask. Thank you

---

### Post by dmizer on 2011-03-01
Once again, I'd like to take the opportunity to strongly advise against any kind of password based authentication, and refer you to the far superior encrypted public key based authentication instead. Most hacked Linux boxes are hacked because of poor security in remote desktop or SSH.

From looking at your sshd_config file, it looks like the only authentication method you have enabled is PAM. Have you configured PAM to allow logins, or are you using PAM in conjunction with an LDAP server?

Can you login to your SSH server from your SSH server? Can you log in from another box on the same network?

---

### Post by Pougnet on 2011-03-01
I have got the server to work after tinkering around with the port forwarding settings. Turns out I did not set a static ip for the computer to connect to the router, so when the DHCP assigned me a new address I was trying to connect to another computer. About the keys I am creating a pair of RSA keys as I type this. Thanks for all of your help.

---

### Post by dmizer on 2011-03-01
Glad to hear you've got this solved.

If you need any help with public key auth, I'll be happy to help.

---

