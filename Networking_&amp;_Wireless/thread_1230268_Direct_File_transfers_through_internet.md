---
title: "Direct File transfers through internet"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by manolomanolo on 2009-08-03
Hi to all.

I'm looking for a gnu/linux tool similar to Simple Socket File Transfer (SSFT for MS Windows) in order to send files to remote user even when they are not included into our LAN:

[http://www.whitsoftdev.com/ssft/](http://www.whitsoftdev.com/ssft/)

I mean a tool allowing to transfer files without need to use email, IM clients (because that requires a MSN, Yahoo, ICQ etc account... and also restricts the file transfers to the file transfer speed of the related servers) or any other service requiring accounts as [DROPBOX]("https://www.getdropbox.com/") since it consists in "tell my friend to create a dropbox account, remind my friend to notice me when he has his own dropbox account, send my file to Dropbox web server, notice my friend when the transfer to the server is done, let's talk about the file when my friend finally downloaded the file from dropbox server, remove the file from dropbox server"

Someone say that my solution could be configuring a VPN or stuff like that. Hope there's a simpler way to do it, as in MS Windows using SSFT.

Thanks for your attention.

---

### Post by jamest09 on 2009-08-03
simple http or ftp download?

---

### Post by manolomanolo on 2009-08-03
whatever: the most important thing is not being obliged to create accounts or facing to incomprehensible configuration settings...

At this time I've been trying [BaShare]("http://code.google.com/p/bashare/")
Do you know something similar?

Do you think setting up an ftp server could be easy?

Thanks

---

### Post by prshah on 2009-08-04
> **manolomanolo said:**
> in order to send files to remote user even when they are not included into our LAN:

**EDIT: There is also a python version of ssft that will work on linux; download it from [http://sooda.dy.fi/ohjelmat/?id=SSFT](http://sooda.dy.fi/ohjelmat/?id=SSFT)**

[s]**EDIT 2: There is also ssft in the repositories; install it with the terminal (Applications-Accessories-Terminal) command **[/s] - Scratch that; it's not a file transfer program.

# OR #

You can setup an ssh server on your machine, then use scp / sftp to transfer files to / receive files from anybody.

The advantage of using sftp / scp as against "normal" ftp is that the traffic between the two computers is encrypted, and will not be readable if  "snooped" midway.

Setting up an SSH server is easy, but will require 15~20 minutes of your time. 

A quick-and-dirty setup will take the following pattern:
a. install SSH server```
sudo apt-get install openssh-server
```b. Edit the configuration parameters for the server (optional), eg. change default port, allowed users, etc```
sudo nano /etc/ssh/sshd_config
```c. Restart server for changed parameters to take effect```
sudo /etc/init.d/ssh restart
```d. Check if you are able to connect from the local machine```
ssh -p xxxx 127.0.0.1
```e. Check if you can connect from another machine on the lan```
ssh -p xxxx *server-machine-ip*
``` (Replace xxxx with custom port number as defined in /etc/ssh/sshd_config).

f. Perform port forwarding to allow your ssh server to be accessed from the outside world. See [http://www.portforward.com](http://www.portforward.com) for exact details based on the model of your Internet router. 

g. Try to access your machine from the Internet; note that the ssh server and the client trying to access the server cannot both use the same Internet connection (Eg, same LAN connection), so put the client on a different wireless or dial-up Internet connection.

h. Once you are able to access your ssh server from the outside, you can transfer files using the commandline with scp```
scp -P xxxx somefile yourserverip:/location
scp -P xxxx someremotecomputer:/location ~
```
i. Or you can use sftp with a number of GUI utilites, including Gnome's default file manager, Nautilus.

Post back if you need details / troubleshooting on any particular step.

---

### Post by manolomanolo on 2009-08-04
> EDIT: There is also a python version of ssft that will work on linux; download it from [http://sooda.dy.fi/ohjelmat/?id=SSFT](http://sooda.dy.fi/ohjelmat/?id=SSFT)
Not so simple: it's not the same having a GUI compared to command line. Also, how should I pass a link to someone else letting him/her to download my file in case of using ssft.py?

> b. Edit the configuration parameters for the server (optional), eg. change default port, allowed users, etc

That's my config file: what shout I modify?

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

Thanks for your help.

---

