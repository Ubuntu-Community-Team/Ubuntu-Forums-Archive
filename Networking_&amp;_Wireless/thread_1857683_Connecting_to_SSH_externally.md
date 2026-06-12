---
title: "Connecting to SSH externally"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by olavgal on 2011-10-10
Hello,

I installed openSSH on my home computer, running ubuntu. I can connect to it easily from within the local network, but I can't connect to it at all externally. I've also tried connecting to my FTP server, but I can't seem to be able to do it. I have opened the ports needed for the programs aswell. I am using my-ip.tk to find my external IP aswell.. And one more thing, I was able to externally connect a minecraft server on my windows machine not long ago. 

Here is my openSSH config file
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

Could you guys help me find out what I'm doing wrong?

---

### Post by papibe on 2011-10-10
Hi olavgal, from where are you trying to connect? outside your network?  because it's very unlikely that your router will support connections to your external IP from your LAN.

Regards.

---

### Post by olavgal on 2011-10-10
I am trying to connect from outside my local network yes, with my external IP. I can however log in with my local IP while I'm on my local network, like you would expect.

---

### Post by papibe on 2011-10-10
A few questions:

- Does the server has DHCP reservation or an static LAN IP?
- Did you port forward the port 22 to your server?
- Have you tried using [http://canyouseeme.org/]("http://canyouseeme.org/") to see if the port is being block by your ISP?

Regards.

---

### Post by haqking on 2011-10-10
when you say you have opened the ports, are you referring to the machine itself ?

I trust the ports are forwarded on the router to the local machine ?

---

### Post by olavgal on 2011-10-10
> **papibe said:**
> 
- Does the server has DHCP reservation or an static LAN IP?
It does not have an static LAN IP, no. So I would assume that would mean it has DHCP reservation? Not completly sure what it means, but I assume it means it changes LAN IP once in a while :P

> **papibe said:**
> 
- Did you port forward the port 22 to your server?
Yes.

> **papibe said:**
> - Have you tried using [http://canyouseeme.org/](http://canyouseeme.org/) to see if the port is being block by your ISP?
Not that one exactly, but I've used other tools like it. And they said my port was open. I will try again though, to make sure. (Will have to do this in the morning, I'm in Europe you see :)

Thanks for the help so far!

---

### Post by olavgal on 2011-10-10
> **haqking said:**
> when you say you have opened the ports, are you referring to the machine itself ?

I trust the ports are forwarded on the router to the local machine ?

Yeah sorry. I mean I have forwarded the ports to my local machine on the router. Quite new to this, so not completly stable with the terms yet.

---

### Post by haqking on 2011-10-10
> **olavgal said:**
> Yeah sorry. I mean I have forwarded the ports to my local machine on the router. Quite new to this, so not completly stable with the terms yet.

ok so you are outside your network ? presumably not behind a device that blocks outgoing SSH connections ?

and you are connecting to your external IP (your home router) that is set to forward incoming requests for port 22 to your machine ?

all correct ?

what error on your device are you getting ? is it authorisation error ? connection timed out failure ? can you ping your WAN IP from outside your LAN ?

---

### Post by olavgal on 2011-10-10
> **haqking said:**
> ok so you are outside your network ? presumably not behind a device that blocks outgoing SSH connections ?

and you are connecting to your external IP (your home router) that is set to forward incoming requests for port 22 to your machine ?

all correct ?
All correct, altough. What kind of device would block outgoing SSH connections? When I'm home and trying to get it to work, I use my phones mobile net to try to connect externally. Altough, I have tried on other networks too, still the same problem. Just wondering incase I won't be able to connect from my phones net anyway. 

> **haqking said:**
> what error on your device are you getting ? is it authorisation error ? connection timed out failure ? can you ping your WAN IP from outside your LAN ?

I con not ping my WAN IP from outside my LAN no. I get connection timed out failure. (when trying to connect with SSH and when pinging)

---

### Post by olavgal on 2011-10-10
I just saw a huge flaw.. I had set the port to forward to 2222 for some reason. I will try again with the port forward set to 22.

---

### Post by olavgal on 2011-10-10
Well, I feel stupid now :) I was able to connect to the server, thanks alot guys! I am still not able to ping the server though, any ideas why?

---

### Post by Lisiano on 2011-10-10
Some routers intentionally block pings to reduce hacker-wannabe attacks, most assume that if the IP doesn't ping then it would be a waste of time to scan.

---

### Post by olavgal on 2011-10-10
Ah, okey. Thanks for the reply:)

---

### Post by haqking on 2011-10-10
> **olavgal said:**
> I just saw a huge flaw.. I had set the port to forward to 2222 for some reason. I will try again with the port forward set to 22.

ha well at least you got it sorted.

And yeah i suspect your router does not allow ping requests which is common.

remember to mark the thread as solved using thread tools, cheers

---

