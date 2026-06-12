---
title: "lost connectivity on ssh"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by type8code0 on 2010-08-21
Hi,

Suddenly I just lost connectivity to ssh server in Ubuntu Lucid. 
I can see that ssh service is running by checking on netstat -an, however I'm unable to connect it from other computer.

But when I ssh from localhost, I'm able to get in.
If you need more info, please let me know.
Thanks

> type8code0@desktop:~$ netstat -an | grep :22
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      1 192.168.1.14:22         192.168.1.15:4759       FIN_WAIT1  
tcp        0      0 192.168.1.14:22         192.168.1.15:4370       ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN     
type8code0@desktop:~$ 

> type8code0@desktop:~$ cat /etc/issue
Ubuntu 10.04.1 LTS \n \l

---

### Post by Iowan on 2010-08-21
Post */etc/ssh/sshd_config*

---

### Post by type8code0 on 2010-08-21
> **Iowan said:**
> Post */etc/ssh/sshd_config*
Thanks Iowan for your prompt reply :)

Here is my sshd config

> # Package generated configuration file
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
AllowUsers type8code0
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

---

### Post by type8code0 on 2010-08-21
192.168.1.14 is Ubuntu machine that running sshd service
192.168.1.15 is another computer that I use to connect into it

Even though the status is shown as established below, but I can't login into it after I lost the connectivity. (ssh 192.168.1.14)

There is no problem to ssh into localhost (ssh localhost)

> type8code0@desktop:~$ netstat -an | grep :22
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.14:22         192.168.1.15:4370       ESTABLISHED
tcp        0      0 192.168.1.14:22         192.168.1.15:4922       ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:22                  ::1:49027               ESTABLISHED
tcp6       0      0 ::1:49027               ::1:22                  ESTABLISHED
type8code0@desktop:~$ 


---

### Post by Iowan on 2010-08-21
Hmmm... :-k
I was hoping for something obvious - like a ListenAddress line.
Your config file looks much like mine - I don't have the **AllowUsers** line. Doubt it'll help, but you could comment it out - just to prove it's not responsible...

or try **ssh type8code0@192.168.1.14**

---

### Post by type8code0 on 2010-08-21
> **Iowan said:**
> Hmmm... :-k
I was hoping for something obvious - like a ListenAddress line.
Your config file looks much like mine - I don't have the **AllowUsers** line. Doubt it'll help, but you could comment it out - just to prove it's not responsible...

or try **ssh type8code0@192.168.1.14**

Thanks... Listen Address is where we change default ssh port rite which is tcp 22. 
I have put AllowUsers line so only certain user can login into ssh.

Btw, the other machine is windows and I'm using putty.

The other problem is sshd is still running even though I already stop it. 
> type8code0@desktop:~$ /etc/init.d/ssh status
 * sshd is running
type8code0@desktop:~$ 

type8code0@desktop:~$ sudo /etc/init.d/ssh stop
 * Stopping OpenBSD Secure Shell server sshd                                                                                                                    [ OK ] 
type8code0@desktop:~$ sudo /etc/init.d/ssh status
 * sshd is running

---

