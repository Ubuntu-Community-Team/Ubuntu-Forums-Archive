---
title: "PuttySSH with plink command problems"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by Sico2 on 2009-02-01
```
dakota@PC:~$ plink -v -v -i /media/disk/Install/xerobank.key 
username@plus.xerobank.com -P 443 -L 8080:httpproxy.xerobank.com:8080
Looking up host "plus.xerobank.com"
Connecting to 88.198.15.111 port 443
Server version: SSH-2.0-OpenSSH_4.3p2 Debian-8
We claim version: SSH-2.0-PuTTY_Local:_May_29_2008_14:47:39
Using SSH protocol version 2
Doing Diffie-Hellman group exchange
Doing Diffie-Hellman key exchange with hash SHA-1
Host key fingerprint is:
ssh-rsa 2048 b7:5f:c6:**:b0:36:9e:**:8c:**:87:c6:a4:**:6b:b9
Initialised ***-256 SDCTR client->server encryption
Initialised ****-*** client->server MAC algorithm
Initialised AES-256 SDCTR server->client encryption
Initialised ***-***server->client MAC algorithm
Reading private key file "/media/disk/Install/xerobank.key"
Pageant is running. Requesting keys.
Pageant has 0 SSH-2 keys
Configured key file not in Pageant
Using username "username".
Offered public key
Remote debug message: Forced command: /home/plus/.ssh/plus_login username
Remote debug message: Port forwarding disabled.
Remote debug message: X11 forwarding disabled.
Remote debug message: Agent forwarding disabled.
Offer of public key accepted
Authenticating with public key "imported-openssh-key"
Remote debug message: Forced command: /home/plus/.ssh/plus_login u9bbjuaul0dra5og6
Remote debug message: Port forwarding disabled.
Remote debug message: X11 forwarding disabled.
Remote debug message: Agent forwarding disabled.
Access granted
Opened channel for session
Local port 8080 forwarding to httpproxy.xerobank.com:8080
Allocated pty (ospeed 38400bps, ispeed 38400bps)
Started a shell/command
++++ CONNECTED ++++


```

Hi all,
I am trying to run encrypted connection on my notebook via provider’s server. I establish connection with username and password, as seen in the console. I then have been advised to change my firefox manual proxy settings for HTTP:localhost and port 8080, SOCKS Host:localhost, port 8085 with SOCKS4. After that I have no internet connection, proxy refused no connection. My provider said, once I establish connection (+++ CONNECTED +++) with them, the blockade comes from my side. The choices were either my ISP (doubtful), firewall, (disabled on router, no shorewall or anything), browser setting in about:config (done that) or some other application.

Does anyone have any idea what may cause this connection not to run? I have a standard Ubuntu 8.10 on an Acer5920G notebook

---

### Post by Dr Small on 2009-02-01
Looks to me that you just need to set Firefox's Network settings to use SOCKS proxy, localhost and port 8080. Leave the rest of the proxy fields blank.

---

### Post by Sico2 on 2009-02-01
Did that, several ways, I can't even count them, how many possibilities did I try already... nothing.

---

### Post by kevdog on 2009-02-01
I just want to clarify a few things

You can get an interactive shell using putty to login?

Do you have control of the server?  Can you post the sshd_conf file also?

---

### Post by Sico2 on 2009-02-02
The only possibility I can do with that server is that command I posted in konsole. Maybe I have some more access, but am not aware of it, am not that bright with networking either.


I've found ssh_config file. no sshd...

```
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
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

---

