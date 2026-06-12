---
title: "SSH - local network connects - external network does not connect"
date: 2012-04-17
forum: Networking &amp; Wireless
---

### Post by jollyc on 2012-04-17
Hi, I am having issues with SSH.

I have Ubuntu 12.04 installed but this was happening with 11.10 as well.

I used to always use password auth and never had a problem, then iirc, when I updated from 11.04 to 11.10 external SSH stopped but local SSH continued to work.

**SSH straight into the local system.**

```

jolly@fucktard:~$ ssh localhost
jolly@localhost's password: 
Welcome to Ubuntu precise (development branch) (GNU/Linux 3.2.0-23-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

Last login: Tue Apr 17 16:37:26 2012 from localhost
jolly@fucktard:~$ 

```

**No issues, but then when I try to SSH out and back through my dyndns hostname.**

**NOTE:** I have changed the dyndns host to be my.dyndns.org and I didn't use [email]jolly@my.dyndns.org[/email] as I am already logged in with that username.

```

jolly@fucktard:~$ ssh -vvv my.dyndns.org
...
Permission denied, please try again.
jolly@my.dyndns.org's password: 
debug3: packet_send2: adding 8 (len 50 padlen 6 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,password).
jolly@fucktard:~$ 

```

I have tried so many different things with /etc/ssh/sshd_config and /etc/ssh/ssh_config it's not funny.

I did find for internal SSH I had to modify my /etc/ssh/ssh_config to have the below lines, that I have now created ~/.ssh/config file with the below text.

```

Cipher 3des
Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160

```

**My /etc/ssh/sshd_config**
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


**My /etc/ssh/ssh_config**
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
#   ForwardX11 no
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
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

**My ~/.ssh/config**
```

Cipher 3des
Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160

```

**Complete output for jolly@fucktard:~$ ssh -vvv my.dyndns.org**
```

jolly@fucktard:~$ ssh -vvv my.dyndns.org
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /home/jolly/.ssh/config
debug3: cipher ok: aes128-ctr [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: aes192-ctr [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: aes256-ctr [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: arcfour256 [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: arcfour128 [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: aes128-cbc [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: cipher ok: 3des-cbc [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug3: ciphers ok: [aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc]
debug2: mac_setup: found hmac-md5
debug3: mac ok: hmac-md5 [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: mac_setup: found hmac-sha1
debug3: mac ok: hmac-sha1 [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: mac_setup: found umac-64@openssh.com
debug3: mac ok: umac-64@openssh.com [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug2: mac_setup: found hmac-ripemd160
debug3: mac ok: hmac-ripemd160 [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug3: macs ok: [hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160]
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to my.dyndns.org [EXTERNAL_IP_HIDDEN] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/jolly/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/jolly/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/jolly/.ssh/id_rsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/jolly/.ssh/id_dsa" as a RSA1 public key
debug1: identity file /home/jolly/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /home/jolly/.ssh/id_dsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/jolly/.ssh/id_ecdsa" as a RSA1 public key
debug1: identity file /home/jolly/.ssh/id_ecdsa type 3
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: identity file /home/jolly/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version dropbear_0.46
debug1: no match: dropbear_0.46
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "my.dyndns.org" from file "/home/jolly/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/jolly/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client 3des-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server 3des-cbc hmac-md5 none
debug2: dh_gen_key: priv key bits set: 188/384
debug2: bits set: 525/1024
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Server host key: RSA 09:53:5a:be:05:11:23:a1:4c:a8:52:f3:55:83:df:c9
debug3: load_hostkeys: loading entries for host "my.dyndns.org" from file "/home/jolly/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/jolly/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "EXTERNAL_IP_HIDDEN" from file "/home/jolly/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/jolly/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug1: Host 'my.dyndns.org' is known and matches the RSA host key.
debug1: Found key in /home/jolly/.ssh/known_hosts:1
debug2: bits set: 505/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/jolly/.ssh/id_rsa (0x7fc45db68830)
debug2: key: /home/jolly/.ssh/id_dsa (0x7fc45db68870)
debug2: key: /home/jolly/.ssh/id_ecdsa (0x7fc45db6a000)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/jolly/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering DSA public key: /home/jolly/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering ECDSA public key: /home/jolly/.ssh/id_ecdsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
jolly@my.dyndns.org's password: 

```

Remembering that passwords don't work.

I have my router port forwarding to the internal IP:22 and I have tried creating keys but the thing is, if you can't even SSH with password auth to begin with, you'll never be able to remotely scp the key to the remote server (even though, really, the remote server is the same box).

