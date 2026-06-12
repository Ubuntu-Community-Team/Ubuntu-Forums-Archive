---
title: "SSH Permission Problem..."
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by Crafty Kisses on 2009-01-08
I'm having some issues logging into a OpenSSH-server running. I've seen a recent problem that was pretty similar to mine, but I have tried more things to solve the issue and I still receive the following error when I try to login, "Permission Denied (publickey)". So I'm really confused right now, I could login just fine like 2 weeks ago. I'm not too sure what changed in the time period, nothing to my knowledge. I checked my **/etc/ssh/sshd_config (daemon side)** for the following:
```
[~] > cat /etc/ssh/sshd_config | grep Protocol
Protocol 2
```
It's obviously there, I wanted to make sure everything was in working order. So I renabled SSH1. (I have an old Windows box I want to use CVS with) so I ran the following:
```
sudo ssh-keygen -t rsa1
```
I then looked at the following:
```
/etc/ssh/sshd_config
```
I obviously got the following from that:
```
Protocol 2,1
# Host Key for protocol rsa1
HostKey /etc/ssh/ssh_host_identity

# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
```
So then I restarted the SSH daemon by running the following:
```
sudo /etc/inid.d/ssh restart
```
So then I try to reconnect, and I still get the same error as before:
```
Permission Denied (publickey)
```
So, I did infact run the following:```
ssh -v localhost
```
This is what I got from that command:
```
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/codename/.ssh/identity type -1
debug1: identity file /home/codename/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/codename/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/codename/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/codename/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/codename/.ssh/identity
debug1: Trying private key: /home/codename/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
```
I'd also like to say that my SSH folder is chmod'd to 700. RSA authentication is enabled according to the config log, so I'm not really sure what's going on, I've been working on this for some time and have been unsuccessful, so any help would be greatly appreciated.

---

### Post by dmizer on 2009-01-08
Have a look here: [http://ubuntuforums.org/showthread.php?t=1031033](http://ubuntuforums.org/showthread.php?t=1031033) see if the solution I posted on page 2 might fix you as well.

---

