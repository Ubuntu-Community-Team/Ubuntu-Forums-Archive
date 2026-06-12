---
title: "Configure passwordless logins... over ssh"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2011-04-05
Hello all, 

I am trying to build my own open source dropbox clone from this site. [http://fak3r.com/geek/howto-build-your-own-open-source-dropbox-clone/](http://fak3r.com/geek/howto-build-your-own-open-source-dropbox-clone/)

But when i run the two commands and try to login without a password prompt i get this error : Agent admitted failure to sign using the key.

below are the commands i used. Can anyone tell me why this is not working? 

ssh-keygen -b 2048 -f ~/.ssh/id_rsa -P ''

then 

ssh-copy-id [email]user@remote.host[/email]

Thanks, 

SlashWannabe94

---

### Post by slashwannabe94 on 2011-04-05
Hey guys, i managed to fix that error i was having before with a simple reboot. 

Now i am wondering why my main machine can ssh into my laptop connected over a wireless interface, yet the laptop cannot ssh into the main machine? 

Strange...

Can anyone help with this? 

Thanks, 

SlashWannabe94

---

### Post by matt_symes on 2011-04-05
Hi

Do they both have ssh server and ssh client on each of them ?

Kind regards

---

### Post by slashwannabe94 on 2011-04-05
Yes, they do.

But the laptop refuses to ssh into my main machine. I don't know why... This is really getting to me. Any help is much appreciated dude :) 

Thanks, 

SlashWannabe94

---

### Post by matt_symes on 2011-04-05
Hi

When trying to connect use the -v switch to get extra information. These can be stacked to get even more info.

eg

```
ssh -v user@host
ssh -vv user@host
ssh -vvv user@host
```

Have a look with these. If you need help post a more verbose log of what is happening when you try to connect.

Can your laptop also connect to local host address ?

Kind regards

---

### Post by slashwannabe94 on 2011-04-07
user@laptop:~$ ssh -vvv server@192.168.1.2
OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.2 [192.168.1.2] port 22.
debug1: connect to address 192.168.1.2 port 22: Connection timed out
ssh: connect to host 192.168.1.2 port 22: Connection timed out

I tried to connect this way from the laptop to my main machine (Server) and had no luck, but once again can connect from the server to the laptop. I have also just ran a ping to the server and do receive packets with no loss. 

Yes my laptop does ssh to 127.0.0.1. 

I see that the connection is timing out, but what could be causing this? a blocked port 22 on my server? I know it's not down to signal as i am getting 100%. 
If you have any ideas dude please discuss them. 

Thanks, 

SlashWannabe94

---

### Post by slashwannabe94 on 2011-04-07
Just thought that i would add. the laptop is connecting over wlan while the server is connecting over eth0. server does not have a wireless NIC.

---

### Post by matt_symes on 2011-04-07
Hi

You are using the default ssh port. Check the port is open on the server (From the sever or use the servers ip address). It should be as you can go the other way but....

```
sudo nmap -sS 127.0.0.1
```

Enter your password. It will not be echoed to the screen. You might have to install nmap

```
sudo apt-get install nmap
```

On your server do you have any firewall rules stopping connection

```
sudo iptables -F
```

will flush any rules (from the server).

You might want to post the output of (from the server)

```
cat /etc/ssh/sshd_config
```

Kind regards

---

### Post by slashwannabe94 on 2011-04-07
Hey using the "sudo iptables -F" worked. I can now ssh back and forth.  nmap states that port 22 (ssh) is open. and the output of my /etc/ssh/sshd_config is as follows

# Package generated configuration file
# See the sshd_config(5) manpage for details
ClientAliveInterval 60
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


P.s. Thanks so much man :)

---

### Post by slashwannabe94 on 2011-04-07
I just rebooted and am now back to square one. :(

---

### Post by gzarkadas on 2011-04-07
Since doing `iptables -F' on your server got ssh working, then it is the server's firewall that blocks port 22. Now that you have rebooted your server's init scripts (which setup the firewall among other things) have rerun and your server's port 22 is again blocked.

So, what you need to do is instruct your server firewall to open port 22 for being able to accept ssh connections. Do not just append the `iptables -F' in your init scripts (for example rc.local), this command disables entirely the firewall and is intended only for debugging purposes. If you need further assistance on this, you 'll have to specify what firewall front-end the server uses.

---

### Post by slashwannabe94 on 2011-04-08
My firewall is Firestarter :) 

SlashWannabe94

---

### Post by gzarkadas on 2011-04-08
This is a firewall I never used, so I cannot provide a ready-to-apply recipy :(. Use the manual at [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php); it appears at first glance that you have to use the Policy part of the Firestarter GUI in order to add an accept rule for new connections at port 22 on your server, but you'll have to work the details from the manual and the options appearing in the GUI.

---

