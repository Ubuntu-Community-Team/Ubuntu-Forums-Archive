---
title: "cannot ssh into github"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by rajivrnair on 2012-05-08
Hi
I have problems ssh-ing into github. I've followed all the guides but still no joy. It does not seem to be picking up my key. Here are the logs:

[B]nrajiv@blr-nairr-nw:~/.ssh$ ssh -vv github
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /home/nrajiv/.ssh/config
debug1: /home/nrajiv/.ssh/config line 1: Applying options for github
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to github.com [207.97.227.239] port 22.
debug1: connect to address 207.97.227.239 port 22: Connection refused
ssh: connect to host github.com port 22: Connection refused[/B]
-----------------------------------------------------------------

I did the following:
1. Uploaded my keys again and verified the fingerprint ([http://help.github.com/linux-verify-ssh/]("http://help.github.com/linux-verify-ssh/")).

2. Set up my ~/.ssh/config file with:
```
Host github
	User git
	Hostname github.com
	PreferredAuthentications publickey
	IdentityFile /home/nrajiv/.ssh/id_rsa
```

3. Updated my file permissions
[I]nrajiv@xxxxx:~/.ssh$ ls -ltr
total 12
-rw------- 1 nrajiv nrajiv  134 May  8 13:42 config
-rw------- 1 nrajiv nrajiv  402 May  8 13:44 id_rsa.pub
-rw------- 1 nrajiv nrajiv 1766 May  8 13:44 id_rsa

-- directory permissions
nrajiv@xxxxx:~$ ls -altr
drwx------  2 nrajiv nrajiv   4096 May  8 13:44 .ssh
[/I]


Still no joy. Can you help please? I'm on a 64-bit Ubuntu 12 LTS.

---

### Post by markbl on 2012-05-08
Follow the very first guide on github in the Beginner section. See [http://help.github.com/linux-set-up-git/](http://help.github.com/linux-set-up-git/). It explains how to set up your ssh key pretty clearly.

---

### Post by rajivrnair on 2012-05-08
Actually, I did. I had a working git ssh connection before I moved from 10.10 to 12 - which is why I think I must've missed something. Oh well, I guess I'll just re-install git and openssh to be sure.

---

### Post by markbl on 2012-05-08
> **rajivrnair said:**
> Actually, I did. I had a working git ssh connection before I moved from 10.10 to 12 - which is why I think I must've missed something. Oh well, I guess I'll just re-install git and openssh to be sure.
Did you copy your old ~/.ssh/id_rsa (private key) to your new home area? It has to pair with the id_rsa.pub (public key) you copied to github.

---

### Post by rajivrnair on 2012-05-08
> **markbl said:**
> Did you copy your old ~/.ssh/id_rsa (private key) to your new home area? It has to pair with the id_rsa.pub (public key) you copied to github.
Nope. I generated new keys and copied them over.

---

### Post by rajivrnair on 2012-05-21
Ignore this issue. It was due to some 'transparent' firewalls at work. I was able to conect to github on port 443.
Just add the following entry to your ~/.ssh/config file:
> Host github.com
        User git
        Hostname ssh.github.com
        PreferredAuthentications publickey
        IdentityFile ~/.ssh/id_rsa
        LogLevel DEBUG
        Port 443

---

