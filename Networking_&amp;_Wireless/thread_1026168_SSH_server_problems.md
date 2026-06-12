---
title: "SSH server problems"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2008-12-30
I'm trying to setup an SSH server on an Ubuntu 8.10 machine that uses RSA key-based logins but I'm running into some difficulty. 

Normally on the server I would run:

```
$ sudo cat id_rsa.pub >> ~/.ssh/authorized_keys
```

to copy the public key to the authorized_keys file and 

```
$ sudo chmod go-w ~/
$ sudo chmod 700 ~/.ssh
$ sudo chmod 600 ~/.ssh/authorized_keys
```

to lock everything down and keep ssh happy. This used to work on Ubuntu 8.04 a couple of months ago. Now when I run (on the Client):

```
$ sudo ssh -i ~/.ssh/id_rsa username@192.168.1.100
```

however, i get:

```
Enter passphrase for key '~/.ssh/id_rsa': 
Permission denied (publickey).
```

It allows me to enter a password, and checks to make sure it's right (if pass is wrong, it asks again), but then
it always displays permission denied. After a couple of hours messing with it I discovered something strange. If
I simply copy the original id_rsa.pub to the server's Desktop and change sshd_config to read:

> AuthorizedKeysFile	%h/Desktop/id_rsa.pub

instead of:
> 
AuthorizedKeysFile	%h/.ssh/authorized_keys

the client begins to connect without any problems. At that point, the id_rsa.pub permissions are set to 644 on the Desktop. I changed those to 600 (which is what they are supposed to be as far as I know) and it worked just as well. If I move the id_rsa.pub file to the .ssh folder however with the same permissions and with the folder's permissions set to either 700, or 666, it doesn't work anymore (even though I edited sshd_config to reflect it's new name and location).

What's going on here? Why does ssh not want the public key in the ~/.ssh folder where it belongs?

---

### Post by terminator14 on 2008-12-31
After a few more hours of messing with it this is what I came up with. SSHD tries to open the public key with a user account and not as admin. Since "drone" is my only registered user account, and I didn't set a root password, that's what it tries to open it with. The permissions on the ~/.ssh have to be 700 and on the authorized_keys have to be 600, yet they still have to be able to be accessed by the user (the account sshd uses to try to open the public key). The only way that is possible is if the user owns both the authorized_keys file and the ~/.ssh directory.

Running:

```
sudo chown drone:drone ~/.ssh
sudo chown drone:drone ~/.ssh/authorized_keys
sudo chmod 700 ~/.ssh
sudo chmod 600 ~/.ssh/authorized_keys
```

worked. Is this a bug, where SSHD doesn't use a root account to try to open the public key, or am I doing something wrong?

---

### Post by terminator14 on 2008-12-31
Upon further testing I have created and run the following script on the Live CD of Ubuntu 8.10:

```
#!/bin/sh
#Setting up SSH - This code contains the configured sshd_config and id_rsa.pub within it
user='ubuntu'
sudo apt-get -y install ssh
sudo mkdir ~/.ssh
echo 'CONTENT OF id_rsa.pub' >> ~/.ssh/authorized_keys
sudo chmod go-w ~/
sudo chmod 700 ~/.ssh
sudo chmod 600 ~/.ssh/authorized_keys
sudo chown $user:$user ~/.ssh
sudo chown $user:$user ~/.ssh/authorized_keys
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.original
sudo rm /etc/ssh/sshd_config
echo 'THE ENTIRE SSHD_CONFIG PRECONFIGURED FOR RSA' > /etc/ssh/sshd_config
sudo /etc/init.d/ssh restart
```

using the proper private key on the client, I am able to connect without any problems. My question is: why do I need the:

```
sudo chown $user:$user ~/.ssh
sudo chown $user:$user ~/.ssh/authorized_keys
```

part, without which, the client cannot connect? Is that supposed to be how it works, is it a bug, or am I doing something wrong?

---

