---
title: "Passwordless SSH (using keys) not working (typical noob question)"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by corrado33 on 2012-02-15
I could SWEAR I'm doing this correctly. I have 2 computers on my home network. One running os X, one running linux. (Yes, I know this is the ubuntu forums, but it's the only linux forums I'm part of.) I want to connect to the linux box using passwordless ssh for scripts and stuff. Here are the steps I followed.
 
For reference, I'm going to refer to the computers as the SERVER (linux box) and the CLIENT (os X box). SSH is installed correctly on the server as I can successfully ssh into the box. (Pretty obvious.)
 
First I ssh into both boxs from the other box to add the .ssh folder correctly and put each other in the known_hosts file. 
 
Then, on the client, I generate keys using
 
```
ssh-keygen -t rsa
```
 
Or whatever variation I feel like using. I don't put a password on the keys as this is on my local network, and I'm not really that worried about people breaking in to my client box and stealing the key. 
 
So I hit enter thrice.
 
Then I scp over the .pub key to the server as the authorized_keys file using
 
(In the .ssh directory)
 
```
 
scp id_rsa.pub [COLOR=black]user@server:~/.ssh/authorized_keys[/COLOR]

```
 
(no other authorized keys there yet, so it's ok for me to just create the file)
 
Then I chmod 600 the authorized keys file (no idea why, was following a tutorial)
 
So I get this far and I can log in just fine using 
 
```
 
ssh user@server

```
It asks for my password and I enter it and it works fine.
 
Then I log in as root and go to /etc/ssh and edit the sshd_config file, changing these three values.
 
```
PermitRootLogin        yes
PasswordAuthentication    yes
UsePAM            yes

```
 
To "no".
 
Then I restart the ssh server on the server and try to log in from the client.
 
Using
 
```
ssh -v user@server
```
 
I get this as the result
 
```
 
Aether:.ssh user$ ssh -v user@server
OpenSSH_5.2p1, OpenSSL 0.9.8r 8 Feb 2011
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to server[server] port PORT.
debug1: Connection established.
debug1: identity file /Users/user/.ssh/identity type -1
debug1: identity file /Users/user/.ssh/id_rsa type 1
debug1: identity file /Users/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debia                                                                             n-6+squeeze1
debug1: match: OpenSSH_5.5p1 Debian-6+squeeze1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'server' is known and matches the RSA host key.
debug1: Found key in /Users/user/.ssh/known_hosts:6
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/user/.ssh/identity
debug1: Offering public key: /Users/user/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /Users/user/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).

```
 
Question: Why is it trying id_rsa and not id_rsa.pub. The public key is the one I transferred over to the server for the authorized hosts file....
 
I'm just really annoyed at this, I've semed to have done everything correctly, but it still doesn't work.

---

### Post by corrado33 on 2012-02-15
Meh, figured it out.  First off I was using a previously generated key for another ssh connection with a different (non default) name.  So if I ssh -i name_of_identiy it worked.  However, that key was protected by a password, so I just made a new set of keys and set those up and it worked just fine.  
 
Sorry for the useless post.  Well, hopefully it'll help someone.

---

### Post by Iowan on 2012-02-15
It'll be even more helpful if you mark it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :D

---

