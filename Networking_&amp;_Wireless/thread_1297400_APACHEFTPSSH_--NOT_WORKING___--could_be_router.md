---
title: "APACHE/FTP/SSH --NOT WORKING   --could be router?"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by adan_linux on 2009-10-21
Hey everybody..yesterday was my first time setting up a home desktop server with a good friend and like most linux users, we ran into some obstacles. Here's what we have done:

[U]Ubuntu 8.04 Desktop:

[/U]0 Setup wireless with D-Link WBR-1310 wireless router 
    & opened ports: 22,21,1024 / 1030, and 80
1. Installed Xampp
2 Installed ddclient
3 Installed ssh
4 Created DynDNS domain name

Programs 1 - 3 properly start up and I can access [http://localhost](http://localhost) effortlessly but I cannot access IP Address and domain name.  For example, when I try to ssh into the local IP address (with the right password), I get this:

adan@adan-desktop:~$ ssh (--IP Address--)
Password:
Password:
Password:
Permission denied (publickey,keyboard-interactive).

adan@adan-desktop:~$ ssh (--Domain Name--)
Password:
Password:
Password:
Permission denied (publickey,keyboard-interactive).

Could there be a firewall issue with this particular router that may cause opening and closing on the ports above or maybe some configuration problem not yet noticed. Please help and thank you in advance.

---

### Post by dmizer on 2009-10-21
Most consumer level routers are not capable of loop back. Since your request is originating and terminating on the same network and appears to be both coming from the internet and from your internal network, the router chokes.

Try adding your domain name to adan-desktop's /etc/hosts file like so:
```
127.0.0.1	localhost
127.0.1.1	adan-desktop
[COLOR="Red"]192.168.1.10[/COLOR] (--Domain Name--)

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
Change [COLOR="Red"]192.168.1.10[/COLOR] to your server's actual **LOCAL** IP (not the WAN IP)

Test your site from a remote location to be sure you have your router configured correctly for external access.

---

### Post by adan_linux on 2009-10-23
I went ahead and added the LOCAL IP address as you told me and still I am getting the same problem (from a remote computer).  While in debug mode, this is what my ssh is acting like:

adan@adan-desktop:~$ ssh -v adan@(--Domain Name--)
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to (--Domain Name--) [Local IP address] port 22.
debug1: Connection established.
debug1: identity file /home/adan/.ssh/identity type -1
debug1: identity file /home/adan/.ssh/id_rsa type -1
debug1: identity file /home/adan/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.2p1 FreeBSD-20050903
debug1: match: OpenSSH_4.2p1 FreeBSD-20050903 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '(--Domain Name--)' is known and matches the DSA host key.
debug1: Found key in /home/adan/.ssh/known_hosts:3
debug1: ssh_dss_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/adan/.ssh/identity
debug1: Trying private key: /home/adan/.ssh/id_rsa
debug1: Trying private key: /home/adan/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
Password:
debug1: Authentications that can continue: publickey,keyboard-interactive
Password:
debug1: Authentications that can continue: publickey,keyboard-interactive
Password:
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: No more authentication methods to try.
Permission denied (publickey,keyboard-interactive).


I have tried to search for the problem in both the sshd_config and ssh_config files but not really sure as to what validate the authentications....any ideas?

---

### Post by tzicatl on 2009-10-24
> **adan_linux said:**
> 
Programs 1 - 3 properly start up and I can access [http://localhost](http://localhost) effortlessly but I cannot access IP Address and domain name.  For example, when I try to ssh into the local IP address (with the right password), I get this:

adan@adan-desktop:~$ ssh (--IP Address--)
Password:
Password:
Password:
Permission denied (publickey,keyboard-interactive).

adan@adan-desktop:~$ ssh (--Domain Name--)
Password:
Password:
Password:
Permission denied (publickey,keyboard-interactive).

Could there be a firewall issue with this particular router that may cause opening and closing on the ports above or maybe some configuration problem not yet noticed. Please help and thank you in advance.

I ran into a similar problem with ubuntu server 8.04 LTS.

I'd recommend you to take a look at the /etc/ssh/sshd_config file and see if there are directives like: DenyUsers, AllowUsers, DenyGroups, AllowGroups or AllowUsers, etc.

Make shure you review and understand the configuration. It's rather simple so you might not have any problem. Also man sshd_config for further info.

my 0.02 cents.

Noe

---

### Post by tzicatl on 2009-10-24
> **tzicatl said:**
> I ran into a similar problem with ubuntu server 8.04 LTS.

I'd recommend you to take a look at the /etc/ssh/sshd_config file and see if there are directives like: DenyUsers, AllowUsers, DenyGroups, AllowGroups or AllowUsers, etc.

Make shure you review and understand the configuration. It's rather simple so you might not have any problem. Also man sshd_config for further info.

my 0.02 cents.

Noe

This is the config file on one of my servers. It works pretty well to date.
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

```

---

### Post by adan_linux on 2009-10-24
My sshd_config file is completely analogous to yours...maybe it could just be a router issue.  If this is the case, how can one test to see if it is in fact just the router?

---

