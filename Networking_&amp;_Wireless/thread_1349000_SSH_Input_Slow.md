---
title: "SSH Input Slow"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by edvar on 2009-12-07
I upgraded my home computer to karmic last month and started having issues with SSH. At first X Forwarding via SSH wasn't working anymore. ([https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/434799](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/434799)). Managed to fix it yesterday using the suggestion on the bug.

Two weeks ago I started to have another problem with SSH. Before that there was no issue. Typing or any kind on input on the terminal is unbearably slow. There's always a couple of seconds lag when I type anything. The connection stays up the whole day and there are no errors on the NIC of the karmic box. It doesn't seem to be a latency issue because whenever I ran an "apt-get update" or some command with a reasonably large output, the text rolls out on the screen without any lags.

I haven't installed any SSH updates as none has been released lately. I'm using kernel 2.6.31-16.

This is my ssh_config:

> # This is the ssh client system-wide configuration file.  See
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
ForwardX11Trusted yes
XAuthLocation /usr/bin/xauth
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
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication no
    GSSAPIDelegateCredentials no


I'm using Putty from a Windows XP box to connect. I have the same problem trying to connect with a Fedora 12 box.

I couldn't find any error on the logs.

Any ideas?

---

### Post by teward on 2009-12-07
is there an sshd_config file?  because ssh_config is for the ssh client on the computer, and not the ssh server config.

Also, is it possible your network just lags?

---

### Post by edvar on 2009-12-08
Ops... Sorry, my bad. Here it goes:

> # Package generated configuration file
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
PermitRootLogin no
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

UseDNS no


I don't think it's a network lag issue. Everything else works fine and, as I said, apt-get update/upgrade outputs show up as usual. The connection also stays up for the whole day. The problem is with the keyboard/mouse input itself.

---

### Post by edvar on 2009-12-09
It's definitely not a network issue. I just tried to ssh from my mac in my bedroom to my ubuntu box in my living room and I'm having the exact same issue: lag when I'm typing. Before I was trying to ssh from work over the internet.

---

### Post by Dr Small on 2009-12-10
> **edvar said:**
> It's definitely not a network issue. I just tried to ssh from my mac in my bedroom to my ubuntu box in my living room and I'm having the exact same issue: lag when I'm typing. Before I was trying to ssh from work over the internet.
And how does your last statement imply that it is not a networking issue?

---

### Post by Jive Turkey on 2009-12-10
is your server in the DMZ or having port22 routed to it?  You might try checking your router settings or reboot your router.

Is the problem only when you access over the internet and not when on your LAN/WLAN?

---

### Post by edvar on 2009-12-10
> And how does your last statement imply that it is not a networking issue?

When I created this thread I was experiencing the problem connecting from my Windows and Fedora boxes at work to my Ubuntu box at home. At the time I didn't bother to test SSH in the same LAN as the Ubuntu box. There are a couple of firewalls, switches and routers in between the office and my apartment. When I tried to SSH from my Mac in my bedroom, the only thing between it and my Ubuntu box is a wireless router (Airport Extremem). There are no errors/retransmissions on any on the NICs and also no errors at the wireless router itself. After the SSH test I streamed a movie from my Ubuntu box to my Mac and it worked flawlessly. Here is the output of Ubuntu's ifconfig: 

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:752896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:752896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:67590346 (67.5 MB)  TX bytes:67590346 (67.5 MB)

wlan1     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:x.x.x.x  Bcast:x.x.x.x  Mask:x.x.x.x
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2939044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5575756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1549156561 (1.5 GB)  TX bytes:2501565131 (2.5 GB)

wmaster0  Link encap:UNSPEC  HWaddr 
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


As you can see no errors and no dropped packets.


> is your server in the DMZ or having port22 routed to it? You might try checking your router settings or reboot your router.

Is the problem only when you access over the internet and not when on your LAN/WLAN?

Yes, my router forwards port 22 to my Ubuntu box when I try to connect from the Internet. However, as I mentioned before, the same problem is happening when I connect from my WLAN thus bypassing the wireless router (I have an Aiport Extreme responsible for all the traffic between computers in my WLAN and it's connected to a DSL Router which does only the Internet traffic).

---

### Post by edvar on 2009-12-14
I did some more testing and realized the SSH session works fine right after a reboot of the ubuntu box however after a couple of hours the problem comes back: slow input and normal output.

I rebooted the box remotely (SSH input slow as usual) and connected again right after the reboot. It's working fine now. I'm connecting from work.

Any ideas?

---

