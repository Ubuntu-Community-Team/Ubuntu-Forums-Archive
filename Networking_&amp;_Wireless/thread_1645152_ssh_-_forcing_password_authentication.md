---
title: "ssh - forcing password authentication"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by kevpatts on 2010-12-14
Hey all,

I have a production host with the ip address 192.168.3.1 and I can access it once I have VPN'd into a specific network. It uses key authentication only.

I also have a KVM virtual machine on my local box that has the same IP address, but does not require the VPN.

The problem I have is that I have to delete the known_hosts file whenever I connect to one and then want to connect to the other. I have them set up as (for example) "Server" and "vServer" in my ~.ssh/config file, and for I have:
```
Host Server
Hostname 192.168.3.1
IdentityFile ~/.ssh/live_host

Host vServer
Hostname 192.168.3.1
PasswordAuthentication yes
PubkeyAuthentication no
RSAAuthentication no
DSAAuthentication no
```

but when I try to log in (ssh -X vServer) I get:
```
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /home/user/.ssh/config
debug1: Applying options for lapp1
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.3.1 [192.168.3.1] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_rsa-cert type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: identity file /home/user/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
----removed for security reasons----.
Please contact your system administrator.
Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending key in /home/user/.ssh/known_hosts:1
Password authentication is disabled to avoid man-in-the-middle attacks.
Keyboard-interactive authentication is disabled to avoid man-in-the-middle attacks.
X11 forwarding is disabled to avoid man-in-the-middle attacks.
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: password
debug1: No more authentication methods to try.
Permission denied (password).
```

I've even disabled RSA and DSA authentication on the remote vServer and get exactly the same thing.

Any help appreciated.

---

### Post by surfer on 2010-12-14
you seem to have changed the key on your server. on the client try:
```
$ rm ~/.ssh/known_hosts
``` 
and then retry the ssh connection.

---

### Post by puppywhacker on 2010-12-14
Having two systems with the same IP address is dirty. The problem is that the hostkey is stored with the address you connect with and the hostkey, but the hostkey is different. So you should clone the hostkey (both private and public) from one system to the other and ssh will stop complaining about this.

```

/etc/ssh/ssh_host_key
/etc/ssh/ssh_host_key.pub

```

---

### Post by luvshines on 2010-12-14
I think you should be able to use ```

CheckHostIP no 
```
option under those particular Hosts sections in ssh_config.
This flag shud disable IP checking in known_hosts file (read man page ssh_config) for more info

---

### Post by puppywhacker on 2010-12-15
you mean setting
```
StrictHostKeyChecking no
```
in the ssh client configuration file /etc/ssh/ssh_config

---

### Post by kevpatts on 2010-12-15
Thanks for all your responses, but still have problems. puppywhacker's response will probably work, but I'm going to be using this for a large amount of hosts and this approach would be impractical.

Unfortunately removing strict host checking is not the problem. I can do this with the command as specified above, howeevr even when I do this, my client doesn't actually attempt password authentication. I get:```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user/.ssh/id_rsa
debug1: Trying private key: /home/user/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey,password).

```I didn't skip and logging lines in there, so as you can see it knows that password authentication is available, but doesn't attempt it. This is the problem I need to overcome.

---

### Post by luvshines on 2010-12-16
Just to be sure, have you checked if the server allows password authentication ?

---

### Post by kevpatts on 2010-12-16
Yes. If I delete the known_hosts file I can log in. But then I can't log in to our production hosts.

I think I have figured out a workaround. If I delete my known_hosts file and then log in to all my test hosts with a password it will store all of these in the known_hosts. Then in future it will complain about but successfully log into the production hosts, because they are using publickey validation.

Not ideal, but should work.

---

