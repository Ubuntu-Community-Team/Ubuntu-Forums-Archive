---
title: "ssh-server works local but gets &quot;Permission denied&quot; when remote-accessing"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by JimHolmstroem on 2010-11-01
Hello guys,

I have stumbled upon a problem when trying to get my openssh-server to work on my computer

It works perfect when running:

```

ssh jim@localhost //or
ssh jim@192.168.1.79

```and almost perfect when running:

```
ssh jim@85.225.12.345 //remote ip
```But then a get:
```

jim@85.225.12.345's password: //entering password (and yes I know its the right password)
Permission denied, please try again.

```And the banner (from the "Banner /etc/issue.net"-row in sshd_config) is missing, as not the case for the local-access

I have configured my routers NAT>Port Forwarding to:
Service Name: SSH
(all port things): 22
Server IP Address: 192.168.1.79
Protocol: TCP

I heard from a friend that I could try to reinstall ssh-server so I did try:
```

mv /etc/ssh/sshd_config /etc/ssh/sshd_config.safety
apt-get remove ssh-server
apt-get install ssh-server

```I'm running Ubuntu 10.04 if that makes any difference :)

Regards //Jim

---

### Post by Iowan on 2010-11-01
Brain is starting to get foggy here tonight, but I wonder if posting */etc/ssh/sshd_config* (if you're comfortable with that) might be helpful.

---

### Post by JimHolmstroem on 2010-11-02
The config-files, I hope there aren't any security issues publicizing theses files :) 

/etc/ssh/sshd_config:
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
LoginGraceTime 20
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
Banner /etc/issue.net

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

AllowUsers jim

```/etc/ssh/ssh_config: (maybe not necessary)
```


# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
   ForwardX11 yes
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
   Port 22
   Protocol 2
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

---

### Post by TSJason on 2010-11-03
Jim,

I would recommend taking a look at your system's auth log to see what's happening.

Run:
```

sudo tail -f /var/log/auth.log

```

While that's up, try doing your two tests again. Local first, and then remote. Compare the results to see any difference.

If there's no output in the log file from the remote ssh connection, then you aren't even getting a connection to the machine that you think you are - and you're entering your password into a (possibly) foreign server.

---

### Post by Iowan on 2010-11-03
A couple more questions...
When you **ssh jim@192.168.1.79** are you on the same machine - or a different machine on the same network? Is **ssh jim@85.225.12.345** done from the "local" side of the network - or from outside the router?

---

### Post by JimHolmstroem on 2010-11-04
/var/log/auth.log after connecting with jim@localhost from the same computer:
```

Nov  4 08:21:02 jim-desktop sshd[2608]: Accepted password for jim from ::1 port 35570 ssh2
Nov  4 08:21:02 jim-desktop sshd[2608]: pam_unix(sshd:session): session opened for user jim by (uid=0)

```/var/log/auth.log after connecting with jim@192.168.1.79 (probably the same  thing as localhost?) from the same computer:
```

Nov  4 08:23:42 jim-desktop sshd[2705]: Accepted password for jim from 192.168.1.79 port 47035 ssh2
Nov  4 08:23:42 jim-desktop sshd[2705]: pam_unix(sshd:session): session opened for user jim by (uid=0)

```And after connecting with ssh jim@85.225.12.345:
Nothing new in the log file :/ just gets the "jim@85.225.12.345's password: Permission Denied, please try again." from the terminal

I'm almost sure that it worked from another computer locally some day ago but now when trying to login from another computer on local network I get "ssh:connect to host 192.168.1.79 port 22: connection timed out" :S

I also tried jim@85.225.12.345 from another computer with my android phone as Internet connection (I think that it classifies as outside my local network) but got connection timed out as well :(

> If there's no output in the log file from the remote ssh connection,  then you aren't even getting a connection to the machine that you think  you are - and you're entering your password into a (possibly) foreign  server.     Hope I ain't giving away my password to someone else :O

Maybe I should just start over with a clean install of openssh-server ? How will I proceed without having some old ghost settings spooking around in the new install? :)

Thanks for your help dudes really appreciating it :)

---

### Post by TSJason on 2010-11-04
Jim,

It sounds like your install of ssh is working just fine. This is a networking issue.

Do you have your router configured to forward the ssh port out to the wan?

It may be that you have an internet device (modem) provided by your ISP that actually listens on port 22 already. You can try forwarding on an alternate port, like 2000 and then connection with "ssh -p 2000 jim@ipaddress"

---

### Post by JimHolmstroem on 2010-11-04
I checked it up and my Internet provider have blocked the ports 25, 135-139 and 445 (found on their FAQ) so that shouldn't effect the port 22 (also confirmed by forums where they used the same Internet provider with ssh over the port 22)

I tested port 54,2000 and a few more:
changed the NAT to (in this case 2000)
Service Name:Secure Shell Server (SSH)
External Start Port: 2000
External End Port: 2000
Internal Start Port: 2000
Internal End Port: 2000
Server IP Address: 192.168.1.79
Protocol: TCP
changed /etc/ssh/sshd_config line: "Port 22" to "Port 2000"
then /etc/init.d/ssh restart

```

jim@jim-desktop:~$ ssh jim@85.225.12.345 //yeah i missed the -p flag
jim@85.225.12.345's password: //entered password
Permission denied, please try again.

jim@jim-desktop:~$ ssh -p 2000  jim@85.225.12.345
ssh: connect to host 85.225.12.345 port 2000: Connection refused

```
:O so I get connection refused for port 2000 but not 22 from external ip but when connecting locally the port 22 is refused and 2000 working

I'm probably missing something trivial :(

---

### Post by TSJason on 2010-11-04
Jim,

If you connected to port 22 while you had the configuration set to port 2000, then something is still amiss. Are you sure your router is forwarding to the correct internal machine? Does it perhaps have a DMZ setting that is causing it to go wonky?

---

### Post by JimHolmstroem on 2010-11-04
I will try to call my Internet provider, they should know if something like that is going on :)

Thanks for the help so far and I will be back soon with updates on the result

Have a nice day :)

---

### Post by bobnw on 2011-01-24
**LOGIN WORKS USING PUTTY BUT NOT OPENSSH**

I had the same problem,  but I was able to login to my remote system using PuTTY.   PuTTY did not work for me because none of the paste text methods I found using Google worked. Could be because I am using a laptop with a touch pad,  but I have no problems with the other apps on this laptop (Toshiba A215 satellite with AMD 64 processor, Ubuntu 10.04).

After looking at the other posts in this tread, the prospects for a quick fix on the login problem do not look encouraging,  especially when login works fine on port 22 in PuTTY.

I am going to check out some other SSH clients and if I find one that logs in OK and pastes text I will let you know.

---

### Post by bobnw on 2011-01-24
**SOLVED FOR ME**

I used 
         # ssh server-user@ipaddress 
in the terminal to open a remote session and got "Permission denied.."   I found this format on Google,  but I do not know where.  

Later I saw someone report using the following format to open a remote session

       # ssh  user@ipaddress

This worked the first time.

Hope this helps.

---

