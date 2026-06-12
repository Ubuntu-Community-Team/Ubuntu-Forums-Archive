---
title: "ssh tunnels and port forwarding"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2013-03-15
I SSH in to my server with the ISPs router doing portforwarding

ie ssh -p 2222 [email]me@myserver.com[/email]  and 2222 is forwarded to 192.168.1.1:22

I now want to connect to my mailbox on server , and relay through exim on the server. the client to set up the tunnel is putty (on windows 7 im afraid)
so I want to forward 1143 on the win7machine to 192.168.1.1:143 through the tunnel which itself is portforwarded through the router 
and 2225 on on win7machine to myserver:25
there is no access from the outside world to 143 or 25 through the ISP router.

but it doesnt work. 
Iv added a tunnel in putty L 1143   myserver.com:143

I've installed the windows telnet client 
Once ive connected with putty .
i do telnet localhost 143  from cmd.exe gives  blank screen which reverts to the command prompt after about 10 secs. Without the tunnel I get an error message ( so the putty config is doing something ! ) 

$ grep ^[A-Za-z] /etc/ssh/sshd_config
Port 22
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes
AllowTcpForwarding yes
GatewayPorts       yes



anyone know how to sort this out further

---

### Post by pdc124 on 2013-03-17
ive been investigating a bit further.  The tunnel through the portforward works  fine from a remote linux  client , so thats not the problem. 
Ive tried setting up the tunnel using plink - Win7 and Win7/XP SP3 compatibility mode - the result is the same 
I can set up the tunnel with plink 
C:\Program Files\PuTTY> plink -v -P 2222 -N -l me   -L 127.0.0.1:1143:myserver.com:143 myserver.com
Looking up host "myserver.com"
Connecting to 62.xx.xx.xx port 2222
Server version: SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
Using SSH protocol version 2
We claim version: SSH-2.0-PuTTY_Release_0.62
Doing Diffie-Hellman group exchange
Doing Diffie-Hellman key exchange with hash SHA-256
The server's host key is not cached in the registry. You
have no guarantee that the server is the computer you
think it is.
The server's rsa2 key fingerprint is:
ssh-rsa 2048 36:fc:f1:cd:4f:b3:dd:2a:c3:e5:bc:58:43:26:3b:6d
If you trust this host, enter "y" to add the key to
PuTTY's cache and carry on connecting.
If you want to carry on connecting just once, without
adding the key to the cache, enter "n".
If you do not trust this host, press Return to abandon the
connection.
Store key in cache? (y/n) y
Host key fingerprint is:
ssh-rsa 2048 36:fc:f1:cd:4f:b3:dd:2a:c3:e5:bc:58:43:26:3b:6d
Initialised AES-256 SDCTR client->server encryption
Initialised HMAC-SHA1 client->server MAC algorithm
Initialised AES-256 SDCTR server->client encryption
Initialised HMAC-SHA1 server->client MAC algorithm
Using username "me".
[email]me@myserver.com[/email]'s password:
Sent password
Access granted


heres the outp0ut from sshd as that is going o 

root@server2:~# /usr/sbin/sshd -d 
debug1: sshd version OpenSSH_5.8p1 Debian-7ubuntu1
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug1: Bind to port 22 on ::.
Server listening on :: port 22.
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 7 out 7 newsock 7 pipe -1 sock 10
debug1: inetd sockets after dupping: 3, 3
Connection from 149.xx.xx.xx port 37733
debug1: Client protocol version 2.0; client software version PuTTY_Release_0.62
debug1: no match: PuTTY_Release_0.62
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
debug1: permanently_set_uid: 104/65534
debug1: list_hostkey_types: ssh-rsa,ssh-dss
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: client->server aes256-ctr hmac-sha1 none
debug1: kex: server->client aes256-ctr hmac-sha1 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST_OLD received
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: KEX done
debug1: userauth-request for user me service ssh-connection method none
debug1: attempt 0 failures 0
debug1: PAM: initializing for "me"
debug1: PAM: setting PAM_RHOST to "149.xx.xx.xx"
debug1: PAM: setting PAM_TTY to "ssh"
debug1: userauth-request for user me service ssh-connection method password
debug1: attempt 1 failures 0
debug1: PAM: password authentication accepted for me
debug1: do_pam_account: called
Accepted password for me from 149.xx.xx.xx port 37733 ssh2
debug1: monitor_child_preauth: me has been authenticated by privileged process
debug1: PAM: establishing credentials
User child is on pid 25851
debug1: SELinux support disabled
debug1: PAM: establishing credentials
debug1: permanently_set_uid: 1001/1001
debug1: Entering interactive session for SSH2.

and then it hangs 

when I try telnet localhost 1143 from the remote client ,the server  responds 

debug1: server_init_dispatch_20
debug1: server_input_channel_open: ctype direct-tcpip rchan 256 win 16384 max 16384
debug1: server_request_direct_tcpip: originator 0.0.0.0 port 0, target myserver.com port 143
debug1: connect_next: host myserver.com ([62.xx.xx.xx:143) in progress, fd=16
debug1: channel 0: new [direct-tcpip]
debug1: server_input_channel_open: confirm direct-tcpip

and then it just sits there until i kill the connection ( or it times out) from the remote client

---

