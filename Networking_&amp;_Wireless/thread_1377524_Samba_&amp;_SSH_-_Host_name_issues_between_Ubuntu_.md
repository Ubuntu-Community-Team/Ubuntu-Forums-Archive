---
title: "Samba &amp; SSH - Host name issues between Ubuntu computers"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by TJ6900 on 2010-01-10
Hello I'm new to these forums, and as usual, am really enjoying Ubuntu.

I have researched the problem and still can't come up with anything.

I have Samba properly set up on my home computer (9.10), my work computer (9.10) and my laptop(9.04). It has worked great, then suddenly out of nowhere, I can't connect by the assigned names I have given them, even though it has worked in the past. When I go into the network I get as far as seeing 'WORKGROUP' but can never actually get into the WORKGROUP. A little later my work computer did the exact same thing. Yet Windows computers can connect just fine using the host name I provided, but any Ubuntu machine of mine actually can't get onto the network to see everything else.

Now on to the twist... The workaround for this is to simply type in the IP address of the computer instead of the host name and then I can connect and use Samba just fine, no other problems. I have gotten by just fine doing this until I started using SSH protocol. I have to type the IP address in as well even though I assigned it a host name that did work for a bit. That isn't really that bad until I try to connect via SSH outside of my local area network. I want to connect to my home computer from my work computer but because, for some reason, the host names are not working, It doesn't broadcast them out there and thus (as far as my limited knowledge to Linux goes) Is the reason I can't SSH over the internet.

---

### Post by TJ6900 on 2010-01-10
[U]Here is my entire smb.conf file.
[/U]





[global]
    ; General server settings
    netbios name = tj
    server string = Home Linux Station
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

;   printing = CUPS
;   printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
;   path = /var/lib/samba/printers
;    browseable = yes
;    guest ok = yes
;    read only = yes
;    write list = root
;    create mask = 0664
;    directory mask = 0775

;[printers]
;    path = /tmp
;    printable = yes
;    guest ok = yes
;    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[tj]
    path = /home/tj
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0750
    directory mask = 0750
    ;force user = tj
    ;force group = tj






_And here is my sshd_config file:_








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

UsePAM yes



AllowTcpForwarding yes
AllowUsers tj

---

### Post by Iowan on 2010-01-10
Winbind *might* help with Samba problems - [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To has some details. For external access to your network, you'll need to port-forward on your router and (unless you have static address from your ISP) use a service like [no-ip.com]("http://www.no-ip.com/") or [dyndns.com]("http://www.dyndns.com/").

---

### Post by TJ6900 on 2010-01-10
> **Iowan said:**
> Winbind *might* help with Samba problems - [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To has some details. For external access to your network, you'll need to port-forward on your router and (unless you have static address from your ISP) use a service like [no-ip.com]("http://www.no-ip.com/") or [dyndns.com]("http://www.dyndns.com/").

I have gone through the entire How-To link a while ago. And I have my router to forward the ssh port which it seems to be doing.

---

### Post by TJ6900 on 2010-01-12
Solved! I feel so happy and yet so stupid at the same time. I just went through that 'How to' that was previously posted and the 3rd problem, of coarse, fixed it. The first time I went through the how to, I was frustrated and must have skimmed through it... sorry, my bad!

---

