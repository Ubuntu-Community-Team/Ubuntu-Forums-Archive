---
title: "SSH keypair authorization"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by kranny on 2009-12-13
I want to make a passwordless ssh to one of my server from desktop..So I created a public-private key


```
sample.desktop% ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/sample/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/sample/.ssh/id_rsa.
Your public key has been saved in /home/sample/.ssh/id_rsa.pub.
The key fingerprint is:
6b:28:cd:de:ec:25:5f:60:d8:66:e4:c7:f2:98:ef:28 sample@sample.desktop.tuxfreaks.com
sample.desktop% ls
id_rsa  id_rsa.pub  known_hosts
```
Then scp'ied to the server 
```
sample.desktop% scp id_rsa.pub  server1:~
Password:
Response:
id_rsa.pub                                    100%  246     0.0KB/s   00:00

```
Then copied the id_rsa.pub contents to authorized_keys on my server
```
server1$ cp ~/id_rsa.pub authorized_keys
server1$ ls
authorized_keys  id_rsa  id_rsa.pub  known_hosts
```

But its not working..I checked the file permissions and also the sshd_config for 
```

RSAAuthentication yes
PubkeyAuthentication yes
```

Did i miss something?

PS: I am using OpenSSH_3.7.1p2 on both my desktop and server

---

### Post by falconindy on 2009-12-13
'Not working' is very ambiguous. Are you getting denied? Are you getting a password prompt? Is the key not being accepted? More importantly, did you restart the ssh daemon after making the changes to the config?

Also, you wiped out (if any) currently known authorized keys by using 'cp'. In the future, you should use cat:
```
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
```
This will append the data in id_rsa.pub to the authorized_keys file.

---

### Post by kranny on 2009-12-13
No i am not getting a denied error but its still prompting for a password..Yes the daemon was restarted..there was no authorized_keys file in the .ssh so cp'ed it.

BTW is there any other way i cud achieve this like appending my trusted users to .rhosts file on server

---

### Post by falconindy on 2009-12-13
Then how are you connecting? Does your /etc/ssh/ssh_config file properly identify the private key file in your .ssh directory or are you using -i /path/to/key in the connect string?

rhosts can be used as well. It's basically a list of "trusted hosts" which won't be asked for a password if you connect from them. Depending on where you're connecting from, this may or may not be a good idea.

---

### Post by Lars Noodén on 2009-12-13
If you connect in the verbose, very verbose or very very verbose mode, then you can see the exact problem.  

```

#
ssh -i /home/sample/.ssh/id_rsa **-v** server1

#
ssh -i /home/sample/.ssh/id_rsa **-vv** server1

#
ssh -i /home/sample/.ssh/id_rsa **-vvv** server1

```

Also make sure that the permissions for the directory .ssh and the file authorized_keys are correct on the server.  sshd won't use them if the permissions are wrong.

```

chmod u=rwx,g=,o= /home/sample/.ssh/
chmod u=rw,g=,o= /home/sample/.ssh/authorized_keys

```

---

### Post by kranny on 2009-12-14
It is prompting me that the key i generated using ssh-keygen is not a RSA1 key file /home/sample/.ssh/id_rsa
```
sample.desktop% ssh -i /home/sample/.ssh/id_rsa -vvv server1
OpenSSH_3.7.1p2, SSH protocols 1.5/2.0, OpenSSL 0.9.6k 30 Sep 2003
debug1: Reading configuration data /etc/opt/third-party/openssh/ssh_config
debug1: Applying options for *
debug1: /etc/opt/third-party/openssh/ssh_config line 10: Deprecated option "RhostsAuthentication"
debug1: /etc/opt/third-party/openssh/ssh_config line 14: Deprecated option "FallBackToRsh"
debug1: /etc/opt/third-party/openssh/ssh_config line 15: Deprecated option "UseRsh"
debug2: ssh_connect: needpriv 0
debug1: Connecting to server1 [10.217.48.31] port 22.
debug1: Connection established.
debug3: Not a RSA1 key file /home/sample/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/sample/.ssh/id_rsa type 1
debug1: identity file /home/sample/.ssh/identity type -1
debug1: identity file /home/sample/.ssh/id_dsa type -1
debug3: Not a RSA1 key file /home/sample/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/sample/.ssh/id_rsa type 1
debug1: Remote protocol version 1.99, remote software version OpenSSH_4.3p2-FC-4.3p2-26.1a1
debug1: match: OpenSSH_4.3p2-FC-4.3p2-26.1a1 pat OpenSSH*
debug1: Local version string SSH-1.5-OpenSSH_3.7.1p2
debug1: Waiting for server public key.
debug1: Received server public key (1152 bits) and host key (1024 bits).
debug3: check_host_in_hostfile: filename /home/sample/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 26
debug3: check_host_in_hostfile: filename /home/sample/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 3
debug1: Host 'server1' is known and matches the RSA1 host key.
debug1: Found key in /home/sample/.ssh/known_hosts:26
debug1: Encryption type: 3des
debug1: Sent encrypted session key.
debug2: cipher_init: set keylen (16 -> 32)
debug2: cipher_init: set keylen (16 -> 32)
debug1: Installing crc compensation attack detector.
debug1: Received encrypted confirmation.
debug1: Doing challenge response authentication.
Password:
Response:

```

---

### Post by Lars Noodén on 2009-12-14
Use RSA2 instead.  RSA is for legacy systems and shouldn't be around any more.  See if that helps.

---