I would love to get this working again, as I've already said to a mate, I feel naked and lost without my external SSH connection.

---

### Post by jollyc on 2012-04-22
Bump. If this is in the wrong forum, please let me know and I'll re-post and close this thread.

---

### Post by jonobr on 2012-04-23
Hello


I may have missed this, but have you tried tracing on the box using tcpdump

```
sudo tcpdump -i any port 22 
```

Try to login in externally.
Do you see some packets,

---

### Post by jollyc on 2012-04-25
> **jonobr said:**
> Hello


I may have missed this, but have you tried tracing on the box using tcpdump

```
sudo tcpdump -i any port 22 
```

Try to login in externally.
Do you see some packets,

Yeah I do see packets, as shown below.

```

jolly@fucktard:~$ sudo tcpdump -i any port 22
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 65535 bytes
22:20:30.086529 IP fucktard.43025 > my.dyndns.org.ssh: Flags [S], seq 3774368985, win 14600, options [mss 1460,sackOK,TS val 23404289 ecr 0,nop,wscale 6], length 0
22:20:30.087080 IP my.dyndns.org.ssh > fucktard.43025: Flags [S.], seq 2436644910, ack 3774368986, win 5792, options [mss 1460,sackOK,TS val 93655048 ecr 23404289,nop,wscale 1], length 0
22:20:30.087107 IP fucktard.43025 > my.dyndns.org.ssh: Flags [.], ack 1, win 229, options [nop,nop,TS val 23404289 ecr 93655048], length 0
22:20:30.218329 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 1:24, ack 1, win 2896, options [nop,nop,TS val 93655179 ecr 23404289], length 23
22:20:30.218417 IP fucktard.43025 > my.dyndns.org.ssh: Flags [.], ack 24, win 229, options [nop,nop,TS val 23404322 ecr 93655179], length 0
22:20:30.218486 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 1:40, ack 24, win 229, options [nop,nop,TS val 23404322 ecr 93655179], length 39
22:20:30.218907 IP my.dyndns.org.ssh > fucktard.43025: Flags [.], ack 40, win 2896, options [nop,nop,TS val 93655180 ecr 23404322], length 0
22:20:30.223629 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 24:192, ack 40, win 2896, options [nop,nop,TS val 93655184 ecr 23404322], length 168
22:20:30.226209 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 40:920, ack 192, win 245, options [nop,nop,TS val 23404324 ecr 93655184], length 880
22:20:30.266762 IP my.dyndns.org.ssh > fucktard.43025: Flags [.], ack 920, win 3776, options [nop,nop,TS val 93655228 ecr 23404324], length 0
22:20:30.266788 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 920:1064, ack 192, win 245, options [nop,nop,TS val 23404334 ecr 93655228], length 144
22:20:30.267126 IP my.dyndns.org.ssh > fucktard.43025: Flags [.], ack 1064, win 4656, options [nop,nop,TS val 93655228 ecr 23404334], length 0
22:20:30.798011 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 192:640, ack 1064, win 4656, options [nop,nop,TS val 93655759 ecr 23404334], length 448
22:20:30.799071 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 1064:1080, ack 640, win 262, options [nop,nop,TS val 23404467 ecr 93655759], length 16
22:20:30.799469 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 640:656, ack 1080, win 4656, options [nop,nop,TS val 93655760 ecr 23404467], length 16
22:20:30.799513 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 1080:1128, ack 656, win 262, options [nop,nop,TS val 23404467 ecr 93655760], length 48
22:20:30.804561 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 656:704, ack 1128, win 4656, options [nop,nop,TS val 93655765 ecr 23404467], length 48
22:20:30.841463 IP fucktard.43025 > my.dyndns.org.ssh: Flags [.], ack 704, win 262, options [nop,nop,TS val 23404478 ecr 93655765], length 0
22:20:30.949432 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 1128:1192, ack 704, win 262, options [nop,nop,TS val 23404504 ecr 93655765], length 64
22:20:30.953210 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 704:760, ack 1192, win 4656, options [nop,nop,TS val 93655914 ecr 23404504], length 56
22:20:30.953231 IP fucktard.43025 > my.dyndns.org.ssh: Flags [.], ack 760, win 262, options [nop,nop,TS val 23404505 ecr 93655914], length 0
22:20:30.953345 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 1192:1712, ack 760, win 262, options [nop,nop,TS val 23404505 ecr 93655914], length 520
22:20:30.992790 IP my.dyndns.org.ssh > fucktard.43025: Flags [.], ack 1712, win 5536, options [nop,nop,TS val 93655954 ecr 23404505], length 0
22:20:31.561989 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 760:816, ack 1712, win 5536, options [nop,nop,TS val 93656523 ecr 23404505], length 56
22:20:31.562094 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 1712:2080, ack 816, win 262, options [nop,nop,TS val 23404658 ecr 93656523], length 368
22:20:31.562530 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 816:872, ack 2080, win 6416, options [nop,nop,TS val 93656523 ecr 23404658], length 56
22:20:31.562586 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 2080:2280, ack 872, win 262, options [nop,nop,TS val 23404658 ecr 93656523], length 200
22:20:31.602815 IP my.dyndns.org.ssh > fucktard.43025: Flags [.], ack 2280, win 7296, options [nop,nop,TS val 93656564 ecr 23404658], length 0
22:20:32.170136 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 872:928, ack 2280, win 7296, options [nop,nop,TS val 93657131 ecr 23404658], length 56
22:20:32.209460 IP fucktard.43025 > my.dyndns.org.ssh: Flags [.], ack 928, win 262, options [nop,nop,TS val 23404820 ecr 93657131], length 0
22:20:32.778005 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 928:984, ack 2280, win 7296, options [nop,nop,TS val 93657739 ecr 23404820], length 56
22:20:32.778024 IP fucktard.43025 > my.dyndns.org.ssh: Flags [.], ack 984, win 262, options [nop,nop,TS val 23404962 ecr 93657739], length 0
22:20:32.778528 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 984:1096, ack 2280, win 7296, options [nop,nop,TS val 93657739 ecr 23404962], length 112
22:20:32.778534 IP fucktard.43025 > my.dyndns.org.ssh: Flags [.], ack 1096, win 262, options [nop,nop,TS val 23404962 ecr 93657739], length 0
22:20:36.909128 IP fucktard.43025 > my.dyndns.org.ssh: Flags [P.], seq 2280:2424, ack 1096, win 262, options [nop,nop,TS val 23405994 ecr 93657739], length 144
22:20:36.909564 IP my.dyndns.org.ssh > fucktard.43025: Flags [.], ack 2424, win 8176, options [nop,nop,TS val 93661870 ecr 23405994], length 0
22:20:37.516790 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 1096:1152, ack 2424, win 8176, options [nop,nop,TS val 93662477 ecr 23405994], length 56
22:20:37.516813 IP fucktard.43025 > my.dyndns.org.ssh: Flags [.], ack 1152, win 262, options [nop,nop,TS val 23406146 ecr 93662477], length 0
22:20:37.517221 IP my.dyndns.org.ssh > fucktard.43025: Flags [P.], seq 1152:1208, ack 2424, win 8176, options [nop,nop,TS val 93662478 ecr 23406146], length 56
22:20:37.517228 IP fucktard.43025 > my.dyndns.org.ssh: Flags [.], ack 1208, win 262, options [nop,nop,TS val 23406146 ecr 93662478], length 0
22:20:52.373468 IP fucktard.43025 > my.dyndns.org.ssh: Flags [R.], seq 2424, ack 1208, win 262, options [nop,nop,TS val 23409860 ecr 93662478], length 0
^C
41 packets captured
41 packets received by filter
0 packets dropped by kernel
jolly@fucktard:~$ 

```

