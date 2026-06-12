---
title: "ssh &quot;server refused our key&quot; using putty"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by Post Monkeh on 2010-02-17
i had my phone working previously to ssh into my laptop using putty for symbian.

i do remember having a tiny bit of trouble getting the putty keys to work (in other words they didn't) but the guide i read on it suggested creating the keys with ssh-keygen -t rsa , moving the key into my authorised keys file with cat id_rsa.pub >> authorized_keys2  and taking the id_rsa file, loading it into puttygen, and saving the private key for my phone from there.

i did have this working before, but my phone started playing bunny fuggers last week and i had to wipe my memory card (key itself was stored on my phone memory, putty was stored on the memory card)  and upon reinstalling putty, i set it up again with the same keyfile, but i kept getting a "server refused our key" message.

so i've been trying on and off for the past couple of nights to get it working again but i cannot get the key to accept at all. i can login fine with my password, but it will not accept the key.  
i followed another guide that suggested using puttygen to make the keys then manually copying the right parts (missing out all the guff at the start and end) into my authorized_keys2 file, but it wouldn't work that way either.

i've tried from a windows box too so i don't think it's my phone.  here' a copy of my sshd_config and my authorized_keys2 file to see if there's anything stupid i'm doing.   

ps, i also read somewhere to chmod my .ssh folder to 700 and my authorized_keys2 file to 600, which i've done.

pps, i also read that it was important that the key info in the authorized_keys2 file was on one line, which it always has been.


```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 2241
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
AuthorizedKeysFile	~/.ssh/authorized_keys2

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
PasswordAuthentication yes

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
```
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAv7q48bG/ihRJQIncfaNAgtCGTp0z8ST4+1ZKf7/4JfgPGAEvFaARG/yGABjjBXbeXyckWbUQ61mAUYB2VmDQ8WfOtWT0+PeeycYz8PrI2oCvL8jOW6eMvfLFiOh5Cey0qCmqyEhyxgDUxHTcdNOgok4kRZ80nJ3rhpj3cUwyVd/m0NdLuQV0sgo1eXAUg3l4kt8G5w9ADmD1pl4+Z85CXQq/BalYGn4wWn50OwY7/hzmIEjdGN91vL4kxYoBpRXoxSOj8Aa1Wez5mz28CIFCpK50ytRhsPI5e1UjqQZhxfPK9x3J5wmfgPm9XTTCLnSkcmkPHV1Q22tRWxqC1Xiwkw== will@will-laptop
```

---

### Post by Post Monkeh on 2010-02-18
anyone?

---

### Post by Samuliko on 2010-02-27
Bump. I have same problem, so if someone knows solution please post it here.

---

### Post by zencoder on 2010-07-06
Is your home directory encrypted? If so, sshd can't read the authorized_keys2 until you've already logged in (creating a circular problem).

[http://ubuntuforums.org/showthread.php?t=1294683](http://ubuntuforums.org/showthread.php?t=1294683)  <= similar issues.

---

