---
title: "ssh public key authentication only works when already logged in"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by mrrusof on 2010-01-06
Hi!

I have an ssh (OpenSSH_5.1p1 Debian-6ubuntu2) client A and a server B set up for public key authentication as described in [https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

The problem is the following: ssh asks for a password when connecting from A to B without any other ssh session going on between A and B; but if I connect from A to B whenever there is another ssh session between A and B, either I get prompted for the passphrase I used to encrypt the private key or I get logged automatically.

I already checked permissions on B: .ssh is 700 and authorized_keys is 600. I already tried "StrictModes no" in sshd_config. Printing debug information using DEBUG3 does not any useful insight. Moreover, there is no /var/log/secure (is it supposed to be there?) :(

Right now the computer is far far away from my reach, but when I configured the system I noted that whenever I was locally logged to B and then ssh'ed from A to B, I was logged in without any problem; whenever I was not logged in locally I was asked for a password. Note that at that time I was using a different public/private key pair whose private part had no passphrase.

Any help will be greatly appreciated. :D

P.S. Can anyone tell me how to know exactly what cipher is ssh/sshd using for a particular session? Is there a way to know any statistics for a given session (something like the ~s option in section 5 of [http://www.thegeekstuff.com/2008/05/5-basic-linux-ssh-client-commands/#more-3]("http://www.thegeekstuff.com/2008/05/5-basic-linux-ssh-client-commands/#more-3"))?

P.S. 2: does the following mean that ssh is using protocol 2.0 or something different than protocol 2.0?

(..........) sshd[2606]: debug1: Enabling compatibility mode for protocol 2.0

Many thanks.

---

### Post by Lars Noodén on 2010-01-07
If the target machine is using an encrypted home directory, then the authorized keys will have to be kept somewhere else.

---

### Post by mrrusof on 2010-01-07
Indeed. Will confirm as soon as I fix it.

---

### Post by Lars Noodén on 2010-01-07
The default is for sshd to look for %h/.ssh/authorized_keys, where %h is converted to the user's home directory.  But that file won't be available until a successful login makes the encrypted directory available, and that is not possible until the authorized_keys file is read and used for login.  The user's login name can be abbreviated in sshd_config using **%u**.    

In sshd_config:

```

AuthorizedKeysFile	/var/openssh/**%u**/.ssh/authorized_keys

```

One way to prep the new locations below.  It might be a good idea to leave a note in the usual default location pointing to the new location, just as a form of insurance in case people forget where to put their keys.

```

# 
sudo mkdir -m 0700 -p /var/openssh/fred/.ssh/

#
sudo touch /var/openssh/fred/.ssh/authorized_keys

#
sudo chmod 0600 /var/openssh/fred/.ssh/authorized_keys

#
sudo chown -R fred:fred /var/openssh/fred/

```

---

### Post by mrrusof on 2010-01-07
I just

1) copied /home/myuser/.ssh/authorized_keys to /etc/ssh/myuser/authorized_keys, the owner of /etc/ssh/myuser/ and /etc/ssh/myuser/authorized_keys being root and set permissions to 755 and 644 respectively.

2) set in sshd_config AuthorizedKeysFile to /etc/ssh/%u/authorized_keys

Does this sound good?

---

### Post by mrrusof on 2010-01-07
I mean, it works, but do you see any bad practice involved?

---

### Post by mrrusof on 2010-01-07
I have a new problem:

After setting "PasswordAuthentication" to "no" in sshd_config and rebooting the server I can log in with my private key, but my home folder does not get mounted properly.

---

### Post by Lars Noodén on 2010-01-08
How about this?

[http://ubuntuforums.org/showthread.php?t=1332820](http://ubuntuforums.org/showthread.php?t=1332820)

---

### Post by Saghaulor on 2010-04-06
> **Lars Noodén said:**
> The default is for sshd to look for %h/.ssh/authorized_keys, where %h is converted to the user's home directory.  But that file won't be available until a successful login makes the encrypted directory available, and that is not possible until the authorized_keys file is read and used for login.  The user's login name can be abbreviated in sshd_config using **%u**.    

In sshd_config:

```

AuthorizedKeysFile	/var/openssh/**%u**/.ssh/authorized_keys

```

One way to prep the new locations below.  It might be a good idea to leave a note in the usual default location pointing to the new location, just as a form of insurance in case people forget where to put their keys.

```

# 
sudo mkdir -m 0700 -p /var/openssh/fred/.ssh/

#
sudo touch /var/openssh/fred/.ssh/authorized_keys

#
sudo chmod 0600 /var/openssh/fred/.ssh/authorized_keys

#
sudo chown -R fred:fred /var/openssh/fred/

```

+1 I just discovered this by accident. Obviously it makes sense, that in order to read the public key, first the encrypted directory containing the public key must be decrypted.


Thanks for the solution.

---

### Post by Redsandro on 2011-08-17
I realize these hints are over a year old, so I was wondering what changed?

I am having this problem, but after the changes, *"Server refused our key"* all the time.

One change I noticed is that the config file is relocated to:
*/etc/ssh/sshd_config*

```
RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys
# RED 2011-08-17 Relocate a_keys for encrypted homes
AuthorizedKeysFile      /var/openssh/%h/.ssh/authorized_keys

```

.ssh is 700 and authorized_keys is 600, but no dice.

Anything new I need to know about to fix this?
Note that the original %h/.ssh/authorized_keys entry was commented out by default [SIZE="1"](on Ubuntu 10.04 LTS)[/SIZE], but it's the correct path to the file used by default.

---

### Post by cesera on 2012-08-14
I realise that this message is more than a year old, and you probably have already worked out what is going wrong, but that line in the config file should be:

/var/openssh/%u/.ssh/authorized_keys

(%u, not %h)

---

### Post by CharlesA on 2012-08-14
> **cesera said:**
> I realise that this message is more than a year old, and you probably have already worked out what is going wrong, but that line in the config file should be:

/var/openssh/%u/.ssh/authorized_keys

(%u, not %h)
It shouldn't matter cuz it is commented out. ;)

I didn't think Ubuntu used /var/openssh ?

---

### Post by cesera on 2012-08-15
> **CharlesA said:**
> It shouldn't matter cuz it is commented out. ;)

I didn't think Ubuntu used /var/openssh ?

The line:
```
 AuthorizedKeysFile      /var/openssh/%h/.ssh/authorized_keys
```is not commented out, and should contain a %u for user, not a %h for user's home directory.

And yes Ubuntu does not use /var/openssh, but if you work with an encrypted home directory you need to put your AuthorizedKeysFile somewhere else.
(On top of that you need to add a little script to your unencrypted home directory to decrypt the encrypted one.)

---

### Post by srhart on 2012-09-04
Also, if anyone is still having issues, try changing authorized_keys to authorized_keys2.

Good luck
Simon
[http://www.L3n.co.uk](http://www.L3n.co.uk)

---