Don't know what to make of it though.

---

### Post by Ms. Daisy on 2012-04-25
Have you tried replacing the key? Maybe it got hosed/lost when you upgraded.

---

### Post by jonobr on 2012-04-25
Agree with Ms. Daisy, the problem is higher then connectivity.
(You may have suggested this already in the OP) however try replacing it, see if it works

cheers

jonobr

---

### Post by jollyc on 2012-04-26
> **Ms. Daisy said:**
> Have you tried replacing the key? Maybe it got hosed/lost when you upgraded.

I assume you mean generating new keys? Yep. Many times, correct permissions too.

```

chmod 600 ~/.ssh/*
chmod 700 ~/.ssh/

```

However, I never used keys before this and I would like to get things working without keys first.

---

### Post by Ms. Daisy on 2012-04-26
Wait, that just confused me. So you're saying you have removed the keys? Because the debug output and your config file indicates that ssh is still trying a key. 

I compared your sshd_config file to my own (which works) and the only difference is password authentication
```
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes
```
Change that to a no. I don't think you want a password and a key- I think it's an either-or.  Plus if you have passwords enabled, then you'll just get brute force attacks from the internet (especially if you keep ssh on port 22).

See these for more, there are also some troubleshooting methods listed in them:

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by cybercity@localhost on 2012-04-26
try ssh example.org -D 22 -l username

