---
title: "can't connect via ssh"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by grey_1 on 2010-08-03
Hi all, 

FYI I'm not new to linux, but I am new to learning it :) please forgive any blunders I may make here...

I'm running 10.04 on both desktop and laptop and am attempting to ssh between the two, but get a "permission denied" after entering the password.

What my question is (If so I'll feel silly:D) I have changed my LAN IP from the default to another number at an I.T. friends suggestion - is there a possibility I'm unwittingly attempting to ssh into another users box that may have the same number?

I've also disabled ufw hoping it was a fw issue, but I haven't found much that specifically mentions any other config required for setting up ssh.

Kind of at a loss here, so any suggestions would be most welcome.

Thanks in advance!

---

### Post by Iowan on 2010-08-03
Just gotta check - did you install SSH-server on one (or both) of the machines? The SSH client comes pre-installed, but you'll need to add the server - it's in the repo's.

---

### Post by grey_1 on 2010-08-04
Hi Iowan - yes, server and client are installed on both machines.

Thanks for the reply.

---

### Post by denver on 2010-08-04
The output from:

```
ssh -vv user@host
```

might give us a better ideea where the problem pops up. Permission denied is usualy returned by the shell, not by the ssh daemon itself (can't be certain though).

---

### Post by grey_1 on 2010-08-04
> **denver said:**
> The output from:

```
ssh -vv user@host
```

might give us a better ideea where the problem pops up. Permission denied is usualy returned by the shell, not by the ssh daemon itself (can't be certain though).

Hi denver, thanks for the reply. Here's the output.

> phil@Gen2:~$ ssh -vv Gen1@10.10.90.4
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 10.10.90.4 [10.10.90.4] port 22.
debug1: Connection established.
debug1: identity file /home/phil/.ssh/identity type -1
debug1: identity file /home/phil/.ssh/id_rsa type -1
debug1: identity file /home/phil/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 138/256
debug2: bits set: 514/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '10.10.90.4' is known and matches the RSA host key.
debug1: Found key in /home/phil/.ssh/known_hosts:1
debug2: bits set: 510/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/phil/.ssh/identity ((nil))
debug2: key: /home/phil/.ssh/id_rsa ((nil))
debug2: key: /home/phil/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/phil/.ssh/identity
debug1: Trying private key: /home/phil/.ssh/id_rsa
debug1: Trying private key: /home/phil/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
Gen1@10.10.90.4's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.


I know the password is correct, I've even reset them a couple of times to be sure I'm not being fumble fingered. Any insight is greatly appreciated.

---

### Post by denver on 2010-08-04
Looks like its the ssh server that's returning that error. Your best bet to find out the real problem, is to look at the ssh logs on the server itself.

Just do a:

```

tail -f /var/log/auth.log

```

while trying to log in and you will probably get a clue as to whats wrong. If nothing pops up, that you are ssh-ing to the wrong machine :).

Thats a generic error that can pop up in different situations (most common is login credentials are wrong).

---

### Post by grey_1 on 2010-08-04
Thanks for the reply denver - I will do that as soon as I get home today.

I sure hope I'm not trying to connect to someone else:oops:

Thanks again.

---

### Post by grey_1 on 2010-08-04
Post Edited:

I entered that command wrong - second attempt I got this.

> phil@Gen2:~$ tail -f /var/log/auth.log ssh Gen1@10.10.90.4
==> /var/log/auth.log <==
Aug  4 16:01:53 Gen2 sudo:     phil : TTY=pts/0 ; PWD=/home/phil ; USER=root ; COMMAND=/usr/bin/ssh Gen1@10.10.90.2
Aug  4 16:03:40 Gen2 sshd[2230]: Invalid user Gen1 from 10.10.90.4
Aug  4 16:03:40 Gen2 sshd[2230]: Failed none for invalid user Gen1 from 10.10.90.4 port 41470 ssh2
Aug  4 16:03:48 Gen2 sshd[2230]: pam_unix(sshd:auth): check pass; user unknown
Aug  4 16:03:48 Gen2 sshd[2230]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=gen2.local 
Aug  4 16:03:48 Gen2 sshd[2230]: pam_winbind(sshd:auth): getting password (0x00000388)
Aug  4 16:03:48 Gen2 sshd[2230]: pam_winbind(sshd:auth): pam_get_item returned a password
Aug  4 16:03:50 Gen2 sshd[2230]: Failed password for invalid user Gen1 from 10.10.90.4 port 41470 ssh2
Aug  4 16:17:01 Gen2 CRON[2593]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  4 16:17:01 Gen2 CRON[2593]: pam_unix(cron:session): session closed for user root
tail: cannot open `ssh' for reading: No such file or directory
tail: cannot open `Gen1@10.10.90.4' for reading: No such file or directory


Si I'm fairly certain I'm doing something wrong - just don't know what.

Thanks

---

### Post by denver on 2010-08-05
Log says that there is no such user (Gen1) on your machine:

```
Aug 4 16:03:40 Gen2 sshd[2230]: Invalid user Gen1 from 10.10.90.4
```

The user you are trying to login as, must exist on the target system (ssh server itself). For example, "phil" seems to be a valid user.

If you want to login as Gen1, you must first create the user:

```
adduser Gen1
```

NOTE: in GNU/Linux case MATTERS :). "Gen1" and "gen1" are NOT the same. So if your going to create a username starting with a capital letter, you will need to login using the same notation. (same goes for passwords, or anything else for that matter)

After creating the user, try:

```
ssh Gen1@10.10.90.2
```

NOTE2: The tail command only needs a filename as an argument :). Doing:

```
tail -f /var/log/auth.log
```

should suffice

---

### Post by grey_1 on 2010-08-05
I think I may have been hacked. I got message saying I was being eavesdropped on (man in the middle attack).

I tried to log in to C&P the message, but haven't been able to log in until now. I may just give up on this for now...now that paranoia has set in. 

One answer I would like is just how sensitive is the info I posted? I reconfigured my router and am reinstalling Ubuntu just to be safe. I hate this hacker crap.

---

### Post by grey_1 on 2010-08-05
Anyone please? I'm hoping to migrate fully to Ubuntu over the next couple of weeks (4 computers) so this is important to me.

The main reason I'm being wary here is a caution out of a tutorial I found in these forums.

[http://support.suso.com/supki/SSH_Tutorial_for_Linux](http://support.suso.com/supki/SSH_Tutorial_for_Linux)

And this is the exact message I received.

> @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ @ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @ @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@ IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY! Someone could be eavesdropping on you right now (man-in-the-middle attack)! It is also possible that the RSA host key has just been changed. The fingerprint for the RSA key sent by the remote host is 96:92:62:15:90:ec:40:12:47:08:00:b8:f8:4b:df:5b. Please contact your system administrator. Add correct host key in /home/suso/.ssh/known_hosts to get rid of this message. Offending key in /home/suso/.ssh/known_hosts:53 RSA host key for arvo.suso.org has changed and you have requested strict checking. Host key verification failed.

Please? :)

Thanks in advance

EDIT: That is C&Pd out of the tut, so that's not the original RSA key

---

### Post by denver on 2010-08-06
That message usually happens when you reinstall your server, or when you regenerate the ssh server's RSA keys. It also happens when another server is using an IP address that used to belong to someone else that you ssh-ed to at one time (hence the man in the middle warning). It is not necessarily an atack, it may just be a configuration change.

If you know its safe, you can get rid of that error by deleting line 53 from:

/home/suso/.ssh/known_hosts

 As for the info you posted, as long as it does not include any passwords, or secrets you are safe. Be sure to set a nice, long random password (8 characters made up of lower and upper case letters, numers and simbols). If you can help it, you should disable password authentication and just use public/private keys to autenticate.

---

### Post by grey_1 on 2010-08-06
> **denver said:**
> That message usually happens when you reinstall your server, or when you regenerate the ssh server's RSA keys. It also happens when another server is using an IP address that used to belong to someone else that you ssh-ed to at one time (hence the man in the middle warning). It is not necessarily an atack, it may just be a configuration change.

If you know its safe, you can get rid of that error by deleting line 53 from:

/home/suso/.ssh/known_hosts

 As for the info you posted, as long as it does not include any passwords, or secrets you are safe. Be sure to set a nice, long random password (8 characters made up of lower and upper case letters, numers and simbols). **_If you can help it, you should disable password authentication and just use public/private keys to autenticate._**
I will do that denver - again, thanks so much for your time and help.

---