---

### Post by jollyc on 2012-04-26
Thanks for your reply Ms. Daisy. Sorry for confusing you, I never used to use keys but once the problem arose a while back, I have tried keys. I have generated keys so may times, it's not funny. But I tried again.

I have had PasswordAuthentication set to yes and no, with the same results.

This time, I removed my ~/.ssh folder and then created again, chmod 700 ~/.ssh and generated a new rsa key, restarted the service and I get this.

```

debug2: key: /home/jolly/.ssh/id_rsa (0x7fe8209ef1e0)
debug2: key: /home/jolly/.ssh/id_dsa ((nil))
debug2: key: /home/jolly/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/jolly/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/jolly/.ssh/id_dsa
debug3: no such identity: /home/jolly/.ssh/id_dsa
debug1: Trying private key: /home/jolly/.ssh/id_ecdsa
debug3: no such identity: /home/jolly/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
jolly@my.dyndns.org's password: 

```

That is with PasswordAuthentication set to no and a new rsa key. For some reason, it's not able to use the key properly.

BTW, I think you can have key and password auth available to you, because when I login just using ssh localhost, if there's no keys, it lets me use password and when there are keys, it asks me for the key passphrase.

Little bit odd huh :P

---

### Post by jollyc on 2012-04-26
> **cybercity@localhost said:**
> try ssh example.org -D 22 -l username

```

jolly@fucktard:~/.ssh$ ssh my.dyndns.org -D 22 -l jolly
Privileged ports can only be forwarded by root.
jolly@fucktard:~/.ssh$

```

I then tried it using

```

sudo ssh my.dyndns.org -D 22 -l jolly

```

and it's the same outcome as above.

---

### Post by Ms. Daisy on 2012-04-26
What exactly are you doing to create keys? are you following this guide:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

You create the key on the remote computer, then transfer them to the server.

edit: transfer to the server!

---

### Post by jollyc on 2012-04-27
Yep.

```

mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa

```

I then choose to save them in my ~/.ssh/ folder.

Not sure, what I could be doing wrong here.

I even changed the permissions of the files inside the ~/.ssh folder to be 600 as well but it doesn't work if I do nothing to the permissions or if I try chmod 600.

```

chmod 600 ~/.ssh/*

```

---

### Post by Ms. Daisy on 2012-04-27
So you ssh into the server, you create a key on the remote computer, then you transfer the public key to the server. Then you try to ssh into the server again and it fails. Is that correct?

You don't have an encrypted home, do you?  See the link I gave you for ssh keys if you do.

I'm pretty much out of ideas, sorry I couldn't help you more. Hopefully someone else can see what's going wrong.

---

### Post by kristianz on 2012-06-16
Bumping this because I have the exact same problem.

I have one local server, one local client and one remote client. I am able to login in to the server from the server itself, from the local client using the lan address and from the remote client using the external IP address. But I am NOT able to log in to server from either server itself or local client by using the external IP address.

I have deleted .ssh directories on all sides, enabled password authentication, so this has nothing to do with keys.

I cannot figure out why the server denies access when connecting from local machine using the external address. All other connections are accepted, that is local machine using local address and external machine using external address.

This is a problem because I'm trying to set up access from a machine that is currently on the lan, but will eventually be connecting from the outside. So I want to know that the setup works connecting using the external address.

---

### Post by Ms. Daisy on 2012-06-16
ssh'ing from inside the LAN through the external IP is not something I have tried. I believe some routers can't handle it, but I'm not certain on that. 

Have you tried ssh'ing from an external location to see if it works?  That would at least tell you whether it's the ssh configuration or the router that's the problem.

---

### Post by kristianz on 2012-06-16
> **Ms. Daisy said:**
> 
Have you tried ssh'ing from an external location to see if it works?  That would at least tell you whether it's the ssh configuration or the router that's the problem.

Thanks for you reply.

Yes, that works. I am able to log in from a client that is outside of the lan, but not from a client within the lan when using the external address.

I guess the router could be a culprit, but I'm able to *connect* to the ssh port of the server, I just get denied *login*: Permission denied (publickey,password). It seems the problem is with authentication, not something the lan router could interfere with.

---

